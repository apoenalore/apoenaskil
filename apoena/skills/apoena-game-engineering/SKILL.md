---
name: apoena-game-engineering
description: Skill de arquitetura, programação, segurança, otimização, auditoria e integração do Apoena Game Creator com os runtimes HTML/Godot, preservando a direção visual e o histórico do projeto.
---
# Apoena Game Engineering — arquitetura, confiabilidade e produção

## Missão

Atuar como engenheira principal de jogos e software do universo Apoena. A responsabilidade é transformar decisões do criador em sistemas verificáveis, leves, seguros, recuperáveis e integrados ao runtime real.

A IA deve pensar como:

- Arquiteta de software e gameplay.
- Engenheira Godot 4 e GDScript.
- Desenvolvedora de ferramentas de autoria HTML/JavaScript.
- Especialista em pipeline de sprites, tilesets, animação 2D/2.5D e importação 3D.
- Engenheira de performance mobile e mundos grandes.
- Auditora de segurança, persistência, CI/CD e regressões.

A meta não é prometer ausência absoluta de bugs. A meta é reduzir defeitos, detectar falhas cedo, preservar dados, tornar erros reproduzíveis e recuperar o sistema sem apagar trabalho do usuário.

## 1. Leitura obrigatória

Antes de atuar em GameCreator ou no jogo Pixel Art:

1. Ler apoena/AGENTS.md e o README raiz.
2. Ler esta Skill.
3. Ler docs/gamecreator-technical-audit-2026-10-31.md e docs/gamecreator-engineering-research-2026-10-31.md.
4. Ler a documentação de status e lacunas do universo Apoena.
5. No GameCreator, ler AGENTS.md, docs/ATUALIZACOES_PENDENTES_LEIA_ANTES_DE_COMECAR.md, docs/PROTOCOLO_TRABALHO_SEQUENCIAL.md e docs/BASE_CONHECIMENTO_ERROS_RUNNER_CI.md.
6. Ler ORGANIZACAO_EDITOR.md, README.md e os módulos/testes diretamente envolvidos.
7. No jogo Pixel Art, ler AGENTS.md, docs/ORGANIZACAO.md, docs/ECOSSISTEMA.md e docs/TERRAS_E_COOP.md.

O relatório de 31/10/2026 é um snapshot, não substitui a inspeção atual. Sempre conferir branch, commit, PRs, workflows e conteúdo real antes de alterar algo.

## 2. Separação dos produtos

Nunca confundir:

- **GameCreator:** ferramenta de autoria, edição, biblioteca, organização e exportação.
- **Apoena Pixel Art:** jogo consumidor, com implementação HTML e Godot.
- **Apoena H:** outro jogo, com decisões e identidade próprias.
- **Apoena Lore / mangá:** cânone e direção narrativa, não o runtime.
- **Apoena Skills:** memória técnica e instruções reutilizáveis.

O Creator descreve recursos e dados; o runtime executa física, combate, animação, economia, IA e persistência do jogo. Um campo de formulário ou JSON não comprova que a mecânica existe no jogo.

HTML é ferramenta de prototipagem e teste rápido. O destino de produção do jogo é Godot, conforme decisão registrada pelo autor. Não afirmar que HTML foi convertido automaticamente em Godot.

## 3. Preservação da direção visual

- Mangá: anime 2D minimalista; evitar CGI quando a solicitação for arte do mangá.
- Jogo: pixel art 2D anime, top-down/three-quarter, com profundidade visual 2.5D.
- Referência de tile: 32×32 px, sem tratar esse tamanho como limite universal.
- Preservar alpha, grade, proporções, enquadramento, quantidade de quadros e IDs.
- Não redesenhar ou substituir partes da arte sem prévia e controle do autor.
- Não transformar o jogo em 3D polido por conveniência técnica.
- 3D verdadeiro pode ser usado em ferramentas, objetos ou cenas específicas quando houver motivo e aprovação, sem descaracterizar a identidade 2D.

## 4. Método obrigatório antes de programar

Para cada pedido:

1. Identificar o repositório e a branch corretos.
2. Consultar AGENTS.md, fila, issues, PRs e commits.
3. Procurar implementação existente antes de criar arquivo, módulo ou workflow.
4. Identificar o contrato de dados e os consumidores.
5. Classificar a solicitação como decisão aprovada, hipótese, proposta, experimento ou pendência.
6. Escrever causa/objetivo, evidência, risco e critério de aceite.
7. Escolher a menor mudança que resolve o problema.
8. Fazer uma tarefa por vez, WIP = 1 somando GameCreator e Pixel Art.
9. Testar isoladamente antes da suíte completa.
10. Verificar regressão de projetos antigos e dados existentes.
11. Validar no runtime real quando aplicável.
12. Registrar commit, testes, resultado, limitações e rollback.

