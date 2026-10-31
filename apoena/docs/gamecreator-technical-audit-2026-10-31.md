# Auditoria técnica e roteiro de engenharia — Game Creator e Apoena Pixel Art

**Data da inspeção:** 2026-10-31  
**Hora do registro:** não disponível na fonte.  
**Natureza:** auditoria documental e estática, baseada em código, testes, workflows, PRs e documentação dos repositórios consultados.  
**Regra:** este documento é uma fotografia técnica da data indicada. Antes de implementar qualquer correção, confira novamente a branch, o commit e os arquivos atuais.

## 1. Por que este relatório existe

Este relatório evita que futuras IAs recomecem a investigação do zero, confundam um erro de código com uma falha de infraestrutura ou declarem pronta uma funcionalidade que só existe como formulário, metadado ou protótipo.

Ele cumpre cinco funções:

1. Preservar evidências verificáveis: arquivos, commits, testes, workflows e PRs.
2. Separar implementação, validação isolada e integração real no jogo.
3. Registrar riscos de segurança, perda de dados e publicação de versões.
4. Definir a ordem de trabalho para não abrir muitas frentes simultâneas.
5. Preparar a próxima camada técnica sem alterar o cânone, a arte ou o código sem autorização.

O relatório não corrige o programa por si só. Ele funciona como mapa de decisão e memória operacional. A Skill associada transforma os critérios deste relatório em um método reutilizável por outras IAs.

## 2. Escopo e commits consultados

