---
name: apoena-progression-economy
description: Organiza profissões, progressão, NPCs persistentes e economia planejada de Apoena sem impor classes rígidas ou afirmar sistemas não implementados.
---
# Skill — Progressão, profissões e economia Apoena

## Fontes e status
Use `../../docs/game-design-recovered.md`, `../../docs/repository-map.md` e a documentação do jogo específico. O material de progressão/economia recuperado é **plano de arquitetura e desenvolvimento**, não prova de implementação e não altera automaticamente o cânone do mangá.

## Conceitos registrados no plano
- **Exploração Livre:** o jogador cria identidade própria e escolhe o que deseja se tornar; exemplos citados: ferreiro, aventureiro, mago, agricultor, comerciante ou combinações. O percurso não deve exigir jogar como Apoena nem seguir o Modo História.
- **Modo História:** plano inicial citado começa na cidade capital onde Apoena estuda, segue para a Tribo da Água para encontrar os pais, inclui uma prova cujo fracasso faz parte da narrativa e abre caminho de aventureiro (caça, coleta de remédios, monstros e defesa da muralha). Tratar como planejamento até conferir a Bíblia e a aprovação autoral.
- **Três camadas de progressão:** (1) personagem — competências, habilidades, Aurium, constelações, equipamentos e especializações; (2) mundo — casa, horta, guilda, companheiros, relações, economia, recursos e regiões; (3) menu permanente — desbloqueios de estruturas/opções como laboratório, ferreiro, arena, melhorias e fabricação.
- **MOBA:** o plano cita progressão temporária de partida nível 0–20 e possível conversão de parte da experiência em progressão permanente do menu. Taxa não definida; níveis da partida e progressão permanente são dados distintos.
- **NPCs persistentes (planejados):** identidade, profissão, objetivos, inventário, rotinas e relações; podem produzir, comprar, vender, viajar e reagir à ausência do jogador.
- **Economia (planejada):** estoque, oferta, demanda, produção, consumo, preços e disponibilidade. Exemplo registrado: mercado pode deixar de comprar espadas quando outro ferreiro já abasteceu o estoque.
- Agar é indicada como região inicial planejada; Pandora amplia a exploração. O retorno do jogador deveria revelar mudanças persistentes conforme o tempo de mundo.

## Regras para agentes
1. Não impor classes rígidas que bloqueiem combinações de profissão ou competências.
2. Diferenciar profissão, classe de combate, especialização, competência e escolha narrativa.
3. Quando criar uma economia, mostrar quais variáveis e ciclos são definidos e quais são propostas.
4. Não inventar salários, moedas, preços, taxas de conversão, rotinas, produção ou progressão quantitativa sem fonte.
5. Separar progressão de personagem, mundo e menu permanente; não misturar seus saves sem especificação.
6. Não declarar NPCs autônomos, economia simulada, mundo persistente ou profissões implementados só porque constam no plano.
7. Se uma proposta mudar oportunidades, relações ou história, explicar efeitos e solicitar aprovação do autor quando afetar o cânone.
8. Registrar requisitos ainda pendentes em vez de completá-los por inferência.

## Relações
- Sistemas gerais: `apoena-game-systems`.
- Cânone: `apoena-canon-guardian`.
- Fonte de recuperação: `../../docs/game-design-recovered.md`.
