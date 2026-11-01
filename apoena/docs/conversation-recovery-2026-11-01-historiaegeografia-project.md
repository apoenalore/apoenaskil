# Recuperação de conversas e requisitos do projeto Apoena

Projeto: historiaegeografia  
Data da auditoria: 2026-11-01  
Escopo: leitura seletiva de conversas e integração de decisões recuperadas ao apoenalore/apoenaskil.  
Status: parcial. O índice do projeto mostrou cerca de 30 conversas; os resumos abaixo cobrem conversas lidas nesta rodada e fontes anteriores já registradas. Não é exportação integral do projeto nem de anexos.

## Como interpretar

- Decisão/requisito do autor: declaração direta do usuário, preservada no escopo indicado.
- Fato de fonte: conteúdo que a conversa atribui a livro/PDF; conferir a fonte primária.
- Proposta do assistente: sugestão, não aprovada automaticamente.
- Status histórico: relato de pacote/teste/runner em uma data; não prova estado atual.
- Pendente/conflito: manter aberto até nova decisão ou evidência.

## Conversas lidas nesta auditoria

### Interpretar mapa de Agar — 2026-10-03

Decisão recuperada do autor: o ciclo de água de Agar depende da Montanha dos Espíritos. A neve derrete, a água abastece o país, evapora, retorna como nuvens e precipitação em forma de neve na montanha, onde volta a derreter. Sequência: Montanha dos Espíritos → degelo → cursos d’água → Agar → evaporação → nuvens → neve na montanha → degelo.

A conversa indica que a praia/massa d’água recebe reposição contínua por esse ciclo. O mapa enviado é a referência espacial a preservar, mas não se deve inventar nome geográfico ou nova geologia.

Correção de erro registrada: o assistente propôs clima temperado, aquífero, lago interior e nascentes subterrâneas. O autor lembrou o ciclo que já havia sido definido. A resposta posterior reconheceu que as ideias anteriores eram sugestões, não cânone. Não reincorporar aquífero, oceano externo ou “Grande Lago de Agar” como fatos.

Limite: as cores e marcações do mapa são descritas na conversa, mas a imagem original não foi incorporada neste registro. Medidas e nomes geográficos continuam sujeitos às fontes visuais originais.

### Tudo sobre as constelações — 2026-10-10

O autor escreveu “Serpentario corvo cordeiro”, confirmando nominalmente três constelações: Serpentário, Corvo e Cordeiro. A resposta anterior dizia que apenas Cordeiro e Serpentário estavam identificados; a mensagem posterior do autor confirma Corvo. Não repetir a contagem de apenas duas confirmadas.

Vínculos apresentados como existentes nas fontes consultadas pela conversa, mas que ainda devem ser rastreados às páginas primárias: Serpentário associado a Nairuk e ao planeta Abadom; Cordeiro associado a Kairu e ao sacrifício que elevou a constelação. O autor confirmou Corvo, sem identificar nessa troca seu representante ou história.

As outras dez constelações, seus representantes, planetas, hierarquia, poderes e posição política não ficaram definidos nesta conversa. A lista do zodíaco real e os temas propostos eram ideias do assistente, não cânone. Não usar astrologia tradicional para completar automaticamente as constelações de Apoena.

### Linha do tempo Apoena — 2026-10-18

A conversa organizou uma cronologia a partir de livros/imagens: criação de Tupi, criação de Anahi após sete anos, três anos de convivência e mais três até o fruto; referência a Pandora no ano 4806 e projeção 4826 baseada na fala de que faltavam vinte anos para Agar sair de Pandora.

A própria resposta alertava que a origem da contagem 4806 não estava estabelecida e que o tempo entre os primeiros humanos e o calendário de Pandora não estava calculado. Não somar esses marcos como se compartilhassem um calendário confirmado.

A resposta deixou idades de Apoena, Brin, Kael, Ruf, Serena, Orium e Birará em aberto. É registro histórico, superado para a idade inicial de Apoena por definições posteriores do projeto: Apoena aparece com 12 anos no início e o rito/mudança de classe está associado aos 14. As idades dos demais e a ligação entre eras permanecem abertas salvo fonte posterior específica.

A conversa descreve a sequência da Caverna dos Renascidos e aproximadamente três meses de treinamento espiritual. Para duração, usar o documento canônico atual de caverna/rito e não regressar para versões antigas de três anos.

### Criar introdução de Apoena — 2026-10-08

Requisitos diretos para a introdução discutida: até 1.000 caracteres; resumir sem falar “Aurium”; não nomear “Nairuk” nessa peça e usar “o Dragão”; escrever para leitor que ainda não conhece a obra; criar ganchos de curiosidade e mistério que convidem à leitura.

São requisitos para aquela introdução, não proibição geral dos nomes Aurium/Nairuk na obra. O texto final não aparece na extração acessível (as respostas ficaram em blocos sem texto exposto); este registro preserva os requisitos, não uma versão final.

### Recuperar Projeto Game Creator e Implementação do Editor Visual

