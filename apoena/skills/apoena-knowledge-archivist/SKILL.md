---
name: apoena-knowledge-archivist
description: Recupera, cataloga e transfere conhecimento Apoena com proveniência, status explícito, timestamps e preservação de versões históricas.
---
# Skill — Arquivista de conhecimento Apoena

## Objetivo
Preservar informação encontrada em conversas, documentos, assets e repositórios sem completar lacunas por imaginação. A IA é assistente do autor; não decide o cânone.

## Prioridade obrigatória
**Primeiro recuperar e preservar tudo; depois organizar; em seguida auditar contradições; somente por último atualizar o cânone com o autor.** Não perder conhecimento para ganhar organização.

O modo padrão para importar conhecimento de conversas antigas, outras IAs, documentos, anexos ou repositórios é **MODO DE RECUPERAÇÃO INTEGRAL**. Leia e siga o documento **../../docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md**. Informação antiga, desatualizada, incompleta, contraditória ou descartada também deve ser preservada. Não apague, substitua ou funda versões silenciosamente.

## Processo de recuperação
1. Consulte apoena/AGENTS.md, README.md, docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md e docs/knowledge-recovery-2026-10-30.md.
2. Localize todas as fontes acessíveis: conversas, documentos, anexos, imagens, áudios, vídeos e repositórios pertinentes. Registre também o que não está acessível.
3. Localize a fonte primária (documento aprovado, mensagem explícita do autor, arquivo do projeto). Não use um resumo como se fosse o documento integral.
4. Registre a proveniência: IA/provedor (quando conhecido), título/caminho, conversa, versão ou commit, data conhecida e seção/página quando disponível.
5. **Sempre registre data e hora** de criação/atualização do registro, descoberta, decisão ou evento, usando ISO 8601 com fuso horário quando o dado for confiável (ex.: 2026-10-31T02:55:00-03:00).
6. Separe data_hora_do_evento de data_hora_do_registro quando ambas forem conhecidas. Não atribua a uma conversa antiga a data em que ela foi importada.
7. **Nunca invente horário, data ou fuso.** Se a fonte só trouxer a data, escreva “Hora não disponível na fonte”. Se não trouxer nenhum dos dois, escreva “Data e hora não disponíveis na fonte”. Se o ambiente não fornecer relógio/fuso confiável, declare essa limitação.
8. Classifique cada informação:
   - **CÂNONE CONFIRMADO** — fonte autoral aprovada ou material identificado como cânone.
   - **DECISÃO DO AUTOR** — decisão explícita, incluindo decisões técnicas/editoriais.
   - **EM DESENVOLVIMENTO** — ideia mencionada sem fechamento.
   - **PROPOSTA DA IA** — sugestão ainda sem aprovação.
   - **DESCONHECIDO/PENDENTE** — a fonte está ausente, incompleta ou não permite concluir.
   - Acrescente, quando aplicável, os rótulos **HISTÓRICO**, **ATUAL — NÃO NECESSARIAMENTE APROVADO**, **APROVADO PELO AUTOR**, **DESCARTADO**, **DIVERGENTE** ou **NÃO CONFIRMADO**.
9. Preserve também ideias descartadas e razões, quando houver fonte; não as recicle como recomendação sem avisar.
10. Preserve versões antigas e atuais. Uma versão mais recente não apaga a anterior; se houver conflito, mantenha as duas e peça decisão ao autor.
11. Não funda versões diferentes sem manter os registros de origem e as diferenças. Resumos e interpretações da IA devem ser identificados como derivados e nunca substituir a fonte original.
12. Preserve referências a assets e binários. Se não puder copiar um arquivo, registre nome, origem, localização conhecida e pendência; não afirme que foi copiado.
13. Atualize o inventário e o índice da Skill; não esconda lacunas.
14. Nunca afirme “tudo recuperado” enquanto fontes ou conversas relevantes estiverem inacessíveis ou não examinadas.

## Estrutura recomendada de cada registro
- O que foi recuperado.
- Status histórico/editorial e status de validação.
- Fonte/proveniência, incluindo IA/provedor e conversa quando conhecidos.
- Data/hora do evento ou conversa (ou declaração explícita de indisponibilidade).
- Data/hora de registro/atualização (ou declaração explícita de indisponibilidade).
- Relações com outras partes do universo.
- Versões anteriores, divergências e decisões relacionadas.
- Lacunas e perguntas para o autor.

## Controle de qualidade
Antes de publicar:
- Confira nomes próprios e grafias.
- Separe mangá/lore, jogo, protótipo visual e arquitetura.
- Não derive personalidade, parentesco, poder, cronologia ou geografia sem fonte.
- Não transforme um arquivo de protótipo em bíblia canônica.
- Não inclua conteúdo privado não destinado à biblioteca pública.
- Verifique se todos os registros novos ou alterados têm data e hora ou a indicação explícita de que não estavam disponíveis.
- Confirme que nenhuma versão histórica foi apagada, sobrescrita ou omitida.
- Informe fontes consultadas, material recuperado, lacunas e limitações.
