# Registro conversacional — GameCreator, Apoena e arquitetura low-end

**Data da conversa:** 2026-11-01 (continuação até 2026-11-02 UTC).  
**Projeto relacionado:** GameCreator / universo Apoena.  
**Destino deste registro:** biblioteca de conhecimento e Skills `apoenalore/apoenaskil`, na branch `knowledge-transfer/apoena-canon-v1-rebased` (PR #2).  
**Natureza:** memória de produto, decisões de engenharia e ideias em discussão. **Não é cânone narrativo** e não comprova funcionalidades implementadas.

## 1. Contexto da PR #11 do GameCreator

O autor pediu resolver a falha de validação da PR #11 do repositório `apoenalore/GameCreator`.

- PR: [#11 — GC-ANIM-006: abrir e editar animações de Apoena no Estúdio](https://github.com/apoenalore/GameCreator/pull/11).
- Branch: `feat/apoena-personagem-estudio-main`.
- Commit consultado: `a9c7148f01504f7be142dd0d852056dd5a9a5114`.
- A PR estava aberta, em Draft e marcada como mergeable na consulta realizada.
- Escopo descrito na PR: carregar referências de corrida multidirecional e ataques laterais do Apoena no Estúdio Pixel Art, separar quadros em grades iniciais, preencher ação/direção, permitir pré-visualização e edição quadro a quadro, preservar PNGs originais e exportar.
- A prévia chamada “andar” reutiliza poses de corrida e precisa permanecer explicitamente identificada como preliminar; caminhada fiel requer quadros próprios.
- As grades dos ataques são aproximações iniciais: efeitos podem atravessar células e exigem inspeção e ajuste manual.
- A PR não declara integração de gameplay com Godot.

### Evidências e limite do diagnóstico

- A execução consultada do workflow `.github/workflows/pixel-art.yml` foi a run [#41357977741](https://github.com/apoenalore/GameCreator/actions/runs/41357977741), inicialmente com conclusão `failure`.
- O job era `validar`. A tentativa anterior identificada estava cancelada.
- Os logs detalhados da execução que falhou não estavam disponíveis no momento da investigação; a consulta aos logs retornou ausência do artefato/blob e não foi possível identificar qual etapa ou comando originou a falha.
- Foi solicitado rerun dos jobs com falha. A nova tentativa apareceu como `queued` e depois `in_progress`; a última consulta ainda não mostrava conclusão.
- Não foi realizada alteração de código nem merge durante essa investigação.
- Portanto, a causa da falha **permanece não diagnosticada**. Não registrar hipótese como causa confirmada. Próximo passo: obter conclusão e logs da nova execução; se a CI falhar novamente, baixar/analisar o artefato de diagnóstico `v41-ci-diagnostics` quando disponível e identificar a etapa exata antes de editar arquivos.
- A CI inclui validações PowerShell/runner Windows, build do Creator, smoke test de DOM em navegador, sintaxe JavaScript, testes de biblioteca/backup/catálogo/ponte, contratos de integração e teste de runtime Godot 4. Uma falha em qualquer etapa pode reprovar o job; isso é descrição do workflow, não evidência de qual etapa falhou.

## 2. Tecnologias explicadas ao autor

O GameCreator e o fluxo do jogo utilizam tecnologias diferentes, cada uma com responsabilidade própria:

- **HTML:** estrutura de telas, painéis, botões, formulários e elemento Canvas do Estúdio/protótipo.
- **CSS:** aparência, layout, responsividade e apresentação pixelada.
- **JavaScript:** lógica interativa do editor, recorte de sprites, animação de prévia, eventos, manipulação de Canvas e integração web.
- **GDScript/Godot 4:** lógica executada no motor do jogo, incluindo gameplay, movimentação, colisões, inimigos e regras, conforme o contrato de integração a ser definido.
- **JSON:** formato de dados/metadados para descrever personagens, ações, direções, quadros, peças e configurações.
- **PowerShell:** automação e etapas de validação no runner Windows/GitHub Actions.

Exemplo didático apresentado, não código já integrado ao jogo:

```html
<canvas id="jogo"></canvas>
```

```javascript
let velocidade = 3;

function andar(personagem) {
  personagem.x += velocidade;
}
```

```css
canvas {
  image-rendering: pixelated;
}
```

Princípio de arquitetura: definir fronteiras e contratos claros. Não duplicar a mesma responsabilidade no editor HTML e no runtime Godot. O Creator edita/prepara/exporta recursos; o runtime executa as regras reais do jogo. Exportar PNG/JSON, por si só, não comprova integração.

## 3. Diretriz proposta: Low-End First

O autor quer que o jogo seja leve e alcance a maior variedade possível de celulares, inclusive aparelhos básicos. A referência de design e engenharia são jogos antigos e plataformas limitadas como Game Boy, aprendendo com suas técnicas sem copiar literalmente suas limitações.

**Diretriz proposta, ainda a formalizar e validar:** desenvolver e testar primeiro em condições de aparelhos de entrada (*low-end first*), em vez de assumir hardware moderno como padrão.

Princípios discutidos:
- reutilizar tiles, sprites, texturas e recursos;
- controlar quantidade de objetos ativos e chamadas de desenho;
- reduzir cálculos desnecessários por quadro;
- manter colisões e simulações tão simples quanto possível sem comprometer o gameplay;
- usar spritesheets e animações por quadros;
- controlar paletas e dimensões dos assets;
- organizar cenários em camadas;
- carregar e descarregar recursos conforme a região do mapa;
- oferecer resolução interna e qualidade gráfica escaláveis;
- reduzir uso de memória, bateria e aquecimento;
- preservar nitidez da pixel art com amostragem apropriada (*nearest-neighbor*), evitando interpolação borrada.

Foram citadas como **metas preliminares para testes, não garantias de desempenho**: 30 FPS como referência mínima em aparelhos de entrada e 60 FPS em aparelhos compatíveis. Essas metas precisam ser confirmadas com testes em dispositivos reais, orçamento de memória, resolução e cenas representativas.

A inspiração Game Boy inclui tiles pequenos (por exemplo, 8×8 ou 16×16, a escolher), reutilização de assets, paleta controlada e spritesheets. A escolha de dimensões, limites e formatos deve ser testada no jogo real, não assumida como padrão definitivo.

## 4. Ideia visual: árvores com billboard ou sprites direcionais

O autor observou em jogos antigos árvores que mudam sua orientação/apresentação conforme a direção de observação do personagem, criando impressão de volume tridimensional com imagens 2D.

Foram discutidas duas técnicas:

### 4.1 Billboard

Uma imagem 2D de árvore posicionada no mundo e orientada para a câmera (ou apresentada de modo a manter a face voltada para a câmera). Pode simular vegetação volumétrica com custo inferior ao de uma árvore modelada em 3D. É apropriada quando a câmera e a perspectiva permitem, mas pode revelar aparência plana em ângulos inadequados.

### 4.2 Sprites direcionais / impostores em múltiplas vistas

Criar versões da mesma árvore para direções ou ângulos distintos (por exemplo, frente, trás, esquerda e direita; ou mais vistas se necessário). O sistema seleciona a imagem adequada conforme câmera/personagem. Isso dá mais controle sobre silhueta e volume aparente, mas aumenta o número de assets e exige transições consistentes.

**Intenção do autor:** aplicar a técnica a algumas árvores, não generalizá-la para casas ou morros. Casas, montanhas e terreno precisam de representação espacial apropriada à sua geometria e à perspectiva do jogo. A técnica específica para árvores ainda é uma proposta, não decisão final de implementação.

Recomendação registrada para avaliação: experimentar primeiro com uma árvore de referência em uma cena de teste, comparar billboard e sprites direcionais, medir memória, draw calls, legibilidade e artefatos em movimento, e só então escolher a técnica por categoria de vegetação.

## 5. Decisão de perspectiva pendente

Foi solicitado ao autor escolher entre três perspectivas:
1. Top-down (visão de cima).
2. Isométrica / 2.5D.
3. Lateral (*side-scroller*).

Também foi perguntada a prioridade:
- aparelhos muito básicos, aceitando reduzir efeitos;
- aparelhos básicos e intermediários, equilibrando qualidade e desempenho;
- maior qualidade visual, com opção de reduzir gráficos.

**Nenhuma resposta de escolha foi registrada neste diálogo.** Não assumir perspectiva nem prioridade como aprovadas. Essas decisões afetam câmera, orientação das árvores, profundidade, colisões, composição de cenário e orçamento de renderização.

## 6. Método de colaboração e governança técnica

O autor quer compreender a linguagem e a lógica do código para poder contribuir com ideias, referências e decisões. O fluxo de trabalho proposto foi:
1. autor apresenta uma ideia ou referência;
2. explicar a técnica e suas alternativas;
3. avaliar custo de processamento, memória e impacto visual;
4. definir escopo e contrato técnico;
5. implementar em branch;
6. testar no editor e no runtime alvo;
7. registrar decisão, evidência e pendências no repositório.

Manter distinção explícita entre:
- ideia discutida;
- requisito confirmado pelo autor;
- decisão aprovada;
- implementação existente;
- implementação testada;
- integração comprovada no jogo.

Não declarar recurso concluído apenas porque existe interface, arquivo, spritesheet, manifesto ou PR aberta. Preservar assets originais e obter autorização antes de mudanças destrutivas ou integração na branch principal.

## 7. Próximas ações sugeridas

1. Acompanhar a run #41357977741 e obter o resultado final/logs da nova tentativa.
2. Diagnosticar a etapa e o comando exatos da falha antes de modificar o código da PR #11.
3. Validar os imports das três referências do Apoena, os recortes, ações/direções, prévia, salvamento e exportação, sem alterar os PNGs originais.
4. Obter do autor a escolha de perspectiva e prioridade de dispositivos.
5. Criar uma cena-prova de baixo custo com uma árvore e comparar billboard com sprites direcionais.
6. Definir métricas e aparelhos reais de teste para desempenho, memória e legibilidade.
7. Manter a PR #11 em Draft até validação; não fazer merge por inferência.

## 8. Relação com registros anteriores

Este registro complementa `apoena/docs/conversation-records/2026-11-01-gamecreator-integration.md` e a Skill `apoena/skills/apoena-game-development/SKILL.md`. Não substitui nem reescreve esses registros. Ele documenta a conversa de 2026-11-01/02 e preserva os pontos ainda abertos.

---
**Nota de proveniência:** este documento sintetiza a conversa disponível no ChatGPT e consultas ao GitHub realizadas durante ela. Não representa auditoria integral de todas as conversas históricas nem substitui a verificação do estado atual dos repositórios.
