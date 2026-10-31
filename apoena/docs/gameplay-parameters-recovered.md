# Parâmetros de gameplay recuperados

**Status:** requisitos/valores discutidos; não são cânone narrativo nem prova de implementação atual.

## MOBA e arena
- Direção mudou de MOBA 3D semelhante a LoL para protótipo pixel-art 2D/2.5D; HTML para teste rápido e Godot para produção.
- Mapa 1000×1000 (unidade/escala a confirmar); câmera de acompanhamento 360° discutida.
- Dungeons/cavernas com entradas vermelha/azul; travessia central e dragão memorável, não excessivamente forte.
- Regra discutida: no máximo um membro da mesma equipe dentro da caverna.
- Monstros na dungeon e no campo; voz/microfone desejados, implementação não confirmada.
- Valores lembrados: torres 5.000 HP; torres intermediárias 2.500 HP; soldados 2.500 HP; heróis 4.000 HP. Categorias precisam ser conferidas.
- Recurso: Aurium (AUR), não mana.
- Loja inicial: 2.000 moedas; ideia anterior de 1.500 foi substituída.
- Autor rejeitou recuperação automática de ataques baseada em cooldown como regra genérica e pediu “regra Apoena”; formulação técnica completa não recuperada.

## Apoena Q/W/E/R/F
- Q: esfera causa 20% da vida do alvo.
- W: golpe atinge três inimigos, causando 15%.
- E: escudo azul por 15 segundos.
- R: soco/impacto sísmico de 100%.
- F: recupera vida e AUR completamente.
- Custo mencionado: aproximadamente 3,5% de AUR. Não está claro se por habilidade ou versão.
README e código precisam ser verificados antes de afirmar funcionamento atual.

## Aqua e Oriom
- Aqua: esfera de água, barreira, cura de HP e remoção de veneno discutidas.
- Veneno: 1 minuto; reduz 30% de HP a cada 10 segundos. Confirmar se percentual da vida máxima ou atual.
- Aqua não deve portar grimório.
- Oriom id “oriom”; alcance 115 e teste 185; teleporte com recarga. Parâmetros experimentais.

## Itens
Gerador com categorias ataque, defesa, velocidade, suporte, magia e crítico. Loja começa com 2.000 moedas conforme correção posterior.
Identidade de itens deve refletir Agar: quatro tribos/cores, Aurium, manopla, cristais, selos/muralha, flora/alquimia, 13 constelações e armas do Manual do Aule (lança, espada, grimório, arco). Conteúdo integral do Manual não recuperado.

## Mundo vivo
Clima, estações e chuva; javali come grama e bananas, deixa frutos em ciclos de cinco minutos e dispersa sementes; abelhas de Agar polinizam árvores, com colmeia associada a tronco seco; plantas crescem, frutificam e morrem. Lista lembrada: javali, abelha e colmeia. É planejamento/objetivo; compare com ecology-game-notes.md.

## Estado
Este documento não prova presença dos parâmetros na versão atual. Ao atualizar, registrar repositório, branch, commit, cena/script e teste.