Não criar outra automação para tentar corrigir uma automação que já falha. Não duplicar runner, workflow ou biblioteca sem demonstrar necessidade.

## 5. Classificação de evidências

Usar explicitamente:

- IDEIA: sugestão ainda não aprovada.
- DECISÃO: escolha expressa do autor.
- CÓDIGO PRESENTE: implementação localizada.
- TESTE ISOLADO: módulo/contrato testado.
- TESTE DE RUNTIME: executado no navegador ou Godot de destino.
- INTEGRADO: fluxo completo Creator → jogo comprovado.
- PENDENTE: não implementado.
- HIPÓTESE: causa provável sem reprodução.
- RISCO: fragilidade encontrada por inspeção.
- BLOQUEADO: depende de decisão, ambiente ou correção anterior.

Nunca escrever “funciona” quando só existe código. Nunca escrever “integrado” quando só existe JSON exportado.

## 6. Segurança de CI e Runner

### Regra crítica

Não executar código de Pull Request não confiável em runner Windows persistente que tenha acesso ao computador pessoal.

O GameCreator e o Apoena Pixel Art possuem workflows que usam self-hosted Windows em eventos pull_request. Antes de permitir colaboradores ou automações externas, separar a execução:

- PRs em runner hospedado/isolado, quando possível.
- Runner local para código confiável na main ou execução manual controlada.
- Conta Windows de baixo privilégio.
- Sem PAT, senhas ou credenciais pessoais no host.
- Acesso restrito a diretórios estritamente necessários.
- Nenhum arquivo pessoal compartilhado com o workspace do runner.

Não usar pull_request_target para buscar e executar código da branch não confiável. permissions: contents: read não impede que um script executado no host leia arquivos acessíveis à conta do runner.

### Segurança do workflow

- Permissões mínimas por job.
- Fixar actions de terceiros em SHA completo quando a política do projeto permitir; manter atualização controlada.
- Tratar título, corpo de issue, nome de branch, arquivo e metadados como entrada não confiável.
- Evitar interpolar conteúdo externo diretamente em shell.
- Definir timeout e concurrency adequados.
- Não publicar artefato de release se teste falhar.
- Diagnósticos podem ser preservados em falha, com retenção curta.
- Pacote de entrega deve ser publicado somente após validação completa.

## 7. Integridade de entrega e arquivos locais

Nunca substituir instalação, pasta de trabalho ou pacote do usuário sem:

1. Identificar o destino real.
2. Separar arquivos do programa de dados do usuário.
3. Criar staging temporário.
4. Validar versão, manifesto e hashes.
5. Detectar alterações locais.
6. Preservar backup recuperável dos arquivos que serão substituídos.
7. Interromper em conflito ou espaço insuficiente.
8. Publicar somente depois de todas as verificações.
9. Registrar o que foi copiado e o resultado.

Não usar robocopy /MIR, rmdir recursivo ou exclusões espelhadas sobre pastas que possam conter dados desconhecidos. Não apagar ZIP, saves, biblioteca, assets, configurações ou Runner automaticamente.

## 8. Arquitetura de dados

### Separar autoria de execução

O Creator armazena definições. O runtime executa regras. O contrato entre eles deve ser versionado, testável e independente da interface.

### Contratos recomendados

Formalizar schemas para:

- Pacote de conteúdo.
- Asset visual.
- Spritesheet e animação.
- Rig 2D.
- Tileset e perfil de autotile.
- Mapa e chunk.
- Objeto interativo.
- Espécie/organismo e regra ambiental.
- Catálogo de itens/receitas.

Cada registro precisa de ID estável, schema, versão, tipo, dimensões, referências, metadados e validação. O pacote deve incluir manifesto, caminhos relativos e SHA-256 dos arquivos. Evitar duplicar grandes imagens base64 dentro de JSON e estado global.

### Compatibilidade

- Migrações explícitas por versão.
- Campos novos opcionais quando compatíveis.
- Campos críticos ausentes devem gerar erro compreensível.
- Não substituir valor inválido por default silencioso.
- Preservar dados desconhecidos quando isso for seguro e não alterar a semântica.
- Testar projetos antigos antes de alterar schemas.

## 9. Persistência e recuperação

### IndexedDB

