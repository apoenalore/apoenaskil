# Floresta Viva — notas de ecossistema recuperadas

**Status:** regras de simulação do protótipo; não são automaticamente cânone da obra nem referência científica.

## Ciclo ambiental
- Solo em células de 160×160 px; em cada dia virtual, recebe água da chuva ou perde umidade por evaporação. Nutrientes regeneram lentamente e são consumidos por plantas.
- Calendário de protótipo: 365 dias virtuais em 7 dias reais com o jogo aberto; até 25 dias virtuais são processados por atualização.
- Umidade perto do rio recebe bônus adicional em raio aproximado de 260 px, decrescente com distância. Germinação é bloqueada até 60 px do leito.
- Temperatura estimada varia por estação, hora virtual e condição meteorológica; não é previsão real.
- Faixas térmicas ajustáveis/provisórias: bananeira 18–36°C; jabuticabeira 14–34°C.

## Sementes e plantas
- A semente precisa ficar molhada por dois dias virtuais em umidade adequada para estar enterrada e apta a germinar.
- Germinação exige água, nutrientes, luminosidade e distância adequados. Sementes inviáveis expiram após 32 dias.
- Plantas acompanham idade, estresse e frutificações; seca pode matá-las antes do fim do ciclo.
- Bananeira: frutos começam em 230 dias virtuais, fim natural em 285 dias (valores de balanceamento); ao completar ciclo produtivo, pode gerar até três rebentos a cerca de 31–46 px, sujeitos a espaço/população.
- Jabuticabeira: frutificação inicial aos 570 dias e fim natural aos 1400 dias (valores de balanceamento). Frutos podem gerar sementes ao apodrecer ou ser consumidos por javali.

## Fauna, decomposição e limites
- O javali pode dispersar sementes para a posição que ocupa após dois dias virtuais.
- Pássaro: evento simulado a cada cinco dias virtuais, se houver fruto de jabuticaba caído; transporte da semente após dois dias.
- Morte de planta deixa madeira em três fases (tronco inteiro, tronco decompondo, pó); nutrientes retornam gradualmente por até 90 dias virtuais.
- Frutos apodrecem e devolvem pequena fração de nutrientes.
- Limites por mapa carregado: 120 plantas, 180 sementes, 90 frutos, 24 sementes transportadas.

## Pendências e limites
- Os valores são provisórios e ajustáveis; não representam leis botânicas.
- Arte e animações de estágios ainda podem ser geométricas/provisórias. GameCreator permite cadastrar 14 fases visuais por espécie, mas a importação de regras do arquivo JSON de espécie ainda não substitui automaticamente os parâmetros internos.
- HTML e Godot mantêm saves separados, sem sincronização e sem multiplayer nesse módulo.
- Parcelas com proprietário/permissões, inventário, plantio/colheita econômicos, venda/troca, caça, dungeons, dragão e coop local Bluetooth/Wi-Fi Direct aparecem como requisitos planejados, não como recursos implementados na documentação consultada.
- Em rede local, o requisito documentado prevê anfitrião como autoridade de simulação do clima, solo, colheita e inventários; é um requisito futuro do protótipo, não implementação atual.

## Fonte
- `apoenalore/Apoena-pixel-art-html/docs/ECOSSISTEMA.md`
- `apoenalore/Apoena-pixel-art-html/docs/TERRAS_E_COOP.md`
- `apoenalore/Apoena-pixel-art-html/docs/ORGANIZACAO.md`
- Skill: `skills/apoena-ecology-systems/SKILL.md`
