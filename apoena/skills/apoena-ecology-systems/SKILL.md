---
name: apoena-ecology-systems
description: Documenta ecossistemas e natureza do protótipo Floresta Viva sem converter parâmetros de simulação em cânone ou ciência validada.
---
# Skill — Ecossistema e natureza de Floresta Viva

## Escopo
Esta Skill cobre sistemas de natureza do jogo Pixel Art/Floresta Viva. Ela não declara que cada parâmetro de simulação é uma regra da cosmologia ou da natureza canônica do mangá.

Fonte operacional detalhada: repositório `apoenalore/Apoena-pixel-art-html`, especialmente `docs/ECOSSISTEMA.md`, `docs/TERRAS_E_COOP.md`, `docs/ORGANIZACAO.md` e `assets/NATUREZA_IMPORTAR.md`.

## Conhecimento de simulação atualmente documentado
- Bananeira e jabuticabeira são espécies simuladas; javali e eventos de pássaros participam da dispersão de sementes.
- Solo é dividido em blocos de 160×160 px; cada dia virtual atualiza água da chuva/evaporação e nutrientes.
- Calendário de protótipo: 365 dias virtuais em 7 dias reais com o jogo aberto. A simulação processa no máximo 25 dias por atualização.
- Semente molhada precisa permanecer em umidade adequada por dois dias virtuais antes de poder germinar; sementes inviáveis expiram após 32 dias.
- A germinação exige água, nutrientes, luz e distância adequados.
- Umidade adicional perto do rio decai com a distância em raio aproximado de 260 px; até 60 px do leito não é permitido germinar.
- Faixas térmicas provisórias: bananeira 18–36°C; jabuticabeira 14–34°C. A temperatura é estimada por estação, hora virtual e clima, não é previsão meteorológica real nem dado agronômico definitivo.
- Bananeira produtiva pode gerar até três rebentos a cerca de 31–46 px do pé-mãe, respeitando espaço e população.
- Jabuticabeira madura produz frutos; sementes podem surgir por apodrecimento ou consumo/dispersão pelo javali. O javali transporta a semente após dois dias virtuais para sua posição naquele momento.
- Restos de madeira têm três fases (tronco inteiro, tronco decompondo, pó) e devolvem nutrientes gradualmente por até 90 dias virtuais.
- Pássaros são eventos simulados a cada cinco dias virtuais quando há fruto de jabuticaba caído; transporte de semente ocorre após dois dias.
- Limites por mapa carregado: 120 plantas, 180 sementes, 90 frutos e 24 sementes transportadas.
- HTML e Godot possuem saves separados; não há sincronização entre os motores nem multiplayer neste módulo.
- Artes de árvores, animais e estágios são provisórias até que sprites autorais sejam importados. GameCreator suporta cadastro de 14 fases visuais por espécie; o JSON de ficha ainda não substitui automaticamente os parâmetros internos do simulador.

## Regras de autoria e implementação
- Marque todos os limites, tempos e faixas acima como **parâmetros de protótipo/balanceamento**, salvo se o autor aprovar explicitamente outra condição.
- Não afirmar realismo botânico, previsão climática, lençol freático ou enchentes: os modelos são abstrações.
- Não declarar inventário, propriedade de terra, multiplayer ou Bluetooth/Wi-Fi Direct implementados quando as fontes os classificam como pendentes.
- Ao alterar uma regra, preservar o registro da causa, teste e status; não duplicar a simulação em mais workflows.
- Para nova espécie, documentar estados, condições de germinação, ciclo, reprodução, interação com fauna, custo computacional e representação visual.

## Relações
- Sistemas de jogo: `apoena-game-systems`.
- Prototipagem: `apoena-godot-prototyping`.
- Recuperação/proveniência: `apoena-knowledge-archivist`.
- O resumo de transferência é `../../docs/ecology-game-notes.md`.
