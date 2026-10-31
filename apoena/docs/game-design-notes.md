# Notas de sistemas de jogo recuperadas — Apoena

**Atualização:** 2026-10-30  
**Status geral:** inventário parcial de conversas e documentos acessíveis; não é uma especificação final nem uma bíblia canônica.

## 1. Decisão de prototipagem

**DECISÃO DO AUTOR:** HTML é usado para testar rapidamente no celular; o jogo pronto seguirá para Godot. O HTML não deve ser tratado como destino final de produção nem como conversão automática para Godot.

Fonte: conversa de projeto Pixel Art, na qual o autor esclareceu que HTML serve para testar rápido no celular e que o resultado final irá para Godot. Registro: `decisions/DEC-0001-html-prototyping-godot-production.md`.

## 2. Conceito de visita cooperativa a mundos

**EM DESENVOLVIMENTO — ideia relatada pelo autor; detalhes não fechados.**

O autor descreveu uma experiência em que cada jogador tem seu mundo de exploração e pode convidar um amigo para dentro dele, ou visitar o mundo do amigo. Durante a visita, poderiam realizar missões, construções e ataques de monstros em equipe.

A conexão do anfitrião foi citada como possível limite. O princípio de transferência desejado é compartilhar somente informações específicas necessárias à sessão — por exemplo, coletas, itens e construções — sem transmitir/rotear o mapa completo do mundo principal do jogador. Ao retornar ao próprio mundo, o visitante receberia prêmios/resultados.

### Não definido no material recuperado
- Se o anfitrião é autoridade definitiva do estado e como validar ações.
- Como são resolvidos conflitos entre saves.
- Como são calculadas e entregues recompensas.
- O que acontece em desconexão, rollback ou sessão abandonada.
- Limites de jogadores, distância, duração, sincronização e segurança.
- Como os dados de construções/coletas são serializados ou versionados.

Não transformar essas perguntas em decisões sem validação do autor.

## 3. Mundo grande e Godot

O autor perguntou sobre a capacidade do Godot para suportar um mapa muito grande e apontou a necessidade de elaborar a arquitetura. **A conversa recuperada registra a pergunta, mas não uma decisão técnica aprovada.**

Streaming por regiões, chunks, carregamento/descarregamento, simulação local e representação de áreas distantes podem ser avaliados como alternativas, sempre rotuladas como propostas técnicas até aprovação.

## 4. Pixel Art / Floresta Viva

O repositório `apoenalore/Apoena-pixel-art-html` documenta um jogo com dois modos — MOBA e exploração/Floresta Viva — e protótipos HTML e Godot distintos. O protótipo Godot tem câmera 2.5D inicial (câmera 2D elevada, acompanhamento, zoom e ordenação por Y), não câmera 3D 360° nem isometria completa.

O ecossistema documentado inclui bananeira, jabuticabeira, javali, sementes, frutos, umidade, nutrientes, clima, decomposição e dispersão. Os valores de balanceamento e artes geométricas são marcados como provisórios. Para regras completas e atualizadas, consultar:
- `docs/ecology-game-notes.md` nesta biblioteca.
- `apoenalore/Apoena-pixel-art-html/docs/ECOSSISTEMA.md`
- `apoenalore/Apoena-pixel-art-html/docs/TERRAS_E_COOP.md`
- `apoenalore/Apoena-pixel-art-html/docs/ORGANIZACAO.md`

Não copiar os valores do simulador para o cânone do mangá.

## 5. Projeto Godot 3D separado

O repositório `apoenalore/JOGO-APOENA-AGAR-` contém protótipos Godot 4 de arena/MOBA e Modo História. Seus documentos registram:
- Godot 4 e GDScript como engine/linguagem do projeto; não migrar para Unity nem misturar APIs/pastas de outro motor.
- Objetivo de longo prazo inicial: PvP familiar 2x2 e coop; plano 5v5 de 25–40 minutos é referência futura, não entrega atual.
- Estado descrito em documentos: treino e Modo História offline; multiplayer online não implementado.
- Sistema prototipado de Energia Elementar: Q/W/E/R gastam reserva interna sem cooldown individual por relógio; ataque básico físico não gasta essa reserva. Barras e custos são abstrações de gameplay, não valores canônicos de Aurium.
- O conhecimento comum em Agar chama a força de **Força Vital / Energia Elementar**; o nome Aurium é conhecimento mais profundo, em parte perdido.
- Apoena começa a história sem manifestação elemental; as habilidades simuladas com manopla no jogo são provisórias. Isso não substitui a predisposição de linhagem documentada no resumo de Aurium.

Esses pontos são específicos do projeto de jogo e devem ser conferidos contra o repositório atual antes de declarar implementação.

## 6. Constelações e bênçãos

A documentação do jogo registra 13 constelações: Cordeiro tem 10 pontos estelares, as 11 seguintes têm 7 pontos cada e Serpentário tem 9. Após a rebelião de Nairuk, Serpentário deixou a Aliança Cósmica, que passou a reunir doze constelações; Serpentário aparece como histórico e não equipável.

O jogo prototipa bênção principal (+10%) e apoio (+4%) sobre atributos de gameplay. Os pareamentos de atributos são hipóteses de game design, não significado espiritual canônico. Detalhes em `docs/constellations-system.md` e Skill `apoena-constellations-and-blessings`.

## Relações
- Poderes: `docs/aurium-system.md` e Skill `apoena-aurium-system`.
- Cânone: `docs/canon-status.md`.
- Coop e sistemas: Skill `apoena-game-systems`.
- Natureza: `docs/ecology-game-notes.md` e Skill `apoena-ecology-systems`.
- Transferência HTML/Godot: Skill `apoena-godot-prototyping`.

## Histórico
- 2026-10-30: consolidação inicial a partir do contexto de conversas compartilhadas e documentação acessível nos repositórios de jogo. Lacunas mantidas explícitas.
