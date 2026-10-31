# Sistemas de jogo recuperados — detalhes adicionais

**Data:** 2026-10-30  
**Status:** mistura deliberadamente separada de decisões de processo, planos, protótipos documentados e requisitos ainda não implementados. Não é cânone do mangá.

## 1. Plano geral de modos

Fonte: `apoenalore/GameCreator/PLANO_GERAL_APOENA.md`.  
**Status: PLANO DE ARQUITETURA / DESENVOLVIMENTO**, não prova de implementação completa.

### História
A sequência inicial planejada começa na cidade capital, onde Apoena estuda; segue até a Tribo da Água para encontrar os pais; inclui uma prova cujo fracasso faz parte da narrativa; e abre caminho de aventureiro, com caça, coleta de remédios, monstros e defesa da muralha.

### Exploração Livre
O jogador cria sua identidade e escolhe o que quer se tornar — exemplos registrados: ferreiro, aventureiro, mago, agricultor, comerciante ou combinações. O desenvolvimento deve surgir das ações, conhecimentos e escolhas, sem exigir que o jogador seja Apoena nem seguir a narrativa do Modo História.

### MOBA
O plano descreve progressão temporária de nível 0 a 20 e uma possível conversão de parte da experiência da partida para progressão permanente do menu. A taxa de conversão deve ser balanceada. Nível de partida e progressão permanente são dados diferentes.

### Três camadas de progressão
1. Personagem: competências, habilidades, Aurium, Constelações, equipamentos e especializações.
2. Mundo: casa, horta, guilda, companheiros, relações, economia, recursos e regiões.
3. Menu permanente: desbloqueios de estruturas e opções, como laboratório, ferreiro, arena, melhorias e fabricação.

As escolhas podem abrir/fechar oportunidades, alterar relações e influenciar o desenvolvimento. O plano recomenda evitar classes rígidas que impeçam combinações.

## 2. Mundo persistente e economia — plano

NPCs importantes são planejados com identidade, profissão, objetivos, inventário, rotinas e relações; poderiam produzir, comprar, vender, viajar e reagir à ausência do jogador. A economia planejada considera estoque, oferta, demanda, produção, consumo, preços e disponibilidade. Exemplo do plano: um mercado pode deixar de comprar espadas se já estiver abastecido por outro ferreiro.

Agar é indicada como região inicial planejada; Pandora amplia a exploração. O retorno do jogador deveria revelar mudanças persistentes, respeitando o tempo de mundo definido pelo jogo.

**Status:** planejamento. Não afirmar que simulação econômica autônoma, NPCs persistentes ou regiões estejam implementados apenas por constarem no plano.

## 3. Ecossistema — classificação de entidades

O plano separa:
- cenário estático: decoração sem simulação individual;
- recurso interativo: árvore, pedra ou planta que reage à coleta;
- organismo simulado: planta ou animal com ciclo ecológico.

A simulação pretendida abrange sementes, germinação, crescimento, água, nutrientes, luz, temperatura, estações, frutificação, coleta, dispersão, morte e decomposição. O editor deve armazenar assets e metadados; o runtime é responsável por executar a simulação. Um campo cadastrado no Creator não prova que a mecânica esteja implementada no jogo.

## 4. Floresta Viva — protótipo Pixel Art

Fonte: `apoenalore/Apoena-pixel-art-html`, README e docs/ECOSSISTEMA.md.

**Documentado no protótipo:**
- Umidade do solo por células de 160 × 160 px; chuva e evaporação em ciclos diários virtuais.
- Calendário configurado para 365 dias virtuais em 7 dias reais de jogo aberto.
- Sementes exigem umidade adequada por dois dias virtuais antes de ficarem aptas a germinar; sementes inviáveis expiram após 32 dias.
- Germinação considera água, nutrientes, luminosidade e distância; plantas acompanham idade, estresse e frutificações.
- Bananeira pode gerar até três rebentos após ciclo produtivo; jabuticabeira dispersa sementes por frutos e animais.
- Decomposição de restos de madeira pode devolver nutrientes por até 90 dias virtuais.
- Visita de pássaros é simulada como evento, mas arte/animação do pássaro estava pendente no documento.
- O protótipo limita entidades por mapa carregado (120 plantas, 180 sementes, 90 frutos e 24 sementes transportadas) e processa no máximo 25 dias virtuais por atualização.
- HTML e Godot mantêm saves separados; o módulo não tem multiplayer nesta etapa.
- Botão “Semear (teste)” planta semente sem custo; não representa inventário nem propriedade de terra.
- Parâmetros de temperatura, tempos e reprodução são explicitamente provisórios de balanceamento, não dados botânicos.

Os valores acima são parâmetros do simulador consultado, não regras ecológicas canônicas do mangá.

## 5. Terras, economia e coop local — requisitos planejados

Fonte: `Apoena-pixel-art-html/docs/TERRAS_E_COOP.md`.

**NÃO IMPLEMENTADO no documento consultado:**
- parcelas privadas e permissões de plantio/colheita;
- plantar, colher, vender, negociar e acumular recursos em inventário;
- caça, monstros, dungeons e dragão no modo exploração/história;
- coop entre dois celulares por Bluetooth ou Wi-Fi Direct.

