---
name: apoena-game-systems
description: Organiza sistemas de jogo do universo Apoena sem confundir protótipos, conceitos em desenvolvimento e cânone narrativo.
---
# Skill — Sistemas de jogo Apoena

## Princípio de separação
O jogo adapta o universo, mas **mecânica provisória não altera automaticamente o cânone da obra**. Consulte `docs/canon-status.md` e a documentação do repositório de jogo relevante. Nunca misture arquivos, regras ou validações dos projetos distintos.

## Projetos que não devem ser confundidos
- `apoenalore/Apoena-pixel-art-html`: projeto Pixel Art, com modos MOBA e exploração/Floresta Viva. HTML é uma forma de testar rapidamente no celular; o destino de produção definido pelo autor é Godot.
- `apoenalore/JOGO-APOENA-AGAR-`: projeto separado de jogo Godot 4, com protótipos MOBA 3D e Modo História. Seus documentos marcam personagens, habilidades, mapas e sistemas alfa como provisórios quando assim indicado.
- `apoenalore/GameCreator`: ferramenta de autoria separada; não copiar o editor inteiro para dentro do runtime do jogo.
- `apoenalore/projeto-apoena-studio-maker-ia`: Studio/Maker, separado do runtime do jogo.

Se a tarefa não indicar qual projeto, pergunte antes de editar ou misturar estruturas.

## Sistemas e objetivos de jogo registrados
- O projeto `JOGO-APOENA-AGAR-` documenta Godot 4/GDScript como base; não migrar para Unity nem misturar APIs/pastas de outro motor.
- Objetivo inicial de longo prazo descrito nos documentos: PvP familiar 2x2 e coop; plano 5v5 de 25–40 minutos é referência futura, não entrega atual. O estado documentado continua offline sem multiplayer online validado.
- Em Agar, a força é chamada no conhecimento comum de Força Vital/Energia Elementar; Aurium é conhecimento profundo, parcialmente perdido.
- No protótipo, Q/W/E/R consomem uma reserva interna, sem cooldown individual por relógio; ataque básico físico não consome energia. Isso é gameplay, não escala numérica canônica de Aurium.
- Apoena começa a história sem manifestação elemental; técnicas com manopla em gameplay são provisórias e não definem automaticamente cânone.

## Conceitos de cooperação relatados pelo autor
Status: **IDEIA EM DESENVOLVIMENTO**, não especificação final.
- Jogador explora seu próprio mundo e pode convidar alguém para entrar; também pode visitar o mundo de outra pessoa.
- Durante a visita, os jogadores poderiam fazer missões, construir e enfrentar monstros em equipe.
- A velocidade/qualidade da conexão do anfitrião foi mencionada como possível limite.
- A intenção é não transmitir nem rotear o mapa completo do mundo principal do visitante/anfitrião. Compartilhar apenas os dados específicos necessários, como eventos de coleta, itens e construções.
- Ao voltar ao mundo próprio, o visitante receberia os prêmios/resultados da sessão.
- Não há especificação confirmada de autoridade de rede, protocolo, persistência, prevenção de fraude, sincronização, limites de sessão ou compensação por desconexão. Não apresente essas soluções como decisões do autor.

## Procedimento para elaborar mecânicas
1. Marque cada item como **IMPLEMENTADO**, **DOCUMENTADO**, **PROPOSTA**, **PENDENTE** ou **DESCONHECIDO**, usando evidência.
2. Separe o que é regra narrativa de cânone do que é balanceamento do jogo.
3. Especifique entrada, estado alterado, custo, recompensa, persistência, falhas e condições de saída.
4. Para coop, defina primeiro quais eventos/dados são compartilhados; não presuma replicação integral de mundo.
5. Não invente mapas, NPCs, criaturas, progressão, economia ou valores de combate.
6. Antes de afirmar implementação, consulte código/testes atuais do repositório correspondente.

## Fontes de referência
- `docs/game-design-notes.md` — ideias recuperadas e seu status.
- `docs/aurium-system.md` e `docs/constellations-system.md` — regras de poder/constelações documentadas.
- `docs/ecology-game-notes.md` — natureza do protótipo.
- `docs/canon-status.md` — fontes e lacunas do cânone.
- Repositórios de jogo citados acima — detalhes técnicos específicos e mutáveis.


## Cânone e desenvolvimento
A Bíblia Oficial — Cânone Mestre é a fonte prioritária para lore quando mecânicas de jogo ou PDFs antigos divergirem. Parâmetros de gameplay (barras, números, cooldowns, bônus de constelação, valores de dano) não se tornam regras narrativas sem aprovação explícita. O sistema de jogo pode adaptar Aurium, mas deve indicar o que é cânone, especificação de jogo, implementação, teste ou proposta. Para o escopo e a separação de repositórios, consultar a Skill apoena-game-development.
