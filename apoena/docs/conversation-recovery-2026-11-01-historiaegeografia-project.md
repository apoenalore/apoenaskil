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


## Conversas adicionais já lidas nesta sessão anterior

### Livro dos 6 Eixos — fonte e camada oculta

O autor descreveu o Livro dos 6 Eixos como registro escrito por alguém que viveu em Agar na Era de Tupi e recolheu histórias da perspectiva de seu tempo. Título/assinatura informados pelo autor: “Livro dos 6 Eixos — Por Glaucius Tupi Filho de Tupi no ano 99 da Criação.”

É uma fonte histórica interna e interpretativa, não narração onisciente. Separar o acontecimento passado da forma como Glaucius o compreendeu a partir de tradição oral. O autor explicou que Agar está em ruínas; uma ruína ainda a escolher será de Glaucius, onde ele escondeu o Livro das Origens. Essa ruína e o modo de chegar até ela continuam pendentes.

Tupi e Glaucius escreveram em Aurélico. A leitura exige domínio intenso de Aurium. Apoena aprende no Mundo Espiritual uma técnica de visão/percepção que lhe permite ler esse nível. O original do Livro dos 6 Eixos está com Cauam; há cópias famosas em Agar, mas apenas o original conserva a camada Aurélica oculta. Cauam pode possuir o original sem compreender o segredo. A pista no original deve indicar a localização/caminho até a ruína e o Livro das Origens; o autor ainda quer definir que ruína será. Não completar os seis eixos antes de decidir a pista e o local.

O Livro das Origens contém o conhecimento sobre Nairuk e a origem da sombra desconhecida. Em Agar sabe-se que a sombra combate o Grande Espírito, mas não sua identidade/origem. Segundo o autor, Agar está simultaneamente em uma dimensão e em um planeta do qual não se consegue sair: embarcações não sobrevivem ao Oceano Primordial e a vida na superfície já não é adaptada a esse ambiente.

O autor também descreveu mudanças após o cataclismo: pressão/sistema atmosférico mudou, as pessoas deixaram de crescer tanto e os gigantes já não existem na Terra; Nairuk envia monstros menores para atacar a capital, enquanto ameaças maiores podem tentar portais. Humanos de Arcana às vezes atravessam primeiro para interceptá-las; os destinos podem incluir Pandora e Abaddon/outros mundos de Serpentário. Cristais negros podem ser enviados junto com monstros e facilitar aberturas maiores de portais, ampliando energia disponível. Preservar essas relações como relato autoral dessa conversa; detalhes de termos e causalidade ainda devem ser comparados com os livros de cosmologia e demais fontes.

Resumo de Montanha dos Espíritos anteriormente disponível na conversa incluiu montanha/lago, Caverna dos Renascidos, entrada triangular, luz espiritual azul e totens simples de pedra. Como eram elementos recapitulados pelo assistente, e não nova confirmação direta nessa troca, manter como pistas para conferência, não elevar por este registro sozinho.

### Branch · Criação de Personagens

Correções e instruções recuperadas:
- Apoena aos 12 anos deve ter aparência de criança de 12 anos, sem simplesmente reduzir proporcionalmente o modelo de 17 anos.
- Uniforme de estudante da Tribo da Água: camisa azul lisa, sem logotipo, símbolo ou detalhes; calça bege; sandálias.
- “Personagem da Tribo do Fogo aos 12 anos, sem detalhes e sem armas” foi pedido separado e não nomeou Apoena; não fundir os dois pedidos.
- Blin foi pedido aos 12 anos com uniforme estudantil, mas a geração falhou; nenhuma característica física foi estabelecida pela falha.

### Branch · Roupas e Uniformes

A lista inicial de uniformes (oficial, cotidiano, combate/equipamento, cerimônia, símbolos e evolução) foi exploração de categorias, não decisão final de figurino. Não converter a lista inteira em política canônica. Os detalhes confirmados do uniforme da Tribo da Água estão na conversa de personagens acima.

## Fontes conversacionais diretas

Links para as conversas listadas no projeto (sessão do projeto historiaegeografia):
- Linha do tempo Apoena: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ad4b64d-43c8-83e9-b848-d8867dabfa6d?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Tudo sobre as constelações: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6aca93eb-38f0-83e9-a340-d3bfaa78db74?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Interpretar mapa de Agar: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6a85f1c4-c07c-83e9-9613-9dcbec2bddee?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Criar introdução de Apoena: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ac7c864-fb74-83e9-a927-8153d8ba274d?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Recuperar Projeto Game Creator: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ae1eff6-4164-83e8-9972-34499cb2ba2e?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Implementação do Editor Visual: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6adb95a1-6408-83e9-ad46-776100ef25b2?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Livro dos 6 Eixos: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6aad466b-03b4-83e9-b0d4-1bcd26c613fd?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Etapas do jogo Apoena: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6adbb73e-c1d8-83e9-9b01-57a6989f9fbf?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Pendências do Game Creator: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ae23b72-ae24-83e9-adc7-5842f37d47c7?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Branch · Criação de Personagens: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ae55333-422c-83e9-8e01-c4da05a30295?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD
- Branch · Roupas e Uniformes: https://chatgpt.com/g/g-p-6ae1cff6d6d081918faeb79fc6e731ef/shared/c/6ae5532a-9600-83ea-a8c7-96e65c02644e?owner_user_id=user-IlVcbMejJPSetxEG7sVBUhjD

