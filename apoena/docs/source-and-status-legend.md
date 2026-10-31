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
| DESCARTADO/SUBSTITUÍDO | Rejeitado ou substituído | Não reintroduzir como estado atual sem pedido; preservar o registro histórico |
| DESCONHECIDO | Informação insuficiente | Manter lacuna |

## Eixo histórico/editorial

Use estes rótulos adicionais para preservar a evolução das informações. Eles não substituem os status da tabela acima.

| Rótulo | Significado | Tratamento |
|---|---|---|
| HISTÓRICO | Versão antiga preservada para consulta | Manter acessível; não apagar por estar desatualizada |
| ATUAL — NÃO NECESSARIAMENTE APROVADO | Versão mais recente localizada | Não presumir aprovação do autor |
| APROVADO PELO AUTOR | Confirmação explícita do autor | Aplicar somente no escopo confirmado |
| DESCARTADO | Ideia rejeitada ou abandonada | Preservar o conteúdo e a razão, se conhecida |
| DIVERGENTE | Fontes apresentam versões diferentes ou incompatíveis | Preservar ambas e encaminhar para auditoria |
| NÃO CONFIRMADO | Informação recuperada cuja validade/proveniência precisa ser verificada | Preservar com ressalva |
| PROPOSTA | Sugestão de IA ou possibilidade ainda não aprovada | Não tratar como decisão |

## Precedência
Correção explícita mais recente do autor prevalece para definir o estado atual **no mesmo escopo**, mas não autoriza apagar a versão anterior. Fonte primária aprovada prevalece sobre resumo de memória para determinar o que a fonte afirma. Se a precedência não puder ser estabelecida, registrar divergência, preservar as versões e pedir decisão.

## Metadados mínimos
Afirmação, status, fonte, escopo (mangá, jogo, editor ou ferramenta), IA/provedor e conversa quando conhecidos, versão anterior relacionada, decisão substituída e validação pendente.

## Regra obrigatória de data e hora
Todo novo registro, atualização, decisão, descoberta, correção, teste ou relatório deve informar data e hora em ISO 8601 com fuso horário quando disponível (ex.: 2026-10-31T02:55:00-03:00).

Quando aplicável, registrar separadamente:
- data_hora_do_evento: quando a conversa, decisão ou acontecimento ocorreu.
- data_hora_do_registro: quando a IA documentou ou atualizou a informação.

Não inventar datas, horários ou fusos. Se só a data for conhecida, escrever **Hora não disponível na fonte**. Se ambos forem desconhecidos, escrever **Data e hora não disponíveis na fonte**. Se o ambiente não fornecer relógio/fuso confiável, declarar a limitação em vez de fabricar um timestamp.