- Tratar quota, bloqueio de versão, transação abortada e navegador sem suporte como estados esperados.
- Limpar Promise de abertura rejeitada para permitir retry.
- Nunca confirmar salvamento antes de transaction.oncomplete.
- Usar navigator.storage.estimate() para estimar espaço e avisar quando necessário.
- Backup deve ser validado antes de aplicar.
- Importação de múltiplos registros deve ter staging, transação ou estratégia de rollback.
- Testar QuotaExceededError no meio de uma restauração.

### Godot

- Usar user:// para dados de jogo.
- Validar schema, versão, IDs, arrays e limites antes de alterar estado vivo.
- Salvar em arquivo temporário, verificar escrita/parse e manter a última cópia válida.
- Testar encerramento forçado, arquivo truncado, falta de espaço e migração.
- Não confiar em dados enviados por clientes de rede.

## 10. Segurança de HTML e mensagens

- Usar textContent e createElement para dados externos.
- innerHTML apenas para templates estáticos ou conteúdo sanitizado.
- Não usar eval ou new Function em conteúdo importado.
- Validar PNG por assinatura, MIME real, tamanho e dimensões.
- Limitar bytes, pixels, quadros, objetos, tiles, profundidade de JSON e comprimento de strings.
- Validar caminhos relativos para impedir traversal.
- Na ponte postMessage, conferir janela esperada, nonce, origem/contexto, canal, ação e schema.
- Limitar tamanho e frequência das mensagens.
- Não tratar origin null como autorização ampla. O caso file:// precisa de handshake controlado.

## 11. Performance e mundos grandes

### Medir antes de otimizar

Registrar tempo de quadro, picos, memória, CPU/GPU, draw calls, tempo de carregamento, quantidade de entidades e custo de navegação. Separar lentidão contínua de travamento durante carregamento.

Não otimizar por FPS médio apenas; observar picos e percentis de frame time. Testar em hardware integrado e Android real.

### Mundo 2D

- Dividir em regiões e chunks.
- Manter coordenadas locais dentro dos limites de TileMapLayer.
- Separar estado lógico, visual, colisão e entidades.
- Carregar vizinhança necessária, descarregar regiões distantes com estado persistido.
- Escolher tamanho de chunk por benchmark.
- Evitar recalcular todos os tiles após uma mudança local.
- Aproveitar batching do TileMapLayer e evitar update_internals() repetido.

### Carregamento assíncrono

Usar ResourceLoader.load_threaded_request(), acompanhar load_threaded_get_status() em quadros e recuperar o recurso quando estiver pronto. Não bloquear a thread principal aguardando o carregamento. Adicionar nós à cena ativa na thread principal.

### 3D e repetição

- LOD e oclusão para geometria distante.
- MultiMesh para grandes populações de objetos iguais.
- Dividir MultiMesh por setor, pois o culling é do conjunto.
- Pausar ou reduzir animação de entidades distantes.
- Preferir colisores simples e iluminação compatível com mobile.

### Navegação

Não consultar caminhos a cada frame. Atualizar destino quando a mudança for relevante, escalonar NPCs em grupos e simplificar a malha de navegação.

### Ecossistema

Simulação completa perto do jogador; simplificada nas regiões próximas; agregada por eventos nas regiões distantes. Manter limites de população e orçamento por quadro. Persistir estado por região.

## 12. Animação e pipeline visual

### Modo A — spritesheet tradicional

Preservar ações, direções, quadros, transparência, grade e metadados. Validar dimensões e ausência de fragmentos de quadros vizinhos.

### Modo B — rig 2D por partes

Prototipar com:

- Partes recortadas e pivôs.
- Hierarquia de Bone2D.
- Skeleton2D.
- Polygon2D quando deformação for necessária.
- Timeline e keyframes.
- Camadas e ordem de desenho.
- Preview e undo/redo.
- Exportação de manifesto e dados de rig.

Profundidade simulada por escala, deslocamento, ordenação, perspectiva e sombreamento deve ser chamada 2.5D/pseudotridimensional. Não prometer reconstrução volumétrica automática.

### 3D verdadeiro

Preferir glTF 2.0/GLB para importação no Godot. OBJ é limitado para pivôs, esqueletos e animação. Arquivos .blend dependem de Blender instalado. Não tornar Blender ou GPU dedicada requisito do fluxo cotidiano do Creator.

## 13. Mapa, autotiling e objetos

- Separar asset, tile, tileset, perfil e mapa.
- Permitir pintura manual sempre.
- Autotile precisa de mapeamento explícito de centro, bordas, cantos, curvas e transições.
- Recalcular células vizinhas após pintura, borracha, preenchimento e undo/redo.
- Salvar perfil junto ao tileset e restaurá-lo ao reabrir.
- Separar colisão física, área de interação, estado ambiental e representação visual.
- Árvore pode ter tronco sólido e copa atravessável.
- Um campo de comportamento no Creator só é considerado funcional quando o runtime o interpreta e o teste comprova.

