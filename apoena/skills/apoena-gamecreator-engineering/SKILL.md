---
name: apoena-gamecreator-engineering
description: Orienta agentes a desenvolver, manter, integrar, testar e distribuir o Apoena Game Creator sem misturar editor, módulos de autoria, runtime do jogo e base de conhecimento.
---
# Apoena GameCreator Engineering

## Objetivo

Manter continuidade técnica do Apoena Game Creator. Esta Skill trata da ferramenta de autoria e de seu ciclo de desenvolvimento. Não define cânone narrativo e não substitui as instruções locais do repositório de código.

## Leitura obrigatória

1. Repositório de código: `https://github.com/apoenalore/GameCreator` — ler o `AGENTS.md` e README atuais antes de modificar.
2. [Visão técnica e estado recuperado](../../docs/game-creator/README.md).
3. [Dossiê de segurança e suas limitações](../../docs/game-creator/security-audit/conversation-dossier-2026-11-02.md).
4. Skill [Project Architect](../apoena-project-architect/SKILL.md).
5. Skill [Gameplay Implementation](../apoena-gameplay-implementation/SKILL.md) quando o trabalho envolver regras de jogo, mecânicas ou integração do runtime.

## Limites entre produtos

- **GameCreator:** editor/ambiente de autoria.
- **Pixel Art HTML:** módulo integrado do ambiente de autoria; não o trate como produto desconectado quando o requisito for integração.
- **JOGO-APOENA-AGAR-:** runtime consumidor; uma exportação bem-sucedida não prova que o asset funciona no jogo.
- **Apoena Skill:** documentação, conhecimento e Skills; não é o código do editor.
- **Lore/mangá:** decisões de mecânica, protótipos e ferramentas não alteram o cânone narrativo.

## Regras de continuidade e execução

1. Identifique repositório, produto, branch, commit-base e estado do working tree antes de editar.
2. Leia as instruções `AGENTS.md` locais e os documentos de pendências antes de tocar em editor, mapa, tilesets, Pixel Art, build, CI ou PowerShell.
3. Respeite **WIP = 1** para GameCreator e Apoena Pixel Art HTML combinados. Não iniciar uma segunda tarefa de código concorrente enquanto a primeira não estiver validada/encerrada.
4. Reaproveite módulos existentes após inspecionar sua API e integração. Não recrie geradores, pontes, bibliotecas, sistemas de tileset ou catálogo sem evidência de que não atendem ao requisito.
5. Preserve assets, dados IndexedDB, projetos, configurações, exports, backups, credenciais e runner. Nunca usar `git reset --hard`, `git clean`, espelhamento destrutivo ou exclusão de dados locais sem autorização explícita e backup verificado.
6. Não alterar a branch principal diretamente para mudanças relevantes. Use branch de trabalho e Pull Request; preserve branches de backup/histórico.
7. Uma alteração pequena e testável por vez. Não enfraquecer testes, remover assertions, ocultar exceções ou criar workflows duplicados para obter CI verde.
8. Antes de mexer em CI, identificar e reutilizar o workflow canônico. Verificar se os gatilhos cobrem os arquivos/branches corretos.
9. Depois de cada alteração de código, verificar que o Actions iniciou automaticamente no SHA e branch/PR corretos. Registrar URL do run e conclusão. Diferenciar queued, in_progress, failed, cancelled e success.
10. Um workflow de Pixel Art não valida automaticamente o atualizador, o editor ou outro conjunto de arquivos. Confirmar que os jobs executados cobrem a mudança.
11. CI verde não substitui validação em Windows real, navegador, Godot ou runtime consumidor quando esses ambientes forem alvo.
12. Separar fatos observados, hipótese, proposta, implementação e teste. Atualizar status somente com evidência.
13. Registrar commit, arquivos alterados, testes executados, resultados e pendências. Nunca afirmar que a instalação local do autor foi modificada sem confirmação real.

## Estado técnico conhecido — referência histórica

O dossiê de segurança descreveu a V4.1 como uma entrega com 76 arquivos de runtime e commit `0bd916157d9bfab6c6c9b121c26050f94918cf80`. Não presumir que esse SHA seja o HEAD atual.

Módulos individuais examinados na conversa de origem:
- `index.html` — interface da Biblioteca Central;
- `shared/asset-library.js` — assets/projetos, IndexedDB, mensagens;
- `shared/creator-bridge.js` — ponte de comunicação entre janelas;
- `shared/library-backup.js` — exportação/importação de snapshots;
- `shared/tileset-check.js` — análise conservadora de bordas/grade de tilesets.

A Biblioteca Central utiliza IndexedDB local ao navegador, com object stores `assets` e `projects`. O GitHub/ZIP não é backup desses dados. A migração de navegador, perfil ou origem exige exportação e restauração verificadas.

## Distribuição e instalação

O dossiê relatou distribuição por ZIP via GitHub Actions em ambiente Windows de equipe. Antes de alterar esse fluxo, auditar o workflow real, permissões, secrets, gatilhos, dependências e publicação. Para cada artefato, vincular versão, commit e SHA-256; assinatura digital é proposta até implementação demonstrada.

Existe também o histórico da tarefa GC-UPDATE-009 no repositório GameCreator. Consultar PR #7 e a documentação local antes de continuar. O atualizador incremental por Git foi preparado em branch de trabalho, mas não declarar validado/mesclado sem CI pertinente e teste Windows real. Um run de workflow não relacionado não satisfaz esse critério.

## Como registrar progresso

Para cada tarefa:
- ID e objetivo;
- produto/repositório;
- branch e SHA base;
- requisito do autor;
- arquivos e módulos afetados;
- hipótese/risco;
- patch e commit;
- testes e logs;
- CI no SHA correto;
- validação manual/plataforma;
- status e riscos residuais.

Use os rótulos da legenda do repositório: IMPLEMENTADO — VERIFICADO, IMPLEMENTADO — HISTÓRICO, PLANEJADO, PROPOSTA, RECUPERADO — VALIDAR e DESCONHECIDO.

## Referência

- [Mapa técnico do GameCreator](../../docs/game-creator/README.md)
- [Dossiê de auditoria de segurança](../../docs/game-creator/security-audit/conversation-dossier-2026-11-02.md)
- [Project Architect](../apoena-project-architect/SKILL.md)
- [Gameplay Implementation](../apoena-gameplay-implementation/SKILL.md)
