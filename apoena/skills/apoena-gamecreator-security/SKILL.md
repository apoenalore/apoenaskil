---
name: apoena-gamecreator-security
description: Conduz auditorias e hardening do Apoena Game Creator para Windows, uso em equipe, armazenamento local, GitHub Actions e distribuição por ZIP.
---
# Apoena GameCreator Security

## Objetivo e escopo

Auditar e melhorar a segurança do editor GameCreator, sua Biblioteca Central, comunicação entre módulos, importação/exportação, distribuição e ambiente de desenvolvimento. Não confundir esta Skill com segurança do runtime do jogo, cânone narrativo ou segurança genérica de outro produto.

## Leitura obrigatória

- [Contexto técnico GameCreator](../../docs/game-creator/README.md).
- [Dossiê de auditoria recuperado](../../docs/game-creator/security-audit/conversation-dossier-2026-11-02.md).
- Repositório de código [apoenalore/GameCreator](https://github.com/apoenalore/GameCreator): instruções locais, arquivos atuais, testes e workflows.
- [Project Architect](../apoena-project-architect/SKILL.md) e [GameCreator Engineering](../apoena-gamecreator-engineering/SKILL.md).

## Threat model recuperado

Contexto declarado pelo autor na sessão de origem:
- aplicação local em Windows;
- utilização por equipe;
- compartilhamento por GitHub/cloud;
- GitHub Actions habilitado;
- distribuição de atualizações em ZIP produzido pelo Actions.

Ameaças a avaliar:
1. comprometimento de conta de integrante e alteração do código;
2. alteração maliciosa de workflows ou dependências;
3. exposição de secrets ou permissões excessivas no Actions;
4. artefato ZIP adulterado ou sem vínculo verificável com commit/release;
5. importação de backup/projeto/imagem malformados;
6. abuso de mensagens entre janelas/módulos;
7. ransomware e sincronização de arquivos criptografados;
8. perda de dados locais mantidos em IndexedDB.

Esse threat model foi recuperado de um dossiê textual; confirmar o ambiente atual antes de assumir que as configurações permanecem iguais.

## Regras de auditoria

1. Obter código atual e SHA; nunca auditar somente uma versão descrita em resumo.
2. Identificar superfície de entrada, privilégio, origem, fluxo de dados, pré-condições e impacto.
3. Separar achado estático, hipótese, vulnerabilidade reproduzida e incidente confirmado.
4. Para cada achado, registrar arquivo/linha, evidência, cenário de exploração, severidade justificada, correção, teste e risco residual.
5. Não atribuir CVSS ou gravidade sem evidência e contexto.
6. Não declarar proteção completa apenas por hash: SHA-256 detecta divergência em relação a um valor confiável, mas não autentica quem publicou esse valor. Assinatura digital e gestão segura da chave são controles separados.
7. Validar importações antes de gravar; limitar bytes, dimensões, quantidade de registros, profundidade/estrutura e consumo de memória/CPU.
8. Preferir transação/staging e rollback testado para restauração; teste deve simular falha em diferentes etapas e verificar estado final.
9. Em `postMessage`, validar `origin`, `source`, canal, tipo, ID, ação, schema e autorização. Não usar `"*"` como destino quando a origem esperada puder ser determinada. Tratar `"null"` como origem opaca, nunca como autorização genérica.
10. Não confiar no MIME informado pelo cliente; validar assinatura/magic bytes e decodificar com limites seguros. Tratar SVG separadamente por poder conter conteúdo ativo.
11. Para GitHub Actions: princípio do menor privilégio, `permissions` explícitas, Actions de terceiros fixadas por SHA, separação build/publicação, secrets protegidos, PRs de fork tratados como não confiáveis e aprovação de environment para publicação quando aplicável.
12. Para distribuição: vincular artefato a tag/commit, publicar manifesto SHA-256 e considerar assinatura assimétrica com chave privada fora do código e de jobs não confiáveis.
13. Para backups: manter cópia fora do endpoint principal, offline ou imutável quando possível, e executar testes periódicos de restauração.
14. Nunca modificar ou apagar dados de usuário durante auditoria. Usar fixtures e ambientes temporários isolados.

## Achados históricos do dossiê — não presumir que continuam no HEAD

| ID | Arquivo/área | Achado recuperado | Status de proveniência |
|---|---|---|---|
| SEC-001 | `shared/creator-bridge.js` | Listener aceitava `event.origin === "null"` e não restringia suficientemente a janela remetente | RECUPERADO — VALIDAR |
| SEC-002 | `shared/asset-library.js` | Envio `postMessage("*")`; receptor de resposta verificava `event.source === root.parent`, mas origem não era validada explicitamente | RECUPERADO — VALIDAR |
| SEC-003 | `shared/library-backup.js` | Importação sequencial sem atomicidade/rollback global | RECUPERADO — VALIDAR; ausência descrita no código da época |
| SEC-004 | `shared/library-backup.js` | Ausência de assinatura/autenticidade do backup | RECUPERADO — VALIDAR; ausência descrita no código da época |
| SEC-005 | `shared/asset-library.js` | MIME `image/*` usado como validação de imagem | RECUPERADO — VALIDAR |
| SEC-006 | Distribuição ZIP | Integridade do pacote não verificada no fluxo descrito | PLANEJADO / NÃO VERIFICADO |
| SEC-007 | Projetos em backup | Validação estrutural descrita como incompleta | RECUPERADO — VALIDAR |

O dossiê declara que não houve exploração, teste dinâmico, incidente, teste de ransomware ou restauração. Portanto, esses itens não são vulnerabilidades exploráveis confirmadas. O código atual pode ter mudado; revalidar antes de abrir issue ou aplicar patch.

## Ordem de trabalho recomendada

### P0 — origem e governança
- conferir branch protection/Rulesets e revisão independente;
- revisar o bridge e o protocolo da biblioteca;
- inspecionar workflows, permissões, secrets, dependências e publicação de ZIP.

### P1 — integridade e recuperação
- schema completo de backup e projetos;
- importação transacional/staging/rollback;
- validação real de imagens e limites;
- SHA-256 vinculado a commit/tag;
- assinatura digital e proteção de chaves;
- backup independente e teste de restauração.

### P2 — cobertura ampliada
- CMD, PowerShell, Python, bundle e legacy;
- Godot, Map Editor e Pixel Art;
- dependências, testes de regressão e testes de segurança.

## Critérios para encerrar um achado

Só marcar como corrigido após:
- revalidar o achado no SHA atual;
- aplicar patch mínimo;
- adicionar teste de regressão que falharia antes da correção;
- executar testes pertinentes;
- confirmar CI no SHA/branch/PR corretos;
- executar teste manual em Windows/navegador/Godot quando aplicável;
- documentar commit, logs, resultado e risco residual.

Se o ambiente alvo não estiver disponível, manter PENDENTE — TESTE MANUAL, sem alegar conclusão.

## Referência de preservação

O registro histórico completo está em [conversation-dossier-2026-11-02.md](../../docs/game-creator/security-audit/conversation-dossier-2026-11-02.md). A proposta V4.2 Security Hardening permanece PROPOSTA até existir implementação, commit e validação.
