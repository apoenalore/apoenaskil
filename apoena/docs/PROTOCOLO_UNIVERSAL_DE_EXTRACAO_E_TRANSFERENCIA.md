# Protocolo Universal de Extração e Transferência de Conhecimento — Apoena

**Versão:** 1.0  
**Solicitado em:** 2026-10-31T17:15:08Z  
**Aplicação:** ChatGPT, Claude, Gemini, Grok, Copilot e qualquer IA com acesso autorizado às fontes e ao GitHub.  
**Status:** procedimento operacional obrigatório para novas extrações; não altera o cânone por si só.

## 1. Objetivo

Recuperar o conhecimento existente nas conversas e materiais de origem com o máximo de fidelidade, preservando detalhes, contexto, autoria, sequência temporal, correções, decisões, propostas, dúvidas e versões antigas.

A IA não deve apenas produzir um resumo do que lembra. Deve consultar a fonte original disponível, demonstrar o que leu e registrar o que não conseguiu acessar.

**Ordem obrigatória:**

1. Identificar as fontes.
2. Confirmar o acesso real.
3. Ler e registrar integralmente tudo o que estiver acessível.
4. Preservar o material bruto ou uma representação detalhada e rastreável.
5. Organizar o conhecimento por assunto.
6. Auditar repetições, mudanças e contradições.
7. Atualizar Skills e índices sem apagar o histórico.
8. Entregar relatório de cobertura e pendências.

Não inverter essa ordem para começar diretamente pela criação de Skills.

## 2. Limite de acesso: não fingir leitura

Antes de iniciar, a IA deve declarar qual fonte realmente consegue consultar:

- conversa aberta e integral;
- histórico completo acessível por ferramenta autorizada;
- exportação integral de conversa;
- documento ou transcrição fornecida;
- contexto parcial;
- resumo ou memória;
- apenas arquivos já existentes no GitHub.

Essas modalidades não são equivalentes.

Acesso ao repositório GitHub **não** significa acesso automático às conversas privadas da plataforma de origem. Um prompt não consegue conceder permissões nem recuperar mensagens que a IA não consegue visualizar.

Se a fonte original não estiver disponível, a IA deve:
1. registrar a limitação;
2. indicar exatamente o material acessível;
3. classificar a recuperação como parcial, baseada em resumo ou não verificada;
4. solicitar exportação, arquivo ou acesso autorizado quando necessário;
5. não afirmar que leu a conversa integral.

## 3. Etapa A — Descoberta e preparação do repositório

Ao receber o repositório:

1. Confirmar nome completo, URL, branch principal e commit de referência.
2. Ler o `/AGENTS.md` da raiz.
3. Ler `README.md`.
4. Ler `apoena/AGENTS.md`.
5. Ler este protocolo e `apoena/docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md`.
6. Ler `apoena/docs/source-and-status-legend.md`.
7. Ler `apoena/skills/INDEX.txt`.
8. Ler `apoena/references/README.md` e `apoena/docs/knowledge-gaps-and-contradictions.md`.
9. Identificar Skills e registros que já tratam dos assuntos da fonte.
10. Registrar o commit e a estrutura consultados, para que a auditoria seja reproduzível.

Não comece a escrever arquivos antes de compreender a estrutura existente.

## 4. Etapa B — Inventário da fonte original

Para cada conversa, documento ou pacote de anexos, criar um identificador estável e registrar, quando disponível:

| Campo | O que registrar |
|---|---|
| ID da fonte | Identificador único e não sensível |
| Plataforma | ChatGPT, Claude, Gemini, Grok, Copilot, arquivo local etc. |
| Título | Título original da conversa/documento |
| Localizador | URL, ID da conversa, nome e caminho do arquivo, se disponíveis |
| Autor da mensagem | Criador, IA, terceiro ou desconhecido |
| Período original | Primeira e última data/hora conhecidas |
| Quantidade | Total de mensagens/páginas/itens, se a fonte informar |
| Acesso | Integral, parcial, exportação, resumo, memória ou outro |
| Anexos | Nome, tipo, quantidade, páginas e situação de leitura |
| Limitações | Mensagens ausentes, anexos expirados, OCR ruim, imagens não acessíveis etc. |
| Cobertura | COMPLETA, PARCIAL, NÃO VERIFICADA ou BLOQUEADA |

