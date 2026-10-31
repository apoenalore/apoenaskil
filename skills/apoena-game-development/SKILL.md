---
name: apoena-game-development
description: Organiza o contexto técnico dos jogos Apoena e evita misturar implementação, lore, ferramentas e repositórios distintos.
---

# Desenvolvimento de jogos Apoena

## Separação de projetos
- O repositório de jogo conhecido é `apoenalore/JOGO-APOENA-AGAR-`; o autor determinou que ele contenha somente arquivos do jogo.
- O repositório de conhecimento Apoena Skills é `apoenalore/apoenaskil`.
- Outros projetos citados: Studio Maker, Lore Engine, Apoena AI Hub (`apoenalore/APOENA-AI-HUB-IA`), ApoenaBrowser e Beringela Studio 2D. Não misturar arquivos nem assumir que todos pertencem ao repositório do jogo.
- As Skills devem tratar gameplay como implementação e não como regra canônica da cosmologia, a menos que o autor diga explicitamente.

## Contexto técnico registrado — tratar como desenvolvimento, não cânone
- Godot 4.0 foi citado em material do Game Creator; projeto do jogo em evolução inclui HTML como protótipo e Godot como destino.
- Uma direção de gameplay foi descrita como arena 2.5D/pixel art, com mapa 1000×1000, torres, bases, respawn, câmera de acompanhamento 360°, entradas de dungeon e dragão central. Houve também ideia anterior 3D tipo MOBA; versões devem ficar separadas.
- Registros de jogo incluem stats e habilidades (torres/HP, personagens, ataques e custos) e simulação ecológica (javali, bananas, sementes, crescimento de árvores, abelhas/polinização, clima e estações). Esses números e regras são parâmetros de gameplay em desenvolvimento, não lore definitivo.
- Prioridade mais recente registrada em 2026-10-30: análise profunda de todos os conteúdos do projeto de jogo; versões completas e não parciais são desejadas. Em conversa anterior, APK foi temporariamente posto de lado para focar em funcionalidades do runner.
- Repositório de jogo deve manter modos/arquiteturas distintos claramente nomeados; não atribuir ao cânone universal decisões específicas de arena.

## Regras de trabalho
- Antes de alterar código, inventariar arquivos, estado atual, funcionalidades completas e pendentes.
- Preservar lista de pendências e versão-alvo do usuário.
- Não declarar APK, HTML, runner ou Godot “concluído” sem validar a execução.
- Para mecânicas, distinguir especificação do autor, implementação presente, teste e bug conhecido.
