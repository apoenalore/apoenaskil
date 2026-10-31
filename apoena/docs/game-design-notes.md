# Notas de sistemas de jogo recuperadas — Apoena

**Atualização:** 2026-10-30  
**Status geral:** inventário parcial de conversas e documentos acessíveis; não é especificação final nem bíblia canônica.

Para detalhes recuperados dos READMEs e planos dos projetos, consulte também:
- `docs/game-design-recovered.md` — modos, progressão, ecossistema, jogo 3D, GameCreator e Lore Engine.
- `docs/repository-map.md` — responsabilidades dos repositórios.
- `docs/ecology-game-notes.md` e Skill `apoena-ecology-systems` — ecossistema de protótipo.

## 1. Decisão de prototipagem
**DECISÃO DO AUTOR:** HTML é usado para testar rapidamente no celular; o jogo pronto seguirá para Godot. HTML não é destino final nem conversão automática para Godot.

## 2. Conceito de visita cooperativa a mundos
**EM DESENVOLVIMENTO — ideia relatada pelo autor; detalhes não fechados.**

Cada jogador teria seu mundo de exploração e poderia convidar um amigo ou visitar o mundo dele. Durante a visita, poderiam realizar missões, construções e ataques de monstros em equipe. A conexão do anfitrião foi citada como possível limite. A intenção é compartilhar somente dados específicos necessários à sessão (coletas, itens e construções), sem transmitir o mapa completo do mundo principal; ao retornar, o visitante receberia os prêmios/resultados.

Não estão definidos autoridade de rede, resolução de conflitos de save, recompensas, desconexão, rollback, limites de jogadores, sincronização ou segurança. Não transformar essas lacunas em decisões.

## 3. Mundo grande e Godot
O autor perguntou sobre a capacidade do Godot para suportar mapa muito grande. **Não foi recuperada uma decisão de arquitetura aprovada.** Streaming por regiões, chunks e carregamento sob demanda são alternativas para avaliação, não decisões do autor.

## 4. Pixel Art / Floresta Viva
O repositório `apoenalore/Apoena-pixel-art-html` documenta um jogo com modos MOBA e exploração/Floresta Viva e protótipos HTML e Godot separados. A câmera Godot inicial é 2.5D (câmera 2D elevada, acompanhamento, zoom e ordenação por Y), não câmera 3D 360° nem isometria completa.

Consulte `docs/game-design-recovered.md` e as fontes `docs/ECOSSISTEMA.md`, `docs/TERRAS_E_COOP.md` e `docs/ORGANIZACAO.md` no repositório Pixel Art. Parâmetros do simulador são provisórios, não cânone do mangá.

## 5. Projeto Godot 3D separado
`apoenalore/JOGO-APOENA-AGAR-` contém protótipos Godot 4 de arena/MOBA e Modo História. A documentação registra gameplay offline contra IA e ausência de multiplayer online no estado descrito. As mecânicas, habilidades, constelações e valores de balanceamento são provisórios, não cânone.

## 6. Constelações e bênçãos
O README do jogo 3D e os documentos específicos descrevem 13 constelações, Serpentário visível mas não equipável, e bônus de gameplay experimentais. Consulte `docs/constellations-system.md`; não inventar significados ou efeitos canônicos.

## Histórico
- 2026-10-30: consolidação inicial e expansão a partir do contexto de conversas e documentação acessível.
