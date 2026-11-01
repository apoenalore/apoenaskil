# Continuidade — chefes, níveis e missões

Data: 2026-11-01. Status: proposta para protótipo; publicação e implementação não confirmadas.

## Ordem de leitura

1. Leia as instruções vigentes do repositório (`AGENTS.md`, se existir, e README), sem substituir regras existentes por este documento.
2. Leia `apoena/docs/knowledge-gaps-and-contradictions.md` para distinguir cânone, lacunas e propostas.
3. Leia `apoena/skills/apoena-aurium-system/SKILL.md`, preservando reservas individuais e fases de domínio.
4. Leia `apoena/skills/apoena-progression-economy/SKILL.md` e a skill vigente de sistemas de jogo, localizando-a no índice atual sem presumir seu caminho.
5. Leia integralmente [o plano](Plano_Apoena_Bosses_Niveis_Missoes.md), especialmente fontes/cobertura, diagnóstico, regras e validação.
6. Leia [o registro de decisões](REGISTRO_DECISOES.md).
7. Confira o estado atual de `GameCreator` e `Apoena-pixel-art-html` antes de implementar. Compare os HEADs com os commits registrados no plano e revalide os achados afetados por mudanças.

## Como continuar

- O pedido do usuário autoriza registrar a análise e organizar sua continuidade no apoenaskil. Não confundir isso com implementação já realizada ou aprovação definitiva de números/cânone.
- Trabalhe em uma fatia: combate solo → primeiro chefe → níveis 1–5 e cadeia de preparação → autoria no Creator → integração → expansão/coop.
- A versão inicial deve demonstrar chefe vencível com recursos obtidos antes do encontro, avisos claros, esquiva alcançável e janelas para atacar.
- Registre separadamente fato verificado, hipótese e decisão do autor. Faixas, XP, HP e multiplicadores do plano são parâmetros experimentais.
- Não trate ausência em busca indexada como prova de ausência no código. A cobertura incompleta do Creator permanece explicitada no plano.
- Ao concluir uma etapa, registre commit analisado, arquivos alterados, testes executados, resultado, limitações e próxima etapa. Atualize este status apenas após publicação verificada.

## Texto enviado ao usuário

> Analisei as regras do `apoenaskil` e os módulos relevantes do Creator e do Pixel Art. **O principal achado: ainda não existe um boss lutável no Pixel Art examinado.** Precisamos construir e medir o primeiro encontro para balanceá-lo.
>
> Minha proposta:
>
> - **Chefes:** ataques com aviso claro, possibilidade real de esquiva e pausa para contra-atacar. Primeiro boss com três ataques, duas fases e duração inicial de 60–90 segundos.
> - **Níveis:** progressão permanente de aventura, separada das profissões e do domínio elemental. MOBA mantém níveis temporários de 0–20.
> - **Missões:** acompanhar nível, equipamentos, competências e história. Ensinar uma mecânica antes de exigi-la no chefe.
> - **Primeira entrega:** um boss, níveis 1–5 e uma sequência de missões de preparação. Expandir após testar dificuldade e ritmo.
>
> Também encontrei uma assimetria no combate atual: o herói alcança **235 unidades**, enquanto as torres atacam até **155**. Isso precisa entrar na revisão de alcance.
>
> O plano completo inclui fórmulas propostas, recompensas, cooperação, integração com o Creator e critérios de teste.
>
> Não alterei os repositórios. A análise não cobre integralmente os grandes HTMLs e bundles do Creator; essa limitação está registrada no documento.

O arquivo completo correspondente está nesta mesma pasta; a referência transitória da conversa foi substituída pelo link relativo acima.
