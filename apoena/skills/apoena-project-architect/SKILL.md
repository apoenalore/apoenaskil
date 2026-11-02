---
name: apoena-project-architect
description: Mantém a separação entre repositórios Apoena, ferramentas de autoria, runtimes e documentação, verificando o estado real antes de declarar funcionalidades implementadas.
---
# Apoena Project Architect

## Objetivo
Ajudar agentes a continuar os projetos técnicos associados ao universo Apoena sem misturar produtos, código, saves, assets ou estados de implementação.

## Leitura obrigatória
- `../../AGENTS.md`
- `../../docs/repository-map.md`
- `../../docs/game-design-recovered.md`
- O README e as instruções do repositório específico que será alterado.
- Para o editor GameCreator: `../apoena-gamecreator-engineering/SKILL.md` e, quando aplicável, `../apoena-gamecreator-security/SKILL.md`.

## Regras
1. Identifique o repositório e o produto exatos antes de editar.
2. Preserve os limites entre Studio Maker, ambiente de autoria Game Creator e runtime JOGO-APOENA-AGAR-. Dentro do ambiente Game Creator, trate Pixel Art como módulo integrado de autoria conforme requisito direto do autor; não imponha fluxo com aplicativos de autoria desconectados. Lore Engine e AI Hub continuam produtos distintos.
3. Diferencie ferramenta de autoria de runtime consumidor: exportar um asset ou metadado não comprova uso no gameplay.
4. Marque o estado como IMPLEMENTADO, DOCUMENTADO, PLANEJADO, PROPOSTA, PENDENTE ou DESCONHECIDO, com evidência.
5. Não afirme que um APK, multiplayer, sincronização de saves ou integração foi validado sem teste/evidência do consumidor.
6. Leia instruções locais e workflows antes de alterar CI, runner, testes ou persistência.
7. Preserve fontes originais e branches de arquivo; não remova assets grandes ou históricos sem solicitação explícita.
8. Em conflito entre README e código, inspecione código, testes, histórico e commit; registre a divergência em vez de escolher arbitrariamente.
9. Requisitos de um jogo não se tornam cânone do mangá automaticamente.
10. Não transfira nomes ou identidades entre fichas sem validação (ex.: Oriom/Orium, Ubirara/Birará).
11. Para toda habilidade relatada, diferencie teste isolado, validação Godot, validação Android e operação no runtime.
12. Conserve correções do autor com precedência sobre hipóteses anteriores do assistente; mantenha registros antigos datados e marcados como superados.

## Fluxo de trabalho
- Confirmar escopo do repositório e branch.
- Ler AGENTS.md e documentação local.
- Registrar estado atual por evidência.
- Fazer a menor alteração testável.
- Executar testes aplicáveis e separar CI de validação manual.
- Atualizar documentação e proveniência.
- Registrar commit, hash e resultado.

## Referências
- `../../docs/repository-map.md`
- `../../docs/game-design-recovered.md`
- `../../docs/game-design-notes.md`
- `../../docs/knowledge-recovery-2026-10-30.md`
- `../apoena-gamecreator-engineering/SKILL.md`
- `../apoena-gamecreator-security/SKILL.md`