Não inventar contagem, data, hora, autor, título ou identificador. Use **não disponível na fonte** quando necessário.

## 5. Etapa C — Leitura integral e sequencial

Quando a fonte original estiver acessível:

1. Começar na primeira mensagem e avançar até a última.
2. Ler mensagens do criador e da IA, sem selecionar apenas as que parecem importantes.
3. Preservar a ordem cronológica.
4. Incluir perguntas, respostas, correções, exemplos, objeções, decisões, mudanças de assunto e mensagens curtas que alterem o contexto.
5. Examinar imagens, documentos, áudio, vídeo e outros anexos disponíveis; registrar quando a leitura visual, auditiva ou textual não for possível.
6. Não pular blocos para economizar contexto.
7. Não substituir a leitura por uma síntese antiga ou pela Skill que já existe.

### Conversas longas ou limites de contexto

Dividir a leitura em blocos sequenciais e contíguos. Para cada bloco, registrar:

- número do bloco;
- primeira mensagem/posição;
- última mensagem/posição;
- quantidade lida, se conhecida;
- assunto(s) identificados;
- lacunas ou falhas de carregamento;
- confirmação de continuidade para o bloco seguinte.

Manter um mapa de cobertura. Não marcar a conversa como integral se existir intervalo não examinado.

Se a plataforma não mostrar numeração de mensagens, usar timestamps, títulos de seção, marcadores de posição ou outro localizador reproduzível. Se não houver nenhum, explicar a limitação.

## 6. Etapa D — Registro bruto e preservação da fonte

A primeira saída deve ser um registro histórico, não uma Skill.

Estrutura recomendada:

```text
apoena/
  archive/
    conversations/
      <source-id>/
        source-manifest.md
        transcript-part-001.md
        transcript-part-002.md
        attachments/
  docs/
    recovery/
      <source-id>-recovery-report.md
```

Regras:

- Se houver exportação integral, preservar o conteúdo original da exportação, respeitando privacidade, segurança e limites de armazenamento.
- Se a plataforma permitir transcrição literal, manter falas e sequência; não reescrever como se fossem palavras originais.
- Se só for possível produzir notas, identificá-las como **registro derivado**, nunca como transcrição literal.
- Preservar trechos exatos importantes entre aspas, com o localizador da mensagem.
- Não remover mensagens só porque parecem repetidas ou irrelevantes; quando o armazenamento exigir seleção, registrar o critério e manter o inventário completo.
- Não inserir senhas, tokens, chaves de API ou segredos no repositório. Redigir o segredo e registrar que houve uma redação de segurança.
- Não declarar que um binário foi preservado se apenas seu nome, descrição ou texto extraído foi registrado.

## 7. Etapa E — Extração detalhada do conhecimento

Depois da preservação, decompor o material em afirmações e registros rastreáveis.

Capturar, conforme aplicável:

- ideias originais e sua evolução;
- personagens, nomes, apelidos, relações, aparência e características;
- acontecimentos, diálogos, ordem narrativa e cronologia;
- cosmologia, dimensões, povos, geografia e sociedade;
- Aurium, elementos, poderes, constelações, bênçãos e regras;
- criaturas, fauna, flora, artefatos e ecossistemas;
- regras, sistemas, mecânicas, números e exemplos;
- decisões explícitas do criador;
- correções de interpretações anteriores da IA;
- propostas do criador ainda não aprovadas;
- sugestões da IA;
- ideias rejeitadas, abandonadas ou substituídas;
- perguntas abertas, lacunas e assuntos interrompidos;
- referências visuais e anexos;
- escopo de cada informação: mangá, jogo, protótipo, ferramenta, editor ou infraestrutura.

### Modelo mínimo para cada registro importante

```yaml
record_id: APOENA-REC-0001
claim_or_event: "Descrição objetiva da informação"
speaker: "Criador | IA | terceiro | desconhecido"
source_id: "ID da conversa/documento"
source_locator: "mensagem, timestamp, página, seção ou trecho"
original_excerpt: "Trecho literal, se disponível"
representation: "LITERAL | PARÁFRASE | RESUMO | INFERÊNCIA"
event_datetime: "data/hora original ou não disponível na fonte"
recorded_datetime: "data/hora deste registro, se confiável"
scope: "mangá | jogo | protótipo | ferramenta | outro"
status: "DECISÃO DO AUTOR | CÂNONE CONFIRMADO | PROPOSTA | RECUPERADO — VALIDAR | DESCARTADO | DESCONHECIDO"
related_records: []
notes: "Limites, contexto e divergências"
```