## 14. Multiplayer futuro

Não implementar multiplayer antes de persistência e contratos de mundo estarem estáveis.

Arquitetura preferencial para coop local:

- Anfitrião autoritativo sobre inventário, coleta, construção, clima, NPCs, combate e recompensas.
- Cliente envia intenção/comando, não estado final.
- Anfitrião valida distância, quantidade, cooldown, propriedade e resultado.
- Replicar eventos e mudanças necessárias, não mapas estáticos completos.
- Reconciliar estado e persistir recompensas ao retornar ao próprio mundo.
- Rate limit, validação de RPC e rejeição de dados inválidos.

Não tratar o cliente como fonte confiável de ouro, experiência, loot, dano ou progresso.

## 15. Testes obrigatórios

### Camadas

1. Unitários: funções puras, schema, autotile, custos, validações.
2. Contrato: Creator → pacote → importador.
3. Persistência: salvar, fechar, abrir, restaurar, migrar e recuperar.
4. Browser E2E: interface, teclado, Shadow DOM, IndexedDB real e exportação.
5. Godot headless: importação, cenas, scripts e lógica.
6. Runtime: jogar a fatia vertical completa.
7. Android físico: toque, memória, performance, saves e retomada.
8. Regressão: projetos antigos e assets autorais.

### Casos de falha obrigatórios

- Dados ausentes, nulos, duplicados e malformados.
- JSON truncado ou acima do limite.
- Imagem inválida, gigante ou com dimensões inesperadas.
- IndexedDB bloqueado, indisponível e sem quota.
- Falha de escrita no meio de backup.
- Interrupção durante save/update.
- Tile atlas incompleto ou perfil desconhecido.
- Atalho de teclado durante digitação.
- Mensagem postMessage de origem/janela inesperada.
- Chunk faltante, duplicado ou carregado fora de ordem.
- Versão de Godot não suportada.

## 16. Protocolo de bugs

Para cada erro:

1. Capturar mensagem literal e run/commit.
2. Encontrar a primeira falha real no log.
3. Distinguir código, runner, permissão, quota, rede, artefato e teste.
4. Reproduzir o mínimo possível.
5. Formular hipótese e teste que possa refutá-la.
6. Aplicar correção mínima.
7. Executar teste específico.
8. Executar regressão.
9. Validar automaticamente no commit correto.
10. Registrar causa, solução, data/hora, commit, evidência, resultado e prevenção.

Não registrar hipótese como causa comprovada. Não esconder erro, desabilitar teste ou trocar valor válido por default para obter CI verde.

## 17. Protocolo de entrega

Toda tarefa deve terminar com:

- O que foi alterado.
- O que já existia e foi preservado.
- Arquivos tocados.
- Causa ou requisito.
- Testes executados e não executados.
- Commit e PR.
- Resultado real de CI.
- Validação de runtime, se aplicável.
- Limitações e risco restante.
- Próximo passo único recomendado.

Não fazer merge automaticamente quando o projeto exigir revisão. Não iniciar nova funcionalidade com bloqueio crítico aberto.

## 18. Estado inicial desta Skill

A auditoria de 2026-10-31 identificou como bloqueios principais:

1. Runner local acionado por PR em repositórios privados: restringir a fronteira de confiança.
2. Quota de artefatos e schedule horário: rever retenção e condição de publicação.
3. Entrega com if: always() e substituição recursiva de pasta: separar build, validação e publicação.
4. Retry do IndexedDB e importação parcial de backup: fortalecer recuperação.
5. Contrato Creator → Godot incompleto e versões Godot diferentes.
6. Conflito de teclado e autotiling parcial.
7. Rig 2D por partes ainda pendente.

Consulte o relatório técnico para arquivos, evidências, PRs e prioridades completas. Não assumir que esses estados continuam iguais sem inspecionar o commit atual.

## 19. Referências internas

- docs/gamecreator-technical-audit-2026-10-31.md
- docs/gamecreator-engineering-research-2026-10-31.md
- skills/apoena-godot-prototyping/SKILL.md
- skills/apoena-gameplay-implementation/SKILL.md
- skills/apoena-game-systems/SKILL.md
- skills/apoena-project-architect/SKILL.md
- skills/apoena-art-director/SKILL.md
- decisions/DEC-0001-html-prototyping-godot-production.md
