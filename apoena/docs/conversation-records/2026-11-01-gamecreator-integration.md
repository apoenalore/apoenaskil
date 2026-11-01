# Registro conversacional — integração do Game Creator

**Fontes:** “Recuperar Projeto Game Creator”, “Implementação do Editor Visual” e “Criar estúdio de animação”, consultadas em 2026-11-01.  
**Status:** decisões e requisitos declarados pelo autor em conversas; representam direção do produto, não comprovação de implementação.

## Integração do produto

- Pixel Art e Game Creator devem funcionar como partes de uma aplicação integrada. O autor descreve que os módulos não devem aparecer como produtos separados.
- A página inicial deve abrir os fluxos principais juntos, com entrada do jogo, telas/menus e o menu do Pixel Art sob navegação integrada.
- O editor Pixel Art também precisa criar objetos e definir suas funções, ataques, defesa e reações a clima, chuva e sol. O autor quer usar os geradores existentes (incluindo editor/gerador de itens e receitas) para editar outro jogo.
- O trabalho nas versões 3.9/4.0 deve recuperar e integrar o que continua útil e retirar páginas HTML iniciadoras sem função. Antes de afirmar o que falta ou alterar o app, inspecionar o estado real do repositório e preservar as partes aproveitáveis.

## Requisitos de combate citados

- No modo MOBA, a exploração do mapa pode permitir encontrar itens e armas melhores.
- A mira em primeira pessoa deve permitir priorizar um alvo específico para evitar que um ataque selecione um soldado próximo em vez do herói.
- A precisão não aumenta o alcance: um ataque fora do alcance não deve acertar.
- Personagens com ataques guiados podem ter alcance um pouco maior.

## Editor e animação — visão em desenvolvimento

- Gerar personagens em camadas, com corpos preparados para esqueleto, posições e expressões reutilizáveis.
- Oferecer escolha de aparência e identidade para personagens de jogos, mantendo o corpo animável sem deformações visuais.
- Permitir movimentos como caminhar e atacar; considerar cabelo movendo-se com o vento, cenário animado e efeitos de luz/poder.
- Esses pontos foram apresentados como ideia de produto. Não significam que o app atual já tenha rigging, animação esquelética, sistema de efeitos ou editor de personagem funcional.

## Próximo passo técnico

Conferir estas notas contra o repositório Game Creator, identificar os módulos existentes e seus estados, e só então transformar requisitos em escopo de implementação. Este registro pertence à memória de produto; não é cânone narrativo de Apoena.
