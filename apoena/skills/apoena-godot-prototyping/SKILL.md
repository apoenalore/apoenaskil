---
name: apoena-godot-prototyping
description: Orienta prototipagem e transferência de ideias do teste HTML para o projeto Godot Apoena, sem confundir prova rápida com entrega final.
---
# Skill — Prototipagem HTML e produção Godot

## Decisão explícita do autor
HTML serve para **testar rapidamente no celular**. O jogo pronto deve seguir para **Godot**. Preserve essa separação ao sugerir arquitetura, organizar tarefas ou documentar entregas.

## Regras de trabalho
- O HTML pode servir como protótipo rápido de interação e validação de ideia; não o trate como entrega final do jogo.
- A versão Godot é o destino de produção. Antes de declarar paridade, testar cada implementação: HTML e Godot podem ter código, saves e comportamento separados.
- Não afirme que um APK foi produzido ou validado sem evidência de exportação e teste em dispositivo.
- O protótipo Pixel Art documenta câmera 2.5D inicial: câmera 2D elevada, acompanhamento do personagem, zoom e ordenação por Y. Isso não é uma câmera 3D 360° nem isometria completa.
- O autor levantou preocupação sobre mapas muito grandes no Godot. Não há, no registro recuperado, decisão de arquitetura de mundo gigantesco. Técnicas como regiões, chunks, carregamento sob demanda e limites de simulação devem ser apresentadas como opções a avaliar, não como arquitetura aprovada.
- Separar o jogo Pixel Art do projeto Godot 3D `JOGO-APOENA-AGAR-`, do GameCreator e do Studio Maker.
- Manter ativos, fontes e dados no repositório proprietário correto; evitar copiar código de ferramenta de autoria para o runtime.

## Checklist de transferência de protótipo
1. Descrever o comportamento que o HTML comprovou e o que não comprovou.
2. Identificar dados, estados e regras que devem migrar.
3. Reimplementar no Godot de forma compatível com a arquitetura existente, sem presumir conversão automática de HTML para Godot.
4. Comparar o comportamento e registrar diferenças.
5. Executar testes automatizados disponíveis e, quando relevante, teste manual em aparelho.
6. Registrar limitações e deixar pendências visíveis.

## Referências
- `docs/game-design-notes.md`
- Repositório `apoenalore/Apoena-pixel-art-html`, especialmente `docs/ORGANIZACAO.md` e `docs/ECOSSISTEMA.md`.
- Repositório `apoenalore/JOGO-APOENA-AGAR-`, somente quando a tarefa for desse projeto.
