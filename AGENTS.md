# AGENTS.md — ponto de entrada obrigatório para IAs

**Repositório:** `apoenalore/apoenaskil`  
**Projeto:** biblioteca de conhecimento, cânone e Skills do Universo Apoena  
**Solicitado em:** 2026-10-31T17:15:08Z  
**Regra central:** preservar antes de resumir, organizar ou atualizar.

Este arquivo é o ponto de entrada para qualquer IA, agente de programação ou assistente que abra este repositório. Não comece uma tarefa de extração, recuperação, organização ou atualização de conhecimento antes de seguir esta leitura.

## 1. Leitura obrigatória ao identificar o repositório

Leia nesta ordem:

1. `README.md` — visão geral e mapa do repositório.
2. `apoena/AGENTS.md` — regras de trabalho e catálogo das Skills.
3. `apoena/docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md` — modos e regras de preservação.
4. `apoena/docs/PROTOCOLO_UNIVERSAL_DE_EXTRACAO_E_TRANSFERENCIA.md` — obrigatório sempre que a tarefa envolver conversas, outras IAs, documentos, anexos ou recuperação de conhecimento.
5. `apoena/docs/source-and-status-legend.md` — proveniência, classificação e precedência.
6. `apoena/skills/INDEX.txt` — catálogo de Skills disponíveis.
7. `apoena/references/README.md` — fontes primárias, transcrições e limitações.
8. `apoena/docs/knowledge-gaps-and-contradictions.md` — lacunas e divergências já conhecidas.
9. Leia as Skills temáticas pertinentes à tarefa.

Se algum arquivo estiver ausente, inacessível ou ilegível, registre isso. Não finja que o leu.

## 2. Regra especial para extração de conversas e conhecimento

Quando o pedido envolver recuperar conhecimento de conversas antigas, de outra IA, de anexos ou de documentos:

- Ative o **MODO DE RECUPERAÇÃO INTEGRAL**.
- Siga todas as etapas do `apoena/docs/PROTOCOLO_UNIVERSAL_DE_EXTRACAO_E_TRANSFERENCIA.md`.
- Consulte a fonte original real, se ela estiver disponível. Não substitua a leitura da conversa por memória, resumo, Skill antiga ou contexto presumido.
- Leia a conversa em sequência, da primeira à última mensagem acessível, incluindo mensagens do usuário e da IA.
- Registre cobertura, mensagens examinadas, trechos inacessíveis, anexos e limites de acesso.
- Preserve o conteúdo original antes de produzir sínteses ou atualizar Skills.
- Não declare leitura integral ou recuperação completa sem evidência de cobertura integral.
- Se só houver resumo, memória ou contexto parcial, classifique a recuperação como parcial e identifique a fonte exata.

**Importante:** a conexão com este repositório GitHub não concede automaticamente acesso ao histórico privado de ChatGPT, Claude, Gemini, Grok, Copilot ou qualquer outra plataforma. A IA precisa ter acesso real à conversa, exportação ou arquivo fornecido. Se não tiver, deve parar nesse limite e pedir a fonte necessária.

## 3. Ordem de autoridade e preservação

- O criador do Universo Apoena é a autoridade final sobre o cânone.
- Correções explícitas do criador prevalecem para o estado atual dentro do escopo indicado, mas não apagam o registro histórico anterior.
- Fonte primária e transcrição devem ser distinguidas de resumo, memória e interpretação.
- Propostas de IA nunca se tornam decisões do criador sem aprovação explícita.
- Contradições devem ser documentadas, não resolvidas por suposição.
- Não excluir, sobrescrever ou fundir versões históricas de forma destrutiva.
- Não confundir cânone do mangá, sistemas de jogo, protótipos, ferramentas e infraestrutura.

## 4. Atualização do repositório

Antes de gravar qualquer material:

1. Faça inventário dos arquivos e da branch atual.
2. Identifique o que já existe e evite duplicações sem perder proveniência.
3. Preserve a fonte bruta ou o registro de recuperação detalhado.
4. Só depois atualize documentos temáticos e Skills.
5. Atualize índices e referências afetados.
6. Confira links, nomes, datas, status e caminhos.
7. Registre arquivos alterados, motivo, fonte, commit e resultado da validação.

Prefira branch de trabalho e Pull Request para alterações documentais relevantes. Não apague conteúdo histórico. Não afirme que anexos binários foram preservados quando apenas o texto foi transcrito.

## 5. Critério de conclusão

Uma tarefa de extração só pode ser marcada como **COMPLETA** quando:

- a fonte original foi acessada e lida integralmente;
- a cobertura está demonstrada;
- anexos foram inspecionados ou listados como pendentes;
- o registro detalhado preserva a proveniência;
- as informações foram classificadas sem misturar decisão, proposta e interpretação;
- lacunas e contradições estão explícitas;
- índices e referências foram atualizados e validados.

Caso contrário, use **PARCIAL**, **NÃO VERIFICADA** ou **BLOQUEADA**, explicando exatamente o motivo.

**Princípio permanente: nenhuma IA pode sacrificar a história do Apoena para produzir uma Skill mais curta ou aparentemente mais organizada.**

## Continuidade de gameplay — chefes, níveis e missões

Para tarefas sobre chefes, progressão ou missões no Creator ou no Pixel Art, leia também, nesta ordem:

1. `apoena/docs/Game Play/LEIA_PRIMEIRO_AGENTES.md` — ordem de leitura, limites da análise e instruções de continuidade.
2. `apoena/docs/Game Play/Plano_Apoena_Bosses_Niveis_Missoes.md` — análise completa, fontes, cobertura, diagnóstico, propostas e validação.
3. `apoena/docs/Game Play/REGISTRO_DECISOES.md` — evidências, justificativas e questões em aberto.

O material é uma proposta para protótipo. Não trate números experimentais como cânone aprovado nem como implementação já realizada. Siga as instruções gerais deste repositório e atualize as referências apenas de forma aditiva.
