---
name: apoena-game-development
description: Mantém a separação entre lore, jogos e ferramentas de Apoena e organiza requisitos, versões, testes e pendências de desenvolvimento.
---
# Desenvolvimento de jogos Apoena

## Separação de projetos
- Repositório de jogo conhecido: apoenalore/JOGO-APOENA-AGAR-; contém somente arquivos do jogo conforme decisão do autor.
- Biblioteca de Skills/lore: apoenalore/apoenaskil.
- Outros projetos citados: Studio Maker, Lore Engine, Apoena AI Hub, ApoenaBrowser e Beringela Studio 2D. Não misturar arquivos nem assumir que são parte do jogo.

## Contexto de desenvolvimento — não é cânone narrativo
- Godot 4.0 foi citado em material de Game Creator; HTML serve para protótipo rápido e Godot como destino, conforme conversas.
- Direção de teste descrita como arena 2.5D/pixel art com mapa 1000×1000, torres, bases, respawn, câmera de acompanhamento, dungeons e dragão central. Existiu também direção anterior 3D tipo MOBA; preservar histórico de desenvolvimento.
- Mecânicas citadas: stats/HP, habilidades de Apoena e Aqua, moedas de loja e simulação ecológica (javali, bananas, sementes, árvores, abelhas/polinização, clima e estações). Tratar como parâmetros de gameplay em desenvolvimento, não regras metafísicas.
- Prioridade registrada em 2026-10-30: análise profunda do conteúdo do projeto de jogo; APK foi temporariamente posto de lado para focar funcionalidades do runner.

## Método
Antes de alterar código: inventariar arquivos, versão, implementações completas, pendências e testes. Distinguir especificação, código existente, resultado de teste e bug. Não declarar build, runner, HTML ou Godot concluído sem validação.
