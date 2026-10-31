# Legenda de proveniência e status

| Rótulo | Significado | Tratamento |
|---|---|---|
| CÂNONE CONFIRMADO | Fonte oficial aprovada | Preservar |
| DECISÃO DO AUTOR | Correção/instrução explícita | Aplicar no escopo indicado |
| RECUPERADO — VALIDAR | Memória/conversa sem fonte primária integral | Preservar com ressalva |
| IMPLEMENTADO — VERIFICADO | Código/cena e teste identificados | Informar repositório, branch, commit e teste |
| IMPLEMENTADO — HISTÓRICO | README/relato antigo sem validação atual | Não afirmar que funciona hoje |
| PLANEJADO | Requisito desejado | Não apresentar como existente |
| PROPOSTA | Sugestão não aprovada | Não aplicar como decisão |
| DESCARTADO/SUBSTITUÍDO | Rejeitado ou substituído | Não reintroduzir sem pedido |
| DESCONHECIDO | Informação insuficiente | Manter lacuna |

## Precedência
Correção explícita mais recente do autor prevalece no mesmo escopo. Fonte primária aprovada prevalece sobre resumo de memória. Se a precedência não puder ser estabelecida, registrar divergência e pedir decisão.

## Metadados mínimos
Afirmação, status, fonte, escopo (mangá, jogo, editor ou ferramenta), decisão substituída e validação pendente.

## Regra obrigatória de data e hora
Todo novo registro, atualização, decisão, descoberta, correção, teste ou relatório deve informar data e hora em ISO 8601 com fuso horário quando disponível (ex.: `2026-10-31T02:55:00-03:00`).

Quando aplicável, registrar separadamente:
- `data_hora_do_evento`: quando a conversa, decisão ou acontecimento ocorreu.
- `data_hora_do_registro`: quando a IA documentou ou atualizou a informação.

Não inventar datas, horários ou fusos. Se só a data for conhecida, escrever **Hora não disponível na fonte**. Se ambos forem desconhecidos, escrever **Data e hora não disponíveis na fonte**. Se o ambiente não fornecer relógio/fuso confiável, declarar a limitação em vez de fabricar um timestamp.
