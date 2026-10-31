---
name: apoena-knowledge-archivist
description: Recupera, cataloga e transfere conhecimento Apoena com proveniência, status explícito, timestamps e preservação de lacunas.
---
# Skill — Arquivista de conhecimento Apoena

## Objetivo
Preservar informação encontrada em conversas, documentos, assets e repositórios sem completar lacunas por imaginação. A IA é assistente do autor; não decide o cânone.

## Processo de recuperação
1. Consulte `apoena/AGENTS.md`, `README.md` e `docs/knowledge-recovery-2026-10-30.md`.
2. Localize a fonte primária (documento aprovado, mensagem explícita do autor, arquivo do projeto). Não use um resumo como se fosse o documento integral.
3. Registre a proveniência: título/caminho, versão ou commit, data conhecida e seção/página quando disponível.
4. **Sempre registre data e hora** de criação/atualização do registro, descoberta, decisão ou evento, usando ISO 8601 com fuso horário quando o dado for confiável (ex.: `2026-10-31T02:55:00-03:00`).
5. Separe `data_hora_do_evento` de `data_hora_do_registro` quando ambas forem conhecidas. Não atribua a uma conversa antiga a data em que ela foi importada.
6. **Nunca invente horário, data ou fuso.** Se a fonte só trouxer a data, escreva `Hora não disponível na fonte`. Se não trouxer nenhum dos dois, escreva `Data e hora não disponíveis na fonte`. Se o ambiente não fornecer relógio/fuso confiável, declare essa limitação.
7. Classifique cada informação:
   - **CÂNONE CONFIRMADO** — fonte autoral aprovada ou material identificado como cânone.
   - **DECISÃO DO AUTOR** — decisão explícita, incluindo decisões técnicas/editoriais.
   - **EM DESENVOLVIMENTO** — ideia mencionada sem fechamento.
   - **PROPOSTA DA IA** — sugestão ainda sem aprovação.
   - **DESCONHECIDO/PENDENTE** — a fonte está ausente, incompleta ou não permite concluir.
8. Preserve também ideias descartadas e razões, quando houver fonte; não as recicle como recomendação sem avisar.
9. Em conflito, mantenha as versões e peça decisão. Uma versão mais recente só substitui a anterior quando isso estiver explícito.
10. Atualize o inventário e o índice da Skill; não esconda lacunas.
11. Nunca afirme “tudo recuperado” enquanto fontes ou conversas relevantes estiverem inacessíveis.

## Estrutura recomendada de cada registro
- O que foi recuperado.
- Status.
- Fonte/proveniência.
- Data/hora do evento ou conversa (ou declaração explícita de indisponibilidade).
- Data/hora de registro/atualização (ou declaração explícita de indisponibilidade).
- Relações com outras partes do universo.
- Decisões e histórico.
- Lacunas e perguntas para o autor.

## Controle de qualidade
Antes de publicar:
- Confira nomes próprios e grafias.
- Separe mangá/lore, jogo, protótipo visual e arquitetura.
- Não derive personalidade, parentesco, poder, cronologia ou geografia sem fonte.
- Não transforme um arquivo de protótipo em bíblia canônica.
- Não inclua conteúdo privado não destinado à biblioteca pública.
- Verifique se todos os registros novos ou alterados têm data e hora ou a indicação explícita de que não estavam disponíveis.