Não é necessário usar YAML em todos os documentos, mas os campos devem ser preservados de forma legível e rastreável.

## 8. Etapa F — Correções, decisões e contradições

Nunca misturar estas categorias:

- **Declaração do criador:** o que o criador efetivamente disse.
- **Decisão explícita:** instrução ou aprovação inequívoca, limitada ao escopo indicado.
- **Proposta do criador:** possibilidade apresentada sem confirmação final.
- **Resposta ou sugestão da IA:** conteúdo produzido pela IA, não pelo criador.
- **Interpretação da IA:** leitura derivada, que precisa ser identificada.
- **Recuperação de resumo/memória:** conteúdo sem acesso à mensagem original.
- **Lacuna:** informação que não foi encontrada.

Quando uma informação mudar:

1. preservar o registro anterior;
2. registrar a nova declaração;
3. apontar a fonte e a data de cada uma;
4. indicar se a nova declaração substitui explicitamente a anterior ou se o vínculo ainda é incerto;
5. atualizar o estado atual apenas no escopo autorizado;
6. manter a divergência aberta se não houver decisão suficiente.

Não harmonizar números, nomes, idades, datas, poderes, relações ou versões por conveniência narrativa.

## 9. Etapa G — Anexos e materiais visuais

Para cada anexo, registrar:

- nome original;
- tipo e formato;
- tamanho, se disponível;
- hash SHA-256, se o arquivo binário estiver acessível;
- número de páginas, quadros ou duração, quando aplicável;
- conversa/documento de origem;
- se foi aberto e examinado;
- se a leitura foi textual, visual, auditiva ou parcial;
- transcrição, descrição e páginas/trechos correspondentes;
- localização do binário original;
- situação de cópia para o GitHub.

A transcrição de um PDF não substitui o PDF. A descrição de uma imagem não substitui a imagem. Se o binário não puder ser transferido, registrar a pendência sem afirmar que o arquivo está armazenado.

## 10. Etapa H — Organização e integração nas Skills

Só iniciar depois de preservar a fonte e criar o relatório de cobertura.

1. Consultar `apoena/skills/INDEX.txt` e localizar Skills existentes.
2. Mapear cada registro para a Skill adequada.
3. Reutilizar Skills existentes quando possível; não criar duplicatas só para acomodar uma conversa.
4. Criar uma nova Skill somente quando houver domínio especializado distinto e conteúdo suficiente.
5. Atualizar a Skill com informação rastreável, sem substituir a fonte bruta.
6. Inserir links para os registros de origem.
7. Atualizar o índice de Skills.
8. Atualizar `apoena/AGENTS.md` quando o catálogo ou as instruções mudarem.
9. Atualizar inventários, lacunas e documentos relacionados.
10. Conferir todos os caminhos e links adicionados.

Uma Skill é uma camada operacional derivada. Ela nunca deve ser a única cópia de uma informação histórica importante.

## 11. Controle de alterações no GitHub

- Confirmar branch e commit antes de editar.
- Preferir branch de trabalho e Pull Request para transferências ou alterações documentais relevantes.
- Não fazer exclusões, renomeações destrutivas ou substituições integrais sem autorização explícita.
- Usar commits pequenos e descritivos.
- Registrar fonte, escopo, arquivos alterados e validações.
- Verificar se nenhum arquivo histórico foi perdido.
- Não declarar concluído enquanto houver links quebrados, fontes não classificadas ou cobertura não demonstrada.

## 12. Auditoria de qualidade — checklist obrigatório

### Acesso e leitura
- [ ] A fonte original foi identificada.
- [ ] O tipo real de acesso foi declarado.
- [ ] A conversa foi lida da primeira à última mensagem acessível.
- [ ] Mensagens do criador e da IA foram examinadas.
- [ ] A cobertura foi demonstrada por blocos/intervalos.
- [ ] Mensagens inacessíveis foram listadas.
- [ ] Anexos foram inventariados e seu estado de leitura foi informado.

