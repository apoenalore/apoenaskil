# Pesquisa técnica aplicada — Engenharia do Game Creator e Apoena

**Data da consulta:** 2026-10-31.  
**Hora da consulta:** não disponível na fonte.  
**Método:** documentação oficial primeiro; fóruns e comunidades usados como evidência empírica e geradores de hipóteses, nunca como substitutos de documentação ou benchmark próprio.

## 1. Síntese da pesquisa

A pesquisa sustenta uma estratégia clara para Apoena:

- Medir antes de otimizar.
- Dividir mundos grandes em regiões/chunks, em vez de concentrar tudo numa cena.
- Carregar recursos em segundo plano, mas manipular a árvore de cenas com cuidado.
- Manter a simulação distante mais barata e orientada a eventos.
- Não ativar coordenadas de mundo grande sem necessidade, especialmente no 2D e em dispositivos móveis.
- Usar Skeleton2D/Bone2D para explorar animação cutout 2D antes de criar um rig 3D completo.
- Usar glTF 2.0/GLB para assets 3D verdadeiros.
- Proteger o Runner local, os dados do usuário e a publicação de artefatos.
- Tratar a quota do IndexedDB e do GitHub Actions como condições esperadas, não como impossibilidades.

## 2. Fontes oficiais Godot

| Fonte | Aplicação em Apoena |
|---|---|
| [Otimização geral](https://docs.godotengine.org/pt-br/4.x/tutorials/performance/general_optimization.html) | Distinguir lentidão contínua, picos e carregamento; usar profiler e hipóteses mensuráveis |
| [Otimização 3D](https://docs.godotengine.org/pt-br/4.x/tutorials/performance/optimizing_3d_performance.html) | LOD, oclusão, distância de animação, iluminação e custo de geometria |
| [TileMaps](https://docs.godotengine.org/pt-br/4.x/tutorials/2d/using_tilemaps.html) | Usar TileMapLayer, quadrantes, colisão e ordenação por Y corretamente |
| [Classe TileMapLayer 4.6](https://docs.godotengine.org/en/4.6/classes/class_tilemaplayer.html) | Atualizações agrupadas e coordenadas serializadas limitadas a inteiros de 16 bits assinados |
| [Carregamento em segundo plano](https://docs.godotengine.org/pt-br/4.x/tutorials/io/background_loading.html) | ResourceLoader.load_threaded_request(), acompanhamento do progresso e recuperação quando pronto |
| [APIs seguras para threads](https://docs.godotengine.org/pt-br/4.x/tutorials/performance/thread_safe_apis.html) | Carregar recursos em thread e adicionar nós à cena ativa na thread principal |
| [Coordenadas de mundo grande](https://docs.godotengine.org/pt-br/4.x/tutorials/physics/large_world_coordinates.html) | Evitar double precision por padrão: raramente é necessária em 2D e aumenta memória/desempenho |
| [Otimização de navegação](https://docs.godotengine.org/pt-br/4.x/tutorials/navigation/navigation_optimizing_performance.html) | Não recalcular caminho todo quadro; simplificar malhas e distribuir consultas |
| [Esqueletos 2D](https://docs.godotengine.org/pt-br/4.x/tutorials/animation/2d_skeletons.html) | Pipeline de cutout 2D nativo, integrado ao motor |
| [Skeleton2D](https://docs.godotengine.org/pt-br/4.x/classes/class_skeleton2d.html) e [Bone2D](https://docs.godotengine.org/pt-br/4.x/classes/class_bone2d.html) | Hierarquia de ossos, poses de repouso e controle de nós 2D |
| [MultiMeshes](https://docs.godotengine.org/pt-br/4.x/tutorials/performance/using_multimesh.html) | Instanciar grande quantidade de objetos iguais; dividir por região porque o culling não é individual |
| [Formatos 3D](https://docs.godotengine.org/pt-br/4.x/tutorials/assets_pipeline/importing_3d_scenes/available_formats.html) | Preferir glTF 2.0/GLB; conhecer limitações de OBJ e requisitos de Blender |
| [Salvamento de jogos](https://docs.godotengine.org/pt-br/4.x/tutorials/io/saving_games.html) | Serializar estado explicitamente e validar o ciclo de salvar/carregar |

### Conclusões práticas

1. **Chunking não é simplesmente esconder tudo que está fora da tela.** É particionar dados, entidades e recursos em regiões com ciclo de vida definido.
2. **Threading não significa executar qualquer operação em qualquer thread.** Carregar em segundo plano e inserir na cena ativa são etapas distintas.
3. **TileMapLayer tem limites reais.** Coordenadas serializadas fora do intervalo assinado de 16 bits podem sofrer wrap; coordenadas locais por chunk são mais seguras.
4. **Navegação pode ser o gargalo mesmo quando renderização está boa.** Consultas de caminho repetidas e malhas excessivamente fragmentadas custam CPU.
5. **MultiMesh é ótimo para repetição, mas não resolve sozinho o mundo inteiro.** Dividir instâncias por setor mantém culling útil.
6. **Mundo aberto 2D não exige automaticamente large world coordinates.** Primeiro definir regiões, origem local e coordenadas lógicas.

## 3. Segurança e armazenamento

| Fonte | Aplicação |
|---|---|
| [GitHub — Secure use](https://docs.github.com/en/actions/reference/security/secure-use) | Runners próprios não são ambientes descartáveis; código não confiável pode comprometer o host |
| [GitHub — adicionar runners](https://docs.github.com/en/actions/how-tos/manage-runners/self-hosted-runners/add-runners) | Recomendação de uso cauteloso de runners próprios, especialmente para PRs |
| [GitHub — artefatos e retenção](https://docs.github.com/en/actions/tutorials/store-and-share-data) | Definir retention-days para cada artefato |
| [GitHub — remover artefatos](https://docs.github.com/en/actions/how-tos/manage-workflow-runs/remove-workflow-artifacts) | Recuperar armazenamento; exclusão é irreversível |
| [actions/upload-artifact](https://github.com/actions/upload-artifact/blob/main/README.md) | Retenção padrão, limites e cota compartilhada |
| [OWASP — prevenção de XSS](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html) | Construção segura de DOM, sanitização, CSP e Trusted Types |
| [OWASP — JavaScript/TypeScript Security](https://cheatsheetseries.owasp.org/cheatsheets/JavaScript_and_TypeScript_Security_Cheat_Sheet.html) | Não executar dados importados, tratar mensagens e erros, evitar sinks perigosos |
| [MDN — quotas de armazenamento](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) | navigator.storage.estimate(), QuotaExceededError, try/catch e recuperação |

### Conclusões práticas

- Um workflow de PR não deve executar código não confiável no computador pessoal que hospeda um Runner persistente.
- Artefatos de CI precisam de política de retenção explícita. Pacote de release e diagnóstico não devem ter o mesmo ciclo de vida.
- IndexedDB pode atingir quota; a aplicação precisa avisar, permitir backup e tratar a falha sem declarar salvamento concluído.
- Dados importados devem ser validados no ponto de entrada, não apenas na interface.
- LocalStorage e IndexedDB não são cofres de credenciais.
- postMessage exige validação de janela, origem/contexto, nonce, ação e payload. Origem opaca file:// exige desenho específico, não confiança genérica em qualquer origem null.

## 4. Fóruns e comunidades — evidência empírica

| Discussão | Observação útil | Limite |
|---|---|---|
| [Godot Forum — tilemap 500×500](https://forum.godotengine.org/t/how-to-manage-performance-of-very-large-tilemaps/73436) | Comunidade recomenda gerenciador de chunks e carregamento próximo ao jogador | Exemplo individual; tamanho ideal depende de benchmark |
| [Godot Forum — desempenho de tilemaps grandes](https://forum.godotengine.org/t/increase-performance-on-large-tilemap/71954) | Reforça particionamento em regiões e medição em hardware mais fraco | Não fornece arquitetura universal |
| [Godot Forum — streaming de mundos massivos](https://forum.godotengine.org/t/how-are-massive-open-world-games-actually-managed/136773) | Relato de abril de 2026 destaca que o streaming deve ser implementado pelo projeto e que memória/instanciação são gargalos | Discussão não substitui teste controlado |
| [Godot Forum — set_cell em mapas grandes](https://forum.godotengine.org/t/large-2d-tilemap-causes-4-5ms-lag-on-setcell-invocation/126593) | Mudanças em células podem criar picos de CPU; avaliar atualização em lote e chunking | Relato com mapa e hardware específicos |
| [Reddit r/godot — experiência com mundo aberto](https://www.reddit.com/r/godot/comments/1r4ru57/does_anyone_have_experience_with_open_world_game/) | Experiência comunitária reforça chunking e cuidado com origem/precisão | Opinião de usuários; não tratar como regra de engenharia |

**Como usar comunidade:** transformar relatos em hipóteses reproduzíveis. Não copiar números, plugins ou técnicas sem comparar com a versão Godot e o hardware de Apoena.

## 5. Experimentos técnicos recomendados

Antes de implementar streaming definitivo:

1. Criar um mapa de benchmark com áreas equivalentes e densidades distintas.
2. Medir um mapa único, chunks de tamanhos diferentes e carregamento sob demanda.
3. Medir tempo de geração, tempo de carregamento, memória residente, tempo de quadro e picos de CPU.
4. Repetir com colisão, navegação e Y-sort ligados/desligados para identificar custo de cada camada.
5. Testar com objetos estáticos, NPCs ativos, plantas e mudanças de estado.
6. Repetir em PC integrado e Android real.
7. Escolher o chunk com melhor compromisso, não o que vence apenas em um teste sintético.

Antes de implementar rig 2D completo:

1. Montar um personagem de teste com cabeça, tronco, braços, mãos, quadril e pernas.
2. Criar hierarquia de Bone2D.
3. Testar peças como Sprite2D e uma variante deformável com Polygon2D.
4. Testar pivôs, oclusão entre membros, inversão de direção e sobreposição.
5. Exportar um manifesto de rig e reimportar no Godot.
6. Comparar custo, qualidade e facilidade de edição com spritesheet tradicional.

## 6. Critério de atualização da pesquisa

Ao atualizar este documento:

- Registrar data e hora reais da nova consulta; se a hora não estiver disponível, declarar isso.
- Priorizar documentação da versão Godot usada pelo projeto.
- Registrar versão da engine e commit dos repositórios.
- Separar fato oficial, relato comunitário, hipótese e decisão do autor.
- Não manter link como fonte atual se ele apontar para documentação instável sem avisar.
- Adicionar novos recursos apenas quando eles mudarem uma decisão, reduzirem risco ou oferecerem um experimento concreto.
