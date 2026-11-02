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


## Game Creator — registros recuperados das conversas do projeto

**Fonte:** conversa “Implementação do Editor Visual”, no projeto ChatGPT `historiaegeografia`. São registros de desenvolvimento e pedidos do autor; datas e estado do código devem ser confirmados no repositório GameCreator antes de tratar como estado atual.

### Auditoria relatada da versão 3.9.2
- A conversa registrou 135 arquivos, 15 scripts JavaScript e 52 ícones oficiais no pacote examinado.
- Os módulos já listados incluíam Editor de Layout, Fábrica Universal de Itens, Slicer, controles PC/Android, personagens/equipamentos, receitas, animações 3D, ações/eventos, simulador de regras, exportação e Central de Projetos.
- A orientação foi inspecionar e completar o executor Godot existente, não recriar esses sistemas. Foram citados salvamentos em IndexedDB, backups JSON e projetos nomeados, cuja consistência precisava ser verificada.
- A conversa relatou 8/8 testes de regras para uma Bancada de Testes v4.0 e 17 scripts sem erro de sintaxe; execução nativa no Godot 4 e em Android físico continuava sem validação. Tratar esses números como resultados daquela etapa, não como status atual.
- Antes de marcar recurso como concluído, verificar se funciona, salva, passa por teste e chega ao jogo exportado. Interface ou cadastro, isoladamente, não provam execução.

### Direção de gameplay e mira
- O conceito de Apoena Agar combina estratégia MOBA, exploração durante a partida, equipamentos encontrados no mapa e combate com opção de câmera MOBA, terceira pessoa ou primeira pessoa.
- O autor especificou que a mira deve melhorar a **precisão** sem aumentar o alcance normal do ataque: um alvo fora do alcance não pode ser acertado. Ataques guiados podem ter alcance um pouco maior, conforme configuração do personagem.
- Seleção/prioridade de alvo deve permanecer separada da colisão física: priorizar ou travar um herói não permite atravessar tropas, escudos ou paredes.
- A conversa também descreve exploração de cavernas, coleta de materiais/equipamentos e retorno à rota; risco, recompensa e equilíbrio entre equipes permanecem requisitos de design a validar.
- São ideias e requisitos de jogo, não cânone narrativo nem funcionalidades comprovadas no Creator. Validar cada item contra a versão atual do GameCreator e o runtime Godot.

## Registro-base — arquitetura leve, árvores e PR #11 (2026-11-01/02)

Consultar também [registro conversacional completo](../docs/conversation-records/2026-11-02-gamecreator-low-end-first-and-tree-billboards.md). O documento preserva a explicação das tecnologias HTML/CSS/JavaScript/GDScript/JSON/PowerShell, a diretriz proposta *Low-End First*, as referências Game Boy, a ideia de árvores com billboard ou sprites direcionais, a escolha de perspectiva ainda pendente e o diagnóstico ainda inconclusivo da validação da PR #11 do GameCreator.

**Importante:** o erro específico da CI não foi confirmado porque os logs da execução original não estavam disponíveis; o rerun ainda estava em andamento na última consulta. Não atribuir causa sem evidência. As técnicas de árvores e as metas de desempenho são propostas para teste, não funcionalidades aprovadas ou implementadas. Este registro é memória de desenvolvimento, não cânone narrativo.
