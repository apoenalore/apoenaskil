# Auditoria de fontes e repositórios Apoena

- **data_hora_do_registro:** 2026-10-31T08:47:00-03:00
- **Escopo:** inspeção documental e estrutural de repositórios GitHub relacionados a Apoena.
- **Status:** RECUPERADO — VALIDAR; não equivale a auditoria integral de código nem a cópia de todos os assets.

## Repositório central de Skills
- `apoenalore/apoenaskil` — biblioteca de conhecimento. Branch consultada: `main`.
- Estrutura encontrada: `apoena/AGENTS.md`, `canon/`, `decisions/`, `docs/`, `skills/`.
- A estrutura anterior foi preservada; esta auditoria adiciona documentação de proveniência e uma Skill de produção editorial.

## Fontes relacionadas consultadas

### `apoenalore/projeto-apoena-studio-maker-ia`
- Responsabilidade: Apoena Studio Maker e produção do mangá.
- README descreve fichas/versionamento de personagens e cenários, geração/correção de imagens, editor de mangá, editor de cena 2D e ferramentas de pose.
- `docs/SEPARACAO_MANGA_E_JOGO.md` estabelece que arquivos e funcionalidades exclusivos do mangá ficam no Studio; código Godot e sistemas de jogo ficam no repositório do jogo.
- Limitações importantes: esqueleto de cena 2D aproximado, deformação de malha não reconstrói partes ocultas, giro de esqueleto não cria vistas reais. Remoção de fundo branco pode falhar em fundos irregulares/roupas brancas.
- A imagem de fortaleza mencionada no README não foi cadastrada automaticamente como cânone; imagens só viram referência oficial após envio/aprovação do autor.

### `apoenalore/Apoena-pixel-art-html`
- Contém runtime HTML/Godot, cenas, scripts, ecossistema, clima e documentação; auditoria do próprio repositório registra que o snapshot não comprova um editor independente de pixel art com canvas/pincéis/camadas.
- `docs/PROTOCOLO_TRABALHO_SEQUENCIAL.md` exige uma tarefa ativa por vez, critérios de aceitação, testes, validação canônica no runner correto, conferência do diff e commit/registro antes de iniciar a próxima tarefa.
- `docs/AUDITORIA_TECNICA_ESTRATEGICA_2026-10-30.md` lista pendências de escopo, persistência e paridade HTML/Godot; a auditoria não executou testes nem confirmou correções.
- Decisão do autor registrada em DEC-0001 na base: HTML é para testes rápidos no celular; entrega final do jogo deve seguir para Godot.

### `apoenalore/JOGO-APOENA-AGAR-`
- README descreve projeto Godot 4 com Floresta Viva, Arena MOBA 3D offline contra IA e Modo História alfa.
- README declara pendentes: caverna interna/dragão lutável, mundo aberto contínuo, geografia canônica completa, NPCs definitivos, narrativas finais e multiplayer online.
- Modelos/efeitos/animações do gameplay são provisórios e não redefinem o cânone visual do mangá.
- README reprova o retargeting de Volibear para CH44; o GLB defeituoso não foi integrado. Não reintroduzir.
- Há modelos GLB e assets no próprio repositório e há branch de arquivo citada para fontes FBX; a auditoria não baixou nem duplicou binários.

### `apoenalore/GameCreator`
- Ferramenta de autoria separada do runtime. Foram encontrados README, plano geral, requisitos, recuperação V4.0, integração Godot e bundles do editor.
- Documentação descreve catálogo de assets, spritesheets, mapas/tilesets, objetos, dados e contratos exportáveis.
- Requisitos e planos não provam que cada funcionalidade esteja concluída ou integrada no runtime. Validar implementação, testes e versão antes de marcar como implementado.
- Preservar distinção entre editor, exportação de dados e execução pelo jogo.

### `apoenalore/que-projeto-e-esse`
- Lore Engine: editor 3D independente em protótipo. Não confundir com Studio Maker, GameCreator ou runtime Godot.
- README e docs descrevem geração humanoide procedural experimental e exportação GLB; não é fonte automática do cânone.

### `apoenalore/APOENA-AI-HUB-IA`
- Repositório de uma Central Multi-IA genérica para conexões, memória, coordenação, contexto exportável e failover autorizado.
- É um projeto de infraestrutura de IA separado; não deve ser confundido com o universo ficcional, Studio Maker, GameCreator ou jogo Apoena.

## Fontes originais ainda não recuperadas / atualização de status
A seção inicial desta auditoria foi escrita antes da leitura dos PDFs e foi superada pela atualização documental de 2026-10-31. O estado correto é:
- `Sistema de Poderes Apoena Atual.pdf`: 62 páginas transcritas integralmente em texto.
- `Sistema de Poderes Apoena.pdf`: 25 páginas transcritas integralmente como versão histórica.
- `Apoena a Origem do Universo (5).pdf`: 90 páginas transcritas; página 90 com OCR fragmentado, exige conferência visual.
- Segunda cópia `Apoena a Origem do Universo (5)(1).pdf`: não comparada.
- Anexo `Texto colado.txt` da conversa “Aurium Constelações Poderes”.
- As 16 referências PDF mencionadas pelo autor em conversa anterior.
- Fichas originais completas, mapas oficiais aprovados, cronologia integral e bíblia visual.
- Binários não copiados para o repositório: PNG/JPG/WEBP originais, spritesheets, GLB/FBX, ZIPs e arquivos de conversa. Dois mapas candidatos foram inspecionados e catalogados em `references/visual-assets-in-library.md`; seus originais continuam na Biblioteca.

## Regras de preservação
1. Não mover código/arquivos entre repositórios por conveniência.
2. Para material exclusivo do mangá, seguir a separação oficial e preservar originais no Studio Maker.
3. Para assets de jogo, manter o repositório/branch de origem e registrar caminho, commit e licença/proveniência quando conhecidos.
4. Não declarar que um arquivo binário foi preservado nesta biblioteca sem cópia verificada.
5. Não transformar protótipo, plano, README histórico ou requisito em cânone narrativo.
6. Uma futura recuperação de PDF/anexo deve registrar nome exato, versão, página/trecho e status de aprovação.

## Inventário de Skills
A biblioteca já continha Skills de cânone, worldbuilding, Aurium, constelações, continuidade, roteiro, personagens, Agar, direção visual, imagem, jogo, ecologia, progressão/economia, Godot, arquitetura e arquivista. Foi acrescentada `apoena-studio-production` para cobrir o pipeline editorial do Studio Maker.

## Limite desta auditoria
A estrutura Git foi inspecionada e documentos textuais selecionados foram lidos. Não houve leitura integral de todo o código, revisão de todos os commits/branches, download de binários, leitura dos PDFs primários nem inspeção integral de todas as conversas históricas.


## Correção posterior de proveniência
**data_hora_do_registro:** 2026-10-31T08:47:00-03:00

A inspeção da Biblioteca encontrou os três PDFs principais e gerou transcrições textuais com marcadores de página. Ver `references/README.md`, `docs/cosmology-source-notes.md` e `docs/aurium-system.md`. Essa atualização corrige a afirmação anterior de que os PDFs não haviam sido lidos integralmente. As limitações de OCR e de preservação binária permanecem.