### Fidelidade e preservação
- [ ] O registro bruto foi preservado ou a impossibilidade foi explicada.
- [ ] Transcrição, paráfrase, resumo e inferência estão diferenciados.
- [ ] Correções, decisões, propostas e ideias rejeitadas foram mantidas.
- [ ] Contradições não foram resolvidas por suposição.
- [ ] Datas e horários não foram inventados.
- [ ] Os binários não foram confundidos com suas transcrições.

### Integração
- [ ] Skills existentes foram consultadas antes de criar novas.
- [ ] Cada nova informação relevante tem proveniência.
- [ ] Índice e instruções foram atualizados.
- [ ] Links e caminhos foram verificados.
- [ ] O histórico anterior continua acessível.
- [ ] O relatório final declara limites e pendências.

## 13. Estados permitidos para o resultado

Use somente um estado que a evidência sustente:

- **COMPLETA:** fonte integral acessada, lida e coberta; anexos e limitações documentados.
- **PARCIAL:** apenas parte da fonte foi acessada ou examinada.
- **BASEADA EM RESUMO:** não houve acesso à conversa original; a recuperação deriva de resumo/memória.
- **NÃO VERIFICADA:** a cobertura ou a origem não pôde ser comprovada.
- **BLOQUEADA:** a tarefa não pode avançar sem fonte, permissão ou material necessário.

Não use "100% recuperado" ou "integral" apenas porque foi criado um documento longo.

## 14. Relatório obrigatório ao concluir

Entregar um relatório com:

1. repositório, branch e commit consultados;
2. fontes localizadas;
3. fontes efetivamente abertas e lidas;
4. quantidade de mensagens/páginas/itens lidos, se conhecida;
5. intervalos cobertos e intervalos ausentes;
6. anexos recebidos, examinados, copiados ou pendentes;
7. registros históricos criados;
8. Skills e índices atualizados;
9. contradições e lacunas encontradas;
10. arquivos alterados e commits;
11. validações realizadas;
12. estado final: COMPLETA, PARCIAL, BASEADA EM RESUMO, NÃO VERIFICADA ou BLOQUEADA.

## 15. Trecho obrigatório para o prompt universal

Copie este bloco para qualquer prompt enviado a uma IA que deverá recuperar conhecimento de Apoena:

> **INSTRUÇÃO OBRIGATÓRIA — LEITURA DO PROTOCOLO DO REPOSITÓRIO**
>
> Antes de analisar, resumir, extrair ou criar qualquer Skill, acesse o repositório GitHub indicado e leia integralmente o arquivo `/AGENTS.md` da raiz. Em seguida, siga a ordem de leitura indicada nele e leia integralmente `apoena/docs/PROTOCOLO_UNIVERSAL_DE_EXTRACAO_E_TRANSFERENCIA.md`, `apoena/AGENTS.md` e `apoena/docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md`.
>
> Não comece a extração antes de confirmar que leu essas instruções. Trabalhe em MODO DE RECUPERAÇÃO INTEGRAL. Consulte a conversa original desde a primeira até a última mensagem que estiver realmente acessível, incluindo mensagens do usuário e da IA, e examine os anexos disponíveis. Não use memória ou resumos como substitutos da leitura da fonte original.
>
> Preserve primeiro o conteúdo histórico e sua proveniência. Registre detalhes, exemplos, correções, decisões, propostas, rejeições, versões, datas, dúvidas e contradições. Só depois organize o conhecimento e proponha atualizações nas Skills. Não apague nem sobrescreva registros antigos.
>
> Se não conseguir acessar a conversa integral, informe exatamente o que conseguiu acessar, o que está faltando e por quê. Não invente mensagens, contagens, datas ou anexos. Não declare recuperação integral sem comprovação.
>
> Antes de gravar no GitHub, apresente o inventário das fontes e dos arquivos que pretende criar ou atualizar. Ao terminar, entregue o relatório de cobertura e as pendências exigidas pelo protocolo.

## 16. Regra final

**O objetivo não é produzir a Skill mais curta. É garantir que o conhecimento original não se perca, que cada afirmação tenha origem rastreável e que uma IA futura consiga entender o que foi dito, por quem, em qual contexto e como a informação evoluiu.**
