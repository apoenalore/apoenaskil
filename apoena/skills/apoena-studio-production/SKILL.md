---
name: apoena-studio-production
description: Orienta agentes na produção visual e editorial do mangá Apoena usando o Apoena Studio Maker, preservando referências, versões e separação entre mangá e jogo.
---

# Skill — Produção editorial e visual no Apoena Studio Maker

## Objetivo
Apoiar a produção do mangá e de materiais visuais do Universo Apoena sem confundir ferramentas de autoria com o cânone ou com o runtime do jogo.

## Fontes e escopo
- Repositório de autoria consultado: `apoenalore/projeto-apoena-studio-maker-ia`.
- README descreve o Apoena Studio como ateliê web com cadastros de personagens/cenários, referências versionadas, criação de cenas, editor de mangá e editor de cena 2D.
- O arquivo `docs/SEPARACAO_MANGA_E_JOGO.md` determina que o Studio Maker é o local do projeto de mangá; código Godot, combate, inventário de partida e IA de inimigos pertencem ao repositório do jogo.
- Esta Skill documenta capacidades descritas no README e não substitui a verificação do código/versão instalada.

## Regras obrigatórias
1. Antes de gerar uma cena, selecionar a ficha aprovada do personagem e do cenário e anexar as referências oficiais pertinentes.
2. Não cadastrar automaticamente uma imagem enviada em conversa como cânone. O autor deve enviá-la e aprovar sua versão.
3. Preservar originais e versões anteriores. Não sobrescrever fichas, imagens ou projetos editáveis com placeholders.
4. Ao corrigir uma imagem, distinguir o resultado anterior das referências originais; manter o snapshot de fichas usado na geração quando a ferramenta assim o registrar.
5. Não alegar que uma ferramenta produz 3D real quando opera sobre imagem 2D. O esqueleto de 15 articulações descrito no editor de cena é aproximado; deformação 2D não reconstrói partes ocultas nem inventa vistas traseiras.
6. Para spritesheets, respeitar grade, quantidade de quadros, âncora, espaçamento, proporções e transparência alfa real conforme pedido. Conferir visualmente cada quadro e exportação.
7. Em remoção de fundo, preservar os elementos de primeiro plano sem redesenho; verificar halos, bordas e regiões semitransparentes.
8. Manter a linguagem visual do mangá separada da estética do gameplay 3D. O jogo pode usar modelos 3D estilizados, mas isso não redefine a arte da obra.
9. Não expor chaves de API, senhas ou arquivos locais de segredo. O README informa que a geração por API depende de credenciais e créditos; assinatura do ChatGPT não substitui créditos de API.
10. Instruções de trabalho para o criador devem ser curtas, sequenciais e em português quando aplicável.

## Capacidades descritas no repositório consultado
- Cadastro/versionamento de personagens e cenários.
- Geração e correção de ilustrações por API, sujeita a credenciais.
- Editor manual de mangá com páginas longas, quadros, balões, efeitos, camadas e exportação PNG.
- Editor de cena 2D com importação de personagens, esqueleto aproximado, deformação de malha, camadas e exportação.
- Ferramentas de pose e continuidade visual.

## Limitações documentadas
- Remoção de fundo branco é baseada em regiões quase brancas conectadas às bordas e pode falhar com fundos irregulares ou roupas brancas junto ao fundo.
- Esqueleto aproximado não é detecção neural; deformação pode esticar ou gerar artefatos.
- Giro do esqueleto é uma projeção orientativa; não converte a imagem em modelo 3D nem cria detalhes inexistentes.
- Exportação e edição devem ser testadas na versão atual; README e código podem mudar.

## Relações com outras Skills
- `apoena-art-director`: direção visual e estilo.
- `apoena-image-production`: prompts, geração e tratamento de imagem.
- `apoena-visual-continuity`: consistência entre vistas, quadros e assets.
- `apoena-character-canon`: fichas e atributos aprovados.
- `apoena-canon-guardian`: impedir que propostas visuais virem cânone sem aprovação.

## Proveniência e status
**RECUPERADO — VALIDAR** a partir do README e da documentação do Studio Maker consultados em 2026-10-31. Capacidades de produto descritas no README não significam que todo fluxo esteja validado em todos os dispositivos. A separação Studio/jogo consta em documento próprio do repositório.

## Registro
- data_hora_do_registro: 2026-10-31T08:47:00-03:00
- fonte: `apoenalore/projeto-apoena-studio-maker-ia/README.md` e `docs/SEPARACAO_MANGA_E_JOGO.md`
- data_hora_do_evento: não aplicável (síntese documental)
