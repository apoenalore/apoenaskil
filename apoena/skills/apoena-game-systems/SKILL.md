---
name: apoena-game-systems
description: Organiza sistemas de jogo do universo Apoena sem confundir protótipos, conceitos em desenvolvimento e cânone narrativo.
---
# Skill — Sistemas de jogo Apoena

## Princípio de separação
O jogo adapta o universo, mas **mecânica provisória não altera automaticamente o cânone da obra**. Consulte `docs/canon-status.md` e a documentação do repositório de jogo relevante. Nunca misture arquivos, regras ou validações dos projetos distintos.

## Projetos que não devem ser confundidos
- `apoenalore/Apoena-pixel-art-html`: projeto Pixel Art, com modos MOBA e exploração/Floresta Viva. HTML é uma forma de testar rapidamente no celular; o destino de produção definido pelo autor é Godot.
- `apoenalore/JOGO-APOENA-AGAR-`: projeto separado de jogo Godot 4, com protótipos MOBA 3D e Modo História. Seu README alerta que personagens, habilidades, mapas e sistemas alfa são provisórios quando assim marcados.
- `apoenalore/GameCreator`: ferramenta de autoria separada; não copiar o editor inteiro para dentro do runtime do jogo.
- `apoenalore/projeto-apoena-studio-maker-ia`: Studio/Maker, separado do runtime do jogo.

Se a tarefa não indicar qual projeto, pergunte antes de editar ou misturar estruturas.

## Conceitos de cooperação relatados pelo autor
Status: **IDEIA EM DESENVOLVIMENTO**, não especificação final.
- Jogador explora seu próprio mundo e pode convidar alguém para entrar; também pode visitar o mundo de outra pessoa.
- Durante a visita, os jogadores poderiam fazer missões, construir e enfrentar monstros em equipe.
- A velocidade/qualidade da conexão do anfitrião foi mencionada como possível limite.
- A intenção é não transmitir nem roteirizar o mapa completo do mundo principal do visitante/anfitrião. Compartilhar apenas os dados específicos necessários, como eventos de coleta, itens e construções.
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
- `docs/aurium-system.md` — regras de poder documentadas.
- `docs/canon-status.md` — fontes e lacunas do cânone.
- Repositórios de jogo citados acima — detalhes técnicos específicos e mutáveis.