Requisitos diretos do autor:
- Pixel Art e Game Creator devem ser partes do mesmo ambiente integrado de autoria; o usuário corrigiu explicitamente que “Pixel Art e Creator é uma coisa só”.
- A página inicial deve abrir o fluxo unificado, com telas e menus compartilhados. Pixel Art fica acessível por navegação dentro do editor, sem um segundo lançador independente.
- Reaproveitar ferramentas existentes e trabalho das versões 3.9/4.0, especialmente geradores e Fábrica Universal de Itens. Revisar antes de reconstruir; remover duplicações/entradas inúteis só após verificar sua função, preservando recursos úteis.
- No editor Pixel Art, poder criar objetos com função e comportamento, incluindo ataque/defesa e resposta a chuva/sol.
- Criar dados no editor não prova que o runtime execute tais comportamentos.

Aparente contradição resolvida: integração Pixel Art + Game Creator é interna ao produto de autoria; o runtime do jogo permanece consumidor separado. A separação de repositórios não deve virar exigência de operar duas ferramentas de autoria desconectadas e tampouco significa fundir o editor ao jogo final.

Combate: não aumentar alcance normal para compensar mira/precisão. Fora do alcance válido, o ataque não acerta. Ataques guiados podem ter alcance ligeiramente maior por configuração do personagem. Seleção/prioridade do alvo não altera colisão; projéteis ainda colidem com tropas, escudos e paredes. Outros modos de mira, câmera ou exploração mencionados pelos assistentes ficam como propostas sem confirmação explícita.

Histórico técnico relatado nos chats: pacotes 3.9.2 e 4.0, contagens de arquivos/scripts e testes isolados (incluindo 8/8 testes de regras e 17 scripts JS). Também aparecem limites: sem confirmação de teste em Godot 4, Android físico ou integração completa no runtime. São relatos históricos do assistente, não verificação atual contra binários/código. Não propagar como status atual.

### Pendências do Game Creator

A conversa agrupa pendências em identidade/spritesheets, editor visual, lógica do motor e projeto/teste/exportação. Uma resposta descreve módulos existentes (layout, fábrica de itens, fatiador, controles PC/Android, personagens/equipamentos, receitas, animação 3D, eventos/regras, simulador, exportação e central de projeto) e pontos a verificar em persistência e Godot. Outro trecho relata bancada V4.0 com testes isolados.

Isso orienta auditoria, mas não é inventário validado do código. Inspecionar o repositório atual antes de declarar módulo funcional.

### Etapas do jogo Apoena

Registro de 2026-10-28: a conversa dizia que não havia nova etapa validada, citava PRs/workflows com falha, ausência de prova de instalação local e pedido do autor para interromper aquela atividade. É estado histórico; não iniciar monitoramento nem alterar o repositório do jogo com base nesse chat. Não usar para descrever o estado atual.

### Conversas de transferência e branches

“Branch · Roupas e Uniformes”, “Branch · Criação de Personagens”, “Branch · IA no jogo”, “Transferir conhecimento Apoena” e “Transferência de conhecimento” incluem instruções de transferência e contexto específico. A auditoria anterior no repositório já registra a regra: separar cânone, decisão, hipótese, rascunho e conflito; preservar proveniência; não duplicar Skills nem apagar versões. Os tópicos de uniforme/personagem também constam em documentos canônicos existentes.

## Inventário visível do projeto

O índice mostrou cerca de 30 conversas:
- Branch · Roupas e Uniformes; Branch · Criação de Personagens;
- Analisar arquivo 3D TENDI; Alterar RPG Maker via GitHub; Diagnóstico da tela azul; Aplicar mapas Google no jogo; Como funcionam IAs 3D;
- Etapas do jogo Apoena; Acompanhamento ativado; Erros do Runner; Lançar jogo Android;
- Criar introdução de Apoena; Tudo sobre as constelações; Interpretar mapa de Agar; Criar estúdio de animação; Título para soberano de Agar;
- Ideias para ChatGPT Plus; Recuperar Projeto Game Creator; Implementação do Editor Visual; Roteiro casa na roça; Livro dos 6 Eixos; Corrigir arquivos Godot; Linha do tempo Apoena;
- Começar primeiro mapa; Descrição para Kwai; Modelando cabeça no Blender; Transferir conhecimento Apoena; Transferência de conhecimento; Branch · IA no jogo; Aurium Constelações Poderes; Pendências do Game Creator; Nomes para spritesheets.

A lista é inventário da interface, não significa que cada conversa foi revisada integralmente nesta rodada.

## Conversas a revisar integralmente

- Aurium Constelações Poderes (incluindo anexo “Texto colado.txt”, ainda não localizado no repositório);
- Livro dos 6 Eixos (texto/autoria e pistas escritas pelo usuário);
- Branch · IA no jogo; Acompanhamento ativado; Erros do Runner; Lançar jogo Android; Corrigir arquivos Godot;
- Título para soberano de Agar; Criar estúdio de animação; Começar primeiro mapa; Analisar arquivo 3D TENDI;
- Nomes para spritesheets; Aplicar mapas Google no jogo; Como funcionam IAs 3D e demais ramos específicos;
- anexos e imagens que não aparecem integralmente na árvore de acessibilidade.

## Atualizações no repositório

Requisitos de autoria integrada e limites de combate foram acrescentados a game-design-recovered.md e às Skills de implementação/arquitetura. O ciclo hídrico, constelações nomeadas, correções de cronologia, requisitos editoriais e pendências foram registrados neste arquivo e no inventário geral. Esta atualização é documental; nenhum teste de código foi executado.