| Repositório | Branch consultada | Commit consultado | Responsabilidade |
|---|---|---|---|
| [GameCreator](https://github.com/apoenalore/GameCreator) | main | 0bd916157d9bfab6c6c9b121c26050f94918cf80 | Editor, biblioteca, mapas, sprites, exportação e integração |
| [Apoena Pixel Art HTML](https://github.com/apoenalore/Apoena-pixel-art-html) | main | a54eb4328640f97cd1e4020f7fa85c96c3070017 | Jogo HTML/Godot, exploração, MOBA e ecossistema |
| [Apoena Skills](https://github.com/apoenalore/apoenaskil) | main | 85951c2549aaf5e4edcf0e0116a531e5e1bc6e57 | Conhecimento reutilizável, decisões e Skills |

Foram consultados, entre outros:

- GameCreator: AGENTS.md, README.md, ORGANIZACAO_EDITOR.md, PLANO_GERAL_APOENA.md, AUDITORIA_CODIGO_EXISTENTE.md, STATUS_V4_0_ETAPA_1.md, RECUPERACAO_FONTE_V4_0_2026-10-28.md e a fila ATUALIZACOES_PENDENTES_LEIA_ANTES_DE_COMECAR.md.
- Código do Creator: shared/asset-library.js, shared/library-backup.js, shared/creator-bridge.js, pixel-art/estudio.js, pixel-art/modulo-integrado.js, pixel-art/ponte-creator.js, map-editor/index.html, map-editor/terrain-system.js, map-editor/world-object-system.js, integracao/catalogo.js e integracao/godot/ApoenaCatalogo.gd.
- Testes do Creator: seis arquivos na pasta tests/, quatro testes em integracao/testes/ e o teste GDScript integracao/godot/tests/test_catalogo.gd.
- Pixel Art: AGENTS.md, docs/ORGANIZACAO.md, docs/ECOSSISTEMA.md, docs/TERRAS_E_COOP.md, scripts/mundo_2_5d.gd e scripts/ecossistema_agar.gd.
- Workflows, logs recentes e estado das PRs #4, #5, #6 e #7.

### Como interpretar os estados

- **CONFIRMADO NO CÓDIGO:** o comportamento ou estrutura foi localizado no arquivo.
- **TESTADO ISOLADAMENTE:** existe teste automatizado que cobre o módulo ou contrato.
- **VALIDADO NO RUNTIME:** o comportamento foi executado no motor ou navegador de destino.
- **INTEGRADO:** o fluxo completo entre Creator e jogo consumidor foi comprovado.
- **PARCIAL:** existe uma parte, mas não a experiência completa solicitada.
- **PENDENTE:** não foi comprovado como implementado.
- **HIPÓTESE:** explicação plausível que ainda precisa de reprodução.
- **RISCO DE INSPEÇÃO:** fragilidade identificada no código, ainda sem exploração ou reprodução controlada.

Não converter CONFIRMADO NO CÓDIGO em VALIDADO NO RUNTIME.

## 3. Arquitetura que já existe — não reconstruir

### 3.1 Game Creator

O Creator já possui uma base considerável:

- Fonte original V4.0 e módulos V4.1.
- Gerador/estúdio de spritesheets, recorte por grade e manual, transparência e Corte Inteligente.
- Editor de mapas com terrenos, tilesets, objetos, alturas e marcadores.
- Biblioteca central baseada em IndexedDB, busca, metadados e backup/restauração.
- Regras de terreno e objetos em módulos separados.
- Catálogo portátil de itens e receitas.
- Ponte de mensagens entre ferramentas e Creator principal.
- Exportação de dados para integração Godot.
- Testes de contratos, catálogo, biblioteca, backup, recorte, tilesets, ponte e sistemas ambientais.

A ferramenta já está além de um protótipo vazio. A prioridade é estabilizar contratos, persistência e integração, não criar outro editor ou outra biblioteca.

### 3.2 Dimensão e organização da fonte

A árvore atual do GameCreator contém:

- Fonte original APOENA_GAME_CREATOR_V4_0_BANCADA_INTEGRADA.html: 16.332.595 bytes.
- index.html: 16.333.266 bytes.
- bundle-v4/: 24 partes, total de 16.361.705 bytes.

As três representações somam aproximadamente 49 MB, antes dos demais módulos e recursos.

Há uma divergência documental: ORGANIZACAO_EDITOR.md descreve index.html como entrada compacta que monta o Creator a partir de bundle-v4, mas o arquivo index.html atualmente versionado tem aproximadamente 16,3 MB. O build_unificado.ps1 compila a fonte original quando ela está presente e mantém um caminho alternativo para o caso de fonte vazia. O fallback também depende de um marcador de comprimento fixo (full.length!==16324808).

**Conclusão:** não apagar nem reestruturar as partes históricas agora. Primeiro definir a fonte canônica, o artefato gerado, o fallback e um manifesto de integridade com SHA-256. O comprimento do arquivo sozinho não é uma prova robusta de integridade.

### 3.3 Integração Godot do Creator

O projeto integracao/godot é identificado como “Apoena Catalogo Integration Tests”. Ele contém ApoenaCatalogo.gd, JSON de catálogo e teste GDScript; não é o runtime completo do jogo.

O contrato de catálogo já contempla validação de IDs, itens, receitas, coleta, fabricação, inventário, sessão e alguns efeitos instantâneos. O método de uso de item reconhece explicitamente três efeitos instantâneos. Efeitos temporários, combate, física, NPCs, animações e multiplayer não passam a existir só porque aparecem em um formulário ou JSON.

A suíte Godot atual comprova o módulo de catálogo, não a importação e execução de um mapa completo, de uma animação ou de uma partida.

### 3.4 Apoena Pixel Art

O projeto consumidor possui HTML e Godot, mas são implementações separadas. A documentação do próprio jogo informa que não há APK validado e que ainda faltam, entre outros pontos, TileMaps com atlas e colisões, inventário/coleta persistentes, MOBA completo em Godot e refinamento da câmera 2.5D.

O projeto Godot consultado contém três cenas principais e quatro scripts de jogo em scripts/: clima, ecossistema, menu e mundo 2.5D. mundo_2_5d.gd desenha partes do mundo com _draw(), usa câmera 2D e ordenação visual; isso não equivale a um mundo 3D completo ou streaming de mundo aberto.

O ecossistema possui limites explícitos de população e processamento, o que é uma boa base para mobile. Os limites atuais são parâmetros do protótipo, não metas finais de capacidade.

### 3.5 Diferença de versões Godot

O workflow de integração do GameCreator baixa Godot 4.7.2. Os workflows do Apoena Pixel Art usam Godot 4.4.1.

Isso cria uma matriz de compatibilidade não declarada. Um contrato testado em 4.7.2 não está automaticamente comprovado no runtime 4.4.1.

**Ação necessária:** definir uma versão de produção compartilhada ou manter uma matriz explícita de versões suportadas e executar o mesmo conjunto de testes de importação nas versões declaradas.

## 4. Achados críticos

### F-01 — Runner local executa código de Pull Request

**Prioridade:** P0 de segurança, condicionada às permissões de colaboração.

O workflow .github/workflows/pixel-art.yml do GameCreator recebe pull_request e executa em [self-hosted, Windows, X64]. O workflow validar-pixel-art-windows.yml do Pixel Art também recebe pull_request e usa [self-hosted, Windows, X64, pixel-art]. O segundo workflow validar-godot.yml também usa o runner próprio em PRs.

Os repositórios consultados são privados, portanto não estão abertos a qualquer usuário da internet. Mesmo assim, pessoas ou contas com acesso suficiente para abrir PRs podem fornecer código que será executado no computador do Runner.

O risco não é eliminado por permissions: contents: read. O processo de teste executa scripts, dependências e código da branch no host Windows. Um runner persistente não equivale a uma VM descartável.

**Recomendação:**

1. Executar PRs em runner hospedado e isolado, quando possível.
2. Reservar o runner local para pushes confiáveis na main e tarefas manuais controladas.
3. Se o runner local continuar necessário para PR, limitar rigorosamente quem pode abrir/autorizar essas execuções e revisar o código antes de permitir execução.
4. Executar o serviço do runner em conta Windows de baixo privilégio, sem acesso a documentos pessoais, credenciais e pastas desnecessárias.
5. Não manter PAT, senha ou segredo pessoal no ambiente do runner.
6. Não usar pull_request_target para contornar o problema e depois executar código da branch não confiável.

A orientação oficial do GitHub alerta que runners próprios podem ser comprometidos por código não confiável, inclusive em repositórios privados quando colaboradores com acesso conseguem abrir PRs.

**Estado:** risco confirmado pela configuração; nenhuma exploração foi executada.

### F-02 — Cota de artefatos do GitHub Actions esgotada

**Prioridade:** P0 operacional.

No run [#41189083410](https://github.com/apoenalore/GameCreator/actions/runs/41189083410), commit 0bd916157d9bfab6c6c9b121c26050f94918cf80, o build e as verificações anteriores passaram. A falha ocorreu na publicação dos artefatos.

Mensagem registrada:

Failed to CreateArtifact: Artifact storage quota has been hit.

O run registrou preparação do pacote de 76 arquivos e dos diagnósticos. A falha de upload não deve ser classificada como falha de compilação ou de teste.

Foram observadas 11 execuções concluídas com falha no mesmo SHA da main, além de uma execução cancelada na sequência. O log do run mais recente confirma a cota como causa da etapa de publicação; não foi feita inspeção individual dos logs de todas as execuções anteriores.

A configuração atual possui:

- schedule a cada hora.
- Preparação de entrega executada com if: always().
- Upload do pacote com if: always().
- Upload dos diagnósticos com if: always().
- Nenhum retention-days explícito nas duas ações upload-artifact.

A documentação do GitHub informa que artefatos usam a retenção configurada no repositório, normalmente 90 dias por padrão, e que podem ser removidos manualmente para recuperar armazenamento. O README de actions/upload-artifact também informa que a cota de armazenamento compartilhada pode impedir novos uploads e que o cálculo de armazenamento não é necessariamente imediato.

**Recomendação:**

1. Verificar e limpar artefatos antigos somente após identificar quais podem ser descartados. A exclusão é irreversível; não fazer limpeza automática sem autorização.
2. Definir retention-days curto para diagnósticos de CI.
3. Manter artefato de entrega por período maior somente quando necessário.
4. Não gerar pacote completo em cada execução agendada.
5. Publicar pacote de entrega somente após sucesso dos testes e em push confiável/manual de release.
6. Publicar diagnósticos quando houver falha, com retenção curta.
7. Usar o agendamento, se mantido, como verificação leve, sem publicar ZIP completo a cada hora.

**Estado:** causa da última falha comprovada; correção ainda não aplicada.

### F-03 — Entrega local pode substituir pacote mesmo após falha

**Prioridade:** P0 de integridade de entrega.

No workflow do GameCreator, a etapa “Preparar entrega na pasta ChatGPT trabalho do runner” usa if: always(). Ela prepara o ZIP e copia o diretório GameCreator-V4.1 para a pasta de entrega local.

Antes de copiar, o script remove recursivamente a pasta de destino GameCreator-V4.1, caso ela exista. O upload do pacote e o upload dos diagnósticos também usam if: always().

Isso cria dois riscos:

- Um pacote pode ser preparado e disponibilizado mesmo que um teste anterior tenha falhado.
- Arquivos adicionados manualmente dentro da pasta GameCreator-V4.1 de destino podem ser apagados pela substituição recursiva.

**Recomendação:**

1. Separar validação, empacotamento e publicação.
2. Pacote de entrega: executar apenas depois de sucesso de todas as verificações obrigatórias.
3. Diagnósticos: preservar em caso de falha, sem publicar pacote de produção.
4. Gerar primeiro em diretório temporário/versionado.
5. Validar manifesto, quantidade de arquivos, hashes e versão.
6. Publicar em diretório de saída dedicado, sem apagar arquivos desconhecidos.
7. Se for necessário substituir uma versão anterior, preservar backup e oferecer recuperação.
8. Nunca substituir a instalação definitiva a partir de uma execução reprovada.

**Estado:** comportamento destrutivo confirmado pela inspeção do workflow; nenhuma pasta local do usuário foi alterada nesta auditoria.

### F-04 — Recuperação do IndexedDB pode ficar presa após erro inicial

**Prioridade:** P1 de confiabilidade.

Em shared/asset-library.js, openDB() guarda a Promise de abertura em dbPromise. Os handlers request.onerror e request.onblocked rejeitam a Promise, mas não redefinem dbPromise para null. Depois de uma rejeição inicial, novas chamadas podem reutilizar a mesma Promise rejeitada, mesmo depois de o usuário fechar a outra aba que bloqueava a abertura.

O handler onversionchange redefine dbPromise, mas os caminhos de erro e bloqueio não fazem o mesmo.

**Correção proposta:** limpar dbPromise nos caminhos de falha, sem criar múltiplas aberturas concorrentes. Testar: primeira abertura bloqueada, fechar a outra aba, tentar novamente sem recarregar a página e confirmar recuperação.

**Estado:** fragilidade demonstrada pela leitura do fluxo; ainda não reproduzida em navegador.

### F-05 — Restauração de backup não é transação única

**Prioridade:** P1 de integridade de dados.

shared/library-backup.js valida o snapshot inteiro antes de importar. Isso é positivo e impede que um backup estruturalmente inválido comece a ser aplicado.

Entretanto, depois da validação, assets e projetos são gravados em sequência, cada um por uma operação de biblioteca. Se o armazenamento atingir a cota ou uma transação falhar no meio, os primeiros registros já gravados podem permanecer enquanto os seguintes falham.

**Correção proposta:** planejar importação transacional ou estratégia de staging/rollback. No mínimo, manter relatório de registros aplicados, identificar a importação incompleta e oferecer recuperação sem apagar dados anteriores.

**Teste ausente:** simular QuotaExceededError no meio de uma restauração com vários registros e provar que o resultado é recuperável e não deixa estado silenciosamente parcial.

### F-06 — Ponte V4.0/V4.1 precisa de endurecimento

**Prioridade:** P1 de segurança.

shared/creator-bridge.js usa postMessage com targetOrigin "*" e aceita origem "null" no listener. O receptor verifica canal, tipo de mensagem e existência de event.source; o handler do Pixel Art também possui lista de ações reconhecidas e validações de schema.

Isso não prova uma exploração. O uso de origem opaca pode estar relacionado à abertura local por file://, então não se deve trocar "*" por uma origem fixa sem testar o cenário real.

Pontos de endurecimento:

- Vincular a sessão à janela esperada e realizar handshake com nonce aleatório de uso único.
- Restringir ações e validar o schema de cada payload no receptor.
- Limitar tamanho de mensagens, dimensões de imagens, quantidade de tiles e frequência de chamadas.
- Não aceitar origem null de forma ampla sem prova de que a janela é a esperada.
- Evitar transportar PNGs base64 gigantes pela ponte quando for possível passar referências a recursos salvos na biblioteca.
- Garantir timeout e remoção dos listeners em todos os caminhos.

Em pixel-art/ponte-creator.js, saveMap limita a grade a 512×512. savePixelAsset limita metadados a 50 KB, mas a validação da string PNG não apresenta limite de tamanho no próprio receptor. O limite de importação da interface não substitui validação no ponto de entrada da ponte.

### F-07 — Contrato Creator → jogo ainda não é ponta a ponta

**Prioridade:** P1 de arquitetura.

O Creator já exporta catálogos, sprites, mapas e metadados. Porém, a documentação do Apoena Pixel Art informa que a transferência de recursos ainda envolve copiar arquivos para assets/ e que a ponte do Creator precisa de validação integrada no jogo.

O catálogo Godot é um harness de testes separado, não o runtime completo. A ficha de natureza exportada pelo Creator ainda não substitui automaticamente os parâmetros internos do simulador ecológico.

A ausência de um pacote de conteúdo versionado e de um importador único cria risco de:

- ID duplicado ou perdido.
- imagem sem manifesto ou manifesto sem imagem.
- regra ambiental cadastrada no Creator, mas ignorada pelo jogo.
- colisão e altura desenhadas no editor, mas inexistentes no runtime.
- divergência entre HTML e Godot.
- importação de assets incompatíveis sem aviso.

**Solução arquitetural:** um pacote de conteúdo versionado, com manifesto, schemas, IDs estáveis, caminhos relativos, hashes, dimensões, metadados e validação. O importador do Godot deve rejeitar versões incompatíveis e relatar campos ausentes, sem inventar defaults que alterem o gameplay.

### F-08 — Conflito de teclado em formulários

**Prioridade:** P1 de usabilidade.

A fila existente registra GC-KEY-007. pixel-art/modulo-integrado.js intercepta keydown no document e verifica se e.target é INPUT, SELECT ou TEXTAREA. Em Shadow DOM, eventos podem sofrer retargeting; o alvo observado fora da raiz pode ser o host, não o campo interno. Isso pode fazer WASD ser interceptado durante a digitação.

**Estado:** hipótese técnica forte, ainda não reproduzida em navegador.

**Correção proposta:** inspecionar event.composedPath(), isContentEditable e controles editáveis; só interceptar atalhos quando a arena estiver ativa e nenhum campo editável estiver no caminho. Revisar keyup e perda de foco para não deixar tecla presa.

### F-09 — Autotiling é específico do perfil, não universal

**Prioridade:** P2, depois de confirmar a tela usada.

A fila GC-TILE-002 documenta que o editor atual aplica conexões automáticas somente a determinados perfis e índices fixos de atlas. A verificação de tileset identifica dimensões, transparência e repetição de bordas, mas não reconhece semanticamente centro, margem, canto, curva ou transição.

A recarga de mapa pela biblioteca também precisa preservar o perfil do tileset; o registro existente aponta que um fluxo separado força manual ao reabrir.

**Solução proposta:**

1. Manter pintura manual como modo permanente.
2. Separar peça individual de terreno automático.
3. Permitir que o usuário mapeie as peças do atlas para centro, bordas, cantos e transições.
4. Salvar esse perfil junto ao tileset e restaurá-lo sem perda.
5. Recalcular células vizinhas após pintura, borracha, preenchimento, desfazer/refazer e carregamento.
6. Criar testes para margens, rios, lagos, curvas, cruzamentos e limites do mapa.

Não prometer autotiling universal para qualquer PNG sem configuração ou reconhecimento validado.

### F-10 — Biblioteca e experiência ainda não completam o fluxo do autor

**Prioridade:** P2.

A fila GC-LIB-006 confirma que IndexedDB, busca, metadados e backup existem. Isso não equivale a gravação automática em uma pasta do Windows nem comprova que todos os perfis de comportamento sobrevivem a salvar, fechar, reabrir e reutilizar.

GC-UX-004 registra a sequência desejada pelo autor:

1. Criar/importar recursos.
2. Definir comportamentos e animações.
3. Reencontrar o recurso na biblioteca.
4. Abrir o editor de mapas e posicioná-lo sem importar novamente.

As abas de personagens, objetos e mapas já existem, mas o percurso completo ainda não foi comprovado sem repetição de importação ou perda de metadados.

### F-11 — Rig 2D por partes ainda não está implementado

**Prioridade:** P2, após estabilizar biblioteca e contratos.

O estúdio atual já faz recorte de imagens, organização de quadros, ações, direções e exportação de spritesheet. Isso não equivale a um editor de rig 2D completo.

O requisito GC-ANIM-005 preserva dois modos:

- Spritesheet tradicional.
- Personagem por partes recortadas, pivôs, hierarquia de ossos, camadas, timeline, keyframes e profundidade simulada.

A rota técnica mais econômica para o jogo é testar Skeleton2D, Bone2D e Polygon2D do Godot. Para o editor HTML, criar um manifesto de rig que possa ser validado e importado pelo runtime. A profundidade simulada deve ser descrita como 2.5D/pseudotridimensional, não como reconstrução volumétrica automática.

### F-12 — Salvamento do runtime precisa de proteção contra interrupção

**Prioridade:** P2 de confiabilidade.

ApoenaCatalogo.gd e scripts/ecossistema_agar.gd escrevem JSON diretamente no arquivo de sessão/salvamento de destino. O fluxo atual abre com WRITE e grava o conteúdo. Não foi encontrado, nos trechos inspecionados, um ciclo completo de arquivo temporário, verificação, backup anterior e substituição recuperável.

**Solução proposta:** salvar snapshot temporário, verificar escrita e parse, manter cópia anterior válida, substituir apenas após verificação e testar encerramento forçado durante a gravação. A estratégia precisa ser validada no Windows e Android; não presumir atomicidade idêntica em todos os sistemas de arquivos.

### F-13 — A fila de PRs está fragmentada

Na data consultada:

| PR | Tema | Estado | Mergeable |
|---|---|---|---|
| [#4](https://github.com/apoenalore/GameCreator/pull/4) | Sessões, MOBA 5v5 e sistemas de mundo | Draft aberto | Não |
| [#5](https://github.com/apoenalore/GameCreator/pull/5) | Teste de hidrologia | Draft aberto | Sim |
| [#6](https://github.com/apoenalore/GameCreator/pull/6) | Biomas e hidrologia | Aberto | Não |
| [#7](https://github.com/apoenalore/GameCreator/pull/7) | Atualizador local incremental GC-UPDATE-009 | Draft aberto | Sim |

Nenhuma dessas PRs estava integrada à main na consulta. PR mergeable não significa testada ou pronta; mergeable false exige investigação de conflito/base.

A PR #7 continua sendo o WIP de código registrado para GC-UPDATE-009. O teste estático do parser/manifesto não substitui simulações de clone, fast-forward, offline, branch errada, alteração local, interrupção e preservação do Runner.

**Regra:** manter WIP = 1 somando Creator e Pixel Art. Não abrir nova frente de implementação enquanto o bloqueio atual e a segurança da entrega não estiverem resolvidos.

## 5. Lista de prioridades recomendada

A prioridade abaixo considera risco, dependência e impacto. Ela não autoriza implementação automática.

| Ordem | Prioridade | Tarefa | Por que vem agora | Critério de saída |
|---|---|---|---|---|
| 1 | P0 | Proteger o Runner local contra PR não confiável | Evita execução de código de terceiros no computador do usuário | PR não executa código não confiável no host local |
| 2 | P0 | Corrigir o ciclo de entrega e o uso da cota | CI atual não consegue publicar; pacote pode ser preparado mesmo após falha | Artefato só sai após sucesso; retenção explícita; pasta local não apaga dados desconhecidos |
| 3 | P1 | Recuperação do IndexedDB e restauração segura | Biblioteca é base de todos os recursos; falha aqui afeta todo o Creator | Retry sem recarregar, quota simulada, backup recuperável |
| 4 | P1 | Resolver GC-KEY-007 | Digitação básica bloqueada impede uso dos formulários | WASD funciona na arena e letras funcionam em todos os campos |
| 5 | P1 | Definir versão Godot e contrato de conteúdo | O Creator precisa exportar dados que o runtime realmente entenda | Matriz de versão, schema versionado e importação testada |
| 6 | P2 | Corrigir e generalizar autotiling | Mapa é um dos produtos centrais do Creator | Perfil salvo, atlas mapeável, vizinhos recalculados, pintura manual preservada |
| 7 | P2 | Reorganizar fluxo da interface | Reduz erro operacional e importações repetidas | Percurso recurso → comportamento → biblioteca → mapa sem perda |
| 8 | P2 | Rig 2D por partes e profundidade simulada | Amplia animação sem obrigar Blender ou GPU dedicada | Um personagem completo exporta e anima no Godot |
| 9 | P2 | Integrar colisão, interação e ambiente de objetos | Metadados do Creator precisam virar comportamento real | Bananeira/árvore testada no mapa com colisão, interação e save |
| 10 | P3 | Streaming de mundo, IA de NPC e multiplayer | Sistemas grandes dependem de contratos, saves e runtime estáveis | Protótipos isolados com orçamento de memória e CPU |
| 11 | P3 | Pipeline 3D verdadeiro | É uma extensão, não pré-requisito para concluir o fluxo 2D aprovado | Importação GLB, rig/animação e perfil de hardware comprovados |

### Sequência prática

**Fase A — Segurança e entrega:** runner, permissões, artefatos, condições de publicação e proteção da pasta local.

**Fase B — Dados confiáveis:** IndexedDB, backups, schemas, migrações, salvamento recuperável e compatibilidade entre versões.

**Fase C — Uma fatia vertical completa:** criar um personagem ou planta no Creator, salvar, fechar, reabrir, exportar, importar no Godot, exibir, animar/interagir e salvar novamente. O mesmo teste deve provar um mapa pequeno com tiles, colisão e objeto.

**Fase D — Ferramentas de autoria:** autotiling, fluxo de navegação, biblioteca por categorias e rig 2D.

**Fase E — Escala do jogo:** chunks, carregamento assíncrono, simulação ecológica por distância, navegação, NPCs e cooperação.

Não avançar para Fase E enquanto a Fase C não for reproduzível.

## 6. Arquitetura recomendada para desempenho

### 6.1 Mundo aberto 2D

Não representar o mundo inteiro como uma única cena ou um único TileMapLayer gigantesco.

Adotar:

- Mundo lógico dividido em regiões com coordenadas inteiras.
- Cada região subdividida em chunks de tamanho configurável.
- Um gerenciador de chunks que decide carregar, manter, descarregar e salvar.
- Dados persistentes separados da representação visual.
- Alterações do jogador armazenadas como estado/delta da região, não como cópia completa do mundo a cada ação.
- Carregamento antecipado apenas da vizinhança necessária.
- Instanciação e alteração da árvore de cenas na thread principal.

TileMapLayer possui coordenadas serializadas limitadas a inteiros de 16 bits assinados, de -32768 a 32767. Isso reforça a necessidade de coordenadas locais por chunk, em vez de um mapa infinito dentro de uma única camada.

O tamanho do chunk não deve ser escolhido por palpite. Começar com poucos perfis de teste, medir tempo de geração, memória, draw calls, colisões e custo de atualização, e então escolher o melhor compromisso.

### 6.2 Carregamento e atualização

Usar ResourceLoader.load_threaded_request() para solicitar recursos em segundo plano e acompanhar o estado em quadros posteriores. Não chamar load_threaded_get() antes de o recurso estar pronto, pois isso pode bloquear a thread chamadora.

Carregar dados e recursos em segundo plano quando seguro; adicionar nós à cena ativa na thread principal. Não compartilhar mutações de containers e Resources entre threads sem respeitar as regras de segurança do Godot.

### 6.3 Renderização 2D/2.5D

- Preservar pixel art nítida e filtro nearest quando adequado.
- Separar chão, decoração, entidades, sombras, elementos altos e efeitos em camadas coerentes.
- Usar ordenação por Y onde a regra visual exigir.
- Separar colisão física da área visual: uma árvore pode ter tronco sólido e copa atravessável.
- Evitar recalcular toda a cena quando uma única célula mudar.
- Aproveitar o batching de TileMapLayer; não chamar update_internals() a cada célula.
- Testar a interação entre Y-sort, altura lógica, camadas e objetos de vários tiles.

### 6.4 Mundo 3D e objetos repetidos

Para grandes populações de árvores, grama, rochas e elementos repetidos, avaliar MultiMesh por região. Um MultiMesh é eficiente em draw calls, mas não faz culling independente por instância; por isso, dividir por chunks ou setores de visibilidade.

Aplicar LOD, oclusão, distância de atualização e redução/pausa de animações distantes. Evitar iluminação dinâmica e geometria excessiva sem medição em hardware-alvo.

### 6.5 Navegação e IA

Não recalcular o caminho de todos os NPCs a cada quadro. Atualizar o destino apenas quando a mudança for relevante, distribuir consultas entre quadros e simplificar a malha de navegação.

Para mapas em grade, avaliar AStarGrid2D ou navegação por regiões conforme o tipo de movimento. Para navegação baseada em malhas, usar bake simplificado e em segundo plano quando necessário.

### 6.6 Ecossistema e mundo persistente

A lógica ecológica já possui limites de entidades. Evoluir para níveis de simulação:

- Perto do jogador: simulação completa.
- Próximo, mas fora da tela: atualização simplificada por intervalos/eventos.
- Região distante: avanço agregado por tempo decorrido, sem processar cada planta a cada quadro.
- Região descarregada: guardar estado e aplicar eventos ao retornar.

A simulação deve ser determinística quando necessário, limitada por orçamento e testada com populações máximas. Não fazer varreduras globais em _process() sem necessidade.

## 7. Arquitetura de dados e segurança

### 7.1 Pacote de conteúdo

Criar um contrato de conteúdo que separe:

- Manifesto do pacote.
- Assets binários.
- Spritesheets e animações.
- Rigs 2D.
- Tilesets e perfis de autotile.
- Mapas e chunks.
- Objetos, colisões e interações.
- Catálogo de itens/receitas.
- Metadados de versão e compatibilidade.

Cada recurso deve ter ID estável, schema, versão, tipo, dimensões, hash SHA-256, caminho relativo e referências válidas. Evitar duplicar PNG base64 em vários estados JSON quando o asset já existe na biblioteca.

### 7.2 Importação defensiva

Validar extensão, MIME real, assinatura do arquivo, tamanho em bytes, dimensões, total de pixels, quantidade de quadros, profundidade de JSON, número de entidades e limites de mapa.

Não confiar em nome, categoria, caminho, ID ou metadados enviados por outra janela. Nunca usar eval ou executar texto importado como código.

### 7.3 DOM e mensagens

Usar textContent e criação de elementos para valores externos. innerHTML só deve receber templates estáticos ou conteúdo sanitizado com política explícita.

Na ponte de mensagens, validar origem, janela esperada, nonce, canal, ação, schema e limites de payload. A origem null deve ser tratada como caso específico de contexto opaco, não como autorização genérica.

### 7.4 Dados locais

IndexedDB é armazenamento local sujeito a quota e políticas do navegador. Tratar QuotaExceededError como condição esperada, exibir mensagem útil, permitir backup e nunca confirmar salvamento antes da conclusão da transação.

LocalStorage deve ficar restrito a preferências pequenas; não guardar segredos ou credenciais. Não presumir que a biblioteca do navegador equivale a uma pasta do Windows.

### 7.5 Salvamento do jogo

Usar versões de schema, validação, arquivo temporário, verificação, backup da última versão válida e substituição controlada. Testar arquivo ausente, JSON inválido, campo desconhecido, migração, pouco espaço, encerramento inesperado e recuperação.

## 8. Direção visual e pipeline de animação

A referência aprovada para o jogo permanece pixel art 2D anime, top-down/three-quarter e profundidade visual 2.5D. A identidade do mangá continua 2D; não substituir a direção visual por CGI.

A ordem recomendada para animação é:

1. Spritesheet tradicional, que já possui uma base no Creator.
2. Rig 2D por partes, pivôs, ossos, camadas e keyframes.
3. Profundidade simulada por ordenação, escala, deslocamento, perspectiva e sombreamento controlados.
4. Exportação para um formato versionado e importador Godot.
5. Só então avaliar modelos 3D verdadeiros para objetos específicos.

Godot oferece Skeleton2D, Bone2D e Polygon2D para animação esquelética 2D. Isso é uma alternativa nativa para experimentar cutout animation sem exigir Blender no fluxo cotidiano do usuário.

Para assets 3D verdadeiros, glTF 2.0 é o formato recomendado; GLB é a opção binária conveniente. OBJ tem limitações relevantes para pivôs, esqueletos e animações.

## 9. Critérios mínimos de qualidade

Nenhuma tarefa deve ser marcada como concluída sem:

- Causa ou requisito descrito.
- Arquivos e contratos envolvidos.
- Teste de unidade ou contrato.
- Teste de regressão dos dados antigos.
- Teste de persistência salvar → fechar → abrir → recuperar.
- Teste no runtime de destino quando a funcionalidade for de jogo.
- Resultado de CI no commit correto.
- Teste visual/manual quando a interface ou arte for afetada.
- Evidência de desempenho em hardware representativo.
- Registro de limitações, rollback e riscos restantes.

Uma suíte verde não prova o jogo completo. Um JSON válido não prova integração. Uma cena que inicia por 30 quadros não prova gameplay. Um protótipo HTML não prova exportação Android.

Não prometer software sem bugs. O objetivo é reduzir defeitos, tornar falhas detectáveis, evitar perda de dados e garantir recuperação previsível.

## 10. O que esta auditoria não fez

- Não alterou código do GameCreator.
- Não alterou código do Apoena Pixel Art.
- Não alterou workflows, runners ou permissões.
- Não apagou artefatos do GitHub.
- Não fez merge das PRs.
- Não alterou o cânone, personagens, arte ou balanceamento.
- Não declarou funções planejadas como implementadas.

As alterações desta entrega são somente documentos e instruções reutilizáveis no repositório Apoena Skills.

## 11. Próxima decisão recomendada

Antes de abrir uma nova funcionalidade, decidir e autorizar a correção dos três bloqueios P0: fronteira de confiança do Runner, política de artefatos e publicação segura. Em seguida, manter apenas uma tarefa de código ativa e priorizar a recuperação da biblioteca e o fluxo de conteúdo Creator → Godot.

A primeira prova de maturidade do Creator não deve ser um recurso novo. Deve ser conseguir criar um recurso, salvá-lo, fechar o programa, reabri-lo, encontrá-lo, exportá-lo, importá-lo no jogo, utilizá-lo e recuperar o estado sem perda ou intervenção manual inesperada.