O documento propõe anfitrião como autoridade da simulação local; clientes enviariam comandos e receberiam eventos/estado confirmados. Propõe compartilhar mapa e combater o mesmo inimigo mesmo com níveis diferentes. Uma redução de 30% da efetividade do dano do convidado foi registrada apenas como proposta inicial de balanceamento, a definir em testes — não é regra final.

Progressão, moeda, inventário e ranking MOBA devem ser validados no servidor em partidas de rede, segundo o documento de requisitos.

## 6. Jogo Godot 3D — estado descrito no README

Fonte: `apoenalore/JOGO-APOENA-AGAR-/README.md`. O README é mutável e descreve uma alfa/protótipo; conferir o código e os testes antes de afirmar o estado atual.

- Arena MOBA 3D offline contra IA, com três rotas, torres, núcleos, tropas e combate/loja alfa. O README descreve um mapa 01 de 1 km², com 18 torres (9 por equipe), e também descreve em outra seção condição de vitória com três torres por equipe; não unificar regras sem conferir a implementação e o contexto de cada modo.
- Arena não é 5v5 online; multiplayer e compras reais são declarados ausentes.
- Modo História alfa tem percursos separados, seleção de herói/avatar e seis mapas de teste em Agar/Pandora/Arkana; mundo aberto contínuo, geografia canônica completa, NPCs definitivos, narrativas finais e multiplayer online são declarados ausentes.
- O README descreve Apoena, Oriom, Serena e Ubirara como opções de personagem no jogo. A nomenclatura deve ser comparada com as fichas canônicas; não equiparar automaticamente Oriom/Orium ou Ubirara/Birará.
- Constelações: interface de 13 constelações; Serpentário aparece mas não é equipável. Bônus são de gameplay experimental e explicitamente não canônicos.
- Técnicas Q/W/E/R/F do Apoena inicial são descritas como integradas ao protótipo, com valores/efeitos específicos no README. São habilidades de jogo provisórias e não devem ser transplantadas para a obra sem aprovação.
- Modelos, animações, habilidades e efeitos são provisórios. O README registra que a experiência de retargeting de animação de Volibear para CH44 foi reprovada e o binário defeituoso não foi integrado.
- O README informa modelos GLB de personagens e fontes 3D grandes preservadas em branch separada. A existência desses caminhos não significa que os binários tenham sido arquivados nesta biblioteca.

## 7. GameCreator — fronteira editor/runtime

Fonte: `apoenalore/GameCreator/README.md` e `PLANO_GERAL_APOENA.md`.

O GameCreator é ferramenta de autoria. O jogo é o runtime. O Creator produz assets, spritesheets, tilesets, mapas, objetos e metadados/contratos; o runtime executa história, exploração, MOBA, economia, NPCs, ecossistema e persistência.

Não criar inventários duplicados nem duplicar a Fábrica Universal de Itens. Não presumir que exportar PNG/JSON ou cadastrar uma espécie significa que ela já funciona no gameplay.

O README consultado descreve ferramentas para:
- edição de pixel art e spritesheets com transparência, âncora inferior, ações/direções por quadro e exportação PNG/JSON;
- biblioteca central de assets e projetos editáveis com backup/restauração;
- mapas 2.5D, tilesets, autotile e verificação de bordas/dimensões;
- catálogo portátil de itens/receitas e integração Godot para inventário, coleta, fabricação temporizada e persistência.

O README também registra limites: a sincronização entre ferramentas e a sessão V4.0 não instala assets automaticamente no runtime; transições de animação e importação no Godot exigem validação no consumidor; Android físico exige teste próprio.

## 8. Lore Engine

Fonte: `apoenalore/que-projeto-e-esse/README.md`.

Nome de produto documentado: **Lore Engine 1.0.0**; estágio descrito: protótipo técnico 0.2.0. É um editor 3D independente, voltado a PC/Android, com humanoide procedural experimental, parâmetros básicos, perfis `.lore.json` e exportação GLB experimental. O README afirma que o humanoide não tem rig, skinning, animações ou qualidade final. Não editar este repositório ao trabalhar no runtime do jogo ou Studio Maker; exportações GLB só devem ser distribuídas quando explicitamente autorizadas.

## 9. Limites e contradições a verificar

- README do jogo 3D contém seções com contagens de torres/condições de vitória que podem pertencer a iterações ou modos distintos. Verificar código e cenas.
- Nomes: Oriom/Orium, Ubirara/Ubirará e Birará aparecem em contextos diferentes. Não presumir equivalência.
- O plano geral descreve sistemas desejados; os READMEs descrevem estados de protótipos em momentos diferentes. A implementação precisa ser conferida em branch/commit atual.
- Coop do conceito geral e coop local do Pixel Art são descrições relacionadas, mas não necessariamente o mesmo escopo/protocolo.
- Nenhum dos detalhes deste arquivo deve alterar o cânone narrativo sem aprovação explícita.
