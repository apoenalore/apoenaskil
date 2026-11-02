# Dossiê de recuperação — auditoria de segurança do Apoena Game Creator

**Fonte imediata:** dossiê forense fornecido pelo autor nesta conversa.  
**Conversa de origem indicada:** “Analisar segurança do repositório”.  
**Período indicado pela extração:** 2026-11-02 01:56:16 UTC a 2026-11-02 02:45:07 UTC.  
**Última mensagem da extração:** missão de preservação documental.  
**Data/hora do registro neste repositório:** não disponível na fonte.  
**Cobertura:** PARCIAL — baseada em extração textual fornecida; não equivale à leitura independente da conversa original nem à auditoria integral do repositório.

## 1. Declaração de completude e limitações

O dossiê recebido informa:

| Elemento | Situação declarada |
|---|---|
| Histórico da conversa original | Histórico visível disponível ao extrator; 24 turnos identificáveis |
| Período | 48 min 51 s |
| Link compartilhado | Página localizada, sem conteúdo textual recuperável |
| Imagens | 2 anexos identificados, sem reanálise visual integral nesta extração |
| TXT | 2 documentos identificados e examinados |
| Código-fonte individual | 5 arquivos recebidos e examinados naquela conversa |
| ZIPs | 3 entregas identificadas; conteúdo interno não integralmente acessível |
| Alterações efetivas no GameCreator | Nenhuma comprovada na conversa de origem |
| V4.2 Security Hardening | Proposta; não implementada |

A fonte compartilhada mencionada foi `https://chatgpt.com/share/6ae7f65e-9d10-83ea-85bd-b3641ebefdaa`. O extrator declarou que não conseguiu recuperar o texto da página. Não inferir mensagens adicionais além do histórico disponibilizado.

O dossiê cita dois anexos JPEG (`1000066266.jpg` e `1000066265.jpg`) relacionados às configurações do GitHub, mas declara que não houve reanálise visual independente. Não atribuir às imagens detalhes além dos descritos no histórico.

Foram mencionados três envios/entregas ZIP: `GameCreator-main (1).zip` (reenvios possivelmente duplicados, sem identidade binária confirmada) e `Apoena-GameCreator-V4.1.zip`. O conteúdo interno não foi integralmente recuperado. Não alegar inspeção dos 76 arquivos de runtime.

## 2. Histórico cronológico recuperado

### 2.1. 01:56:16–02:09:09 UTC — início e tentativas de acesso

O autor solicitou uma análise de segurança do repositório GameCreator, com foco em resiliência a ransomware, vulnerabilidades de código, cadeia de suprimentos e proteção de dados.

O endereço fornecido foi `https://github.com/apoenalore/GameCreator`. As tentativas iniciais de consulta retornaram 404. A IA apresentou hipóteses de endereço incorreto, repositório removido ou privado. O autor informou posteriormente que tornou o repositório público, mas a ferramenta continuou retornando 404. A extração registra que essa indisponibilidade não prova configuração incorreta pelo autor.

O autor perguntou como permitir a inspeção sem retirar a privacidade. Foram discutidas alternativas: ZIP, visibilidade pública temporária e envio de arquivos individuais. A recomendação inicial foi preservar a privacidade e preferir o ZIP.

### 2.2. 02:09:09–02:14:00 UTC — ZIPs e pacote V4.1

O autor enviou `GameCreator-main (1).zip`, mas a IA não conseguiu acessar seu conteúdo interno naquele ambiente. Após novas tentativas, foram identificados:

- `MANIFESTO-ARQUIVOS.txt`;
- `LEIA-ME-ENTREGA.txt`;
- `Apoena-GameCreator-V4.1.zip`.

O manifesto/documentação identificou a entrega V4.1, pasta `GameCreator-V4.1`, 76 arquivos de runtime, criação em 2026-11-01 17:29:42 -03:00, commit `0bd916157d9bfab6c6c9b121c26050f94918cf80` e referência a GitHub Actions run `41347018076`. A documentação afirmava que o pacote continha arquivos de runtime e excluía documentação interna, testes e CI. O ZIP não foi extraído integralmente pelo ambiente da conversa.

### 2.3. 02:15:25–02:20:42 UTC — contexto operacional e governança

O autor estabeleceu o cenário:

- aplicação executada localmente;
- uso por equipe;
- sistema operacional Windows;
- compartilhamento cloud;
- GitHub como serviço de compartilhamento;
- GitHub Actions habilitado;
- atualização distribuída por ZIP produzido pelo Actions.

O autor informou também que não havia aprovação independente obrigatória e que a proteção da branch `main` era desconhecida. A extração não comprova se essas configurações continuam iguais hoje.

A análise passou a considerar comprometimento de contas, alteração do código, workflows, tokens, secrets, artefatos, releases, ransomware e sincronização de arquivos danificados. Foram propostas MFA/passkeys, privilégio mínimo, proteção de branch, Pull Requests, revisão independente, restrição de permissões do Actions, SHA-256, assinatura digital e backups independentes.

### 2.4. 02:21:29–02:29:09 UTC — cobrança por análise efetiva

O autor questionou a falta de alterações concretas. A IA reconheceu que ainda não havia alterado arquivos, aplicado patch, criado commit, executado testes ou publicado V4.2.

Foi proposta uma futura V4.2 Security Hardening com Integrity Guard, SHA-256, Backup Protection, Safe Import, Secure Bridge, Startup Security e Security Logger. O dossiê classifica esses itens como proposta, não implementação.

### 2.5. 02:31:40–02:45:07 UTC — cinco arquivos-fonte e achados iniciais

O autor disponibilizou cinco arquivos individuais:

1. `index.html`;
2. `asset-library.js`;
3. `creator-bridge.js`;
4. `library-backup.js`;
5. `tileset-check.js`.

A IA realizou uma revisão estática inicial e registrou pontos de atenção em comunicação entre janelas, importação de backups, validação de imagens e IndexedDB. Não houve teste de exploração, teste de ransomware, teste de adulteração de release ou teste de restauração.

## 3. Contexto técnico e arquitetura operacional

### 3.1. Identidade e ambiente

| Propriedade | Informação recuperada | Status |
|---|---|---|
| Projeto | Apoena Game Creator | Identificação |
| Repositório | `apoenalore/GameCreator` | Declarado |
| Versão | V4.1 | Referência da entrega |
| Commit da entrega | `0bd916157d9bfab6c6c9b121c26050f94918cf80` | Manifesto |
| Execução | Local | Declaração do autor |
| Usuários | Equipe | Declaração do autor |
| Sistema operacional | Windows | Declaração do autor |
| Compartilhamento | GitHub/cloud | Declaração do autor |
| GitHub Actions | Habilitado | Declaração do autor |
| Distribuição | ZIP gerado por Actions | Declaração do autor |
| Aprovação independente | Não obrigatória na configuração relatada | Declaração histórica |
| Proteção da main | Desconhecida | Lacuna |

### 3.2. Fluxo de distribuição descrito

Repositório GitHub → GitHub Actions → geração do ZIP → distribuição do artefato → instalações locais Windows da equipe.

A quantidade de integrantes e computadores não foi informada. A extração não prova que a distribuição atual usa exatamente o mesmo workflow ou configuração.

### 3.3. Biblioteca Central e armazenamento

A interface `biblioteca/index.html` é descrita como Biblioteca Central, com busca, filtro por categoria, atualização, exportação/restauração de backup, download de PNG/original, projetos editáveis e exclusão de registros.

O armazenamento é local ao navegador via IndexedDB. Isso significa que o repositório GitHub e o ZIP não equivalem a backup da biblioteca local.

Categorias registradas:

| Categoria | Identificador |
|---|---|
| Personagens | `personagem` |
| Animais | `animal` |
| Cenários | `cenario` |
| Plantas | `planta` |
| Efeitos | `efeito` |
| Tilesets | `tileset` |
| Objetos | `objeto` |
| Outros | `outro` |

## 4. Inventário dos módulos examinados na conversa de origem

### 4.1. `shared/asset-library.js`

Responsabilidades relatadas: gerenciamento de assets e projetos, identificadores, conversão Data URL/Blob, persistência, listagem, exclusão, eventos, IndexedDB, fallback em memória no Node e comunicação com janela pai.

Constantes identificadas:

```javascript
const CHANNEL = "apoena.gamecreator.library.v1";
const DB_NAME = "apoena.gamecreator.library.v1";
const DB_VERSION = 1;
const ASSETS = "assets";
const PROJECTS = "projects";
```

Object stores: `assets` e `projects`. Índices de assets: `category`, `nameKey`, `updatedAt`. Índice de projetos: `updatedAt`.

Ações do protocolo citadas: `saveAsset`, `getAsset`, `listAssets`, `deleteAsset`, `saveProject`, `getProject`, `listProjects`, `deleteProject`.

Funções identificadas: `clone`, `jsonCopy`, `validTimestamp`, `makeId`, `emit`, `openDB`, `getRecord`, `getAllRecords`, `putRecord`, `removeRecord`, `toBlob`, `localSaveAsset`, `localListAssets`, `localDeleteAsset`, `localSaveProject`, `localListProjects`, `localDeleteProject`, `dispatch`, `requestHost`, `call`, `blobToDataURL`, `subscribe`.

O gerador de IDs usa `crypto.randomUUID()` quando disponível e fallback com data/hora + `Math.random()`.

Trecho observado na extração:

```javascript
root.parent.postMessage({
  channel: CHANNEL,
  type: "request",
  id: id,
  action: action,
  payload: payload || {}
}, "*");
```

O receptor de respostas verifica `event.source === root.parent`; portanto, não descrever o módulo como totalmente desprovido de validação da janela. A pendência registrada é validar também a origem (`event.origin`) e reforçar a integridade/autorização do protocolo.

Validação de imagem observada:

```javascript
if (!blob.type || blob.type.indexOf("image/") !== 0)
  throw new Error("A biblioteca aceita arquivos de imagem.");
```

O MIME declarado não comprova que os bytes correspondam a uma imagem válida.

### 4.2. `shared/creator-bridge.js`

Canal: `apoena.creator.v4.bridge.v1`.

Funções identificadas: `targetWindow()`, `request(action, payload, timeoutMs)` e `listen(handler)`.

O protocolo descrito inclui solicitação, resposta, ID, ação, payload, timeout e tratamento de erro. Timeout padrão: 5.000 ms; limites: 500–15.000 ms. `targetWindow()` tenta localizar `window.opener` ou `window.parent`.

Trecho observado:

```javascript
if ((event.origin !== origin && event.origin !== "null") ||
    !data ||
    data.channel !== CHANNEL ||
    data.type !== "request" ||
    typeof data.id !== "string" ||
    !event.source ||
    event.source === root) return;
```

Achado preliminar: a condição aceita origem opaca `"null"` e não restringe `event.source` a uma janela autorizada específica. O envio usa destino `"*"`. A explorabilidade depende do contexto de origem, isolamento, janelas que podem carregar o módulo e ações/payloads aceitos; não foi demonstrada.

### 4.3. `shared/library-backup.js`

Schema: `apoena.gamecreator.library-backup.v1`. Limites citados: `MAX_RECORDS = 10000` e `MAX_IMPORT_CHARS = 120 * 1024 * 1024`.

Funções identificadas: `library()`, `exportSnapshot()`, `isImageDataURL()`, `validate()`, `importSnapshot()`.

Exportação: assets, projetos, imagens/originais, metadados e datas são serializados em JSON; imagens são convertidas em Data URLs.

Validação relatada: schema, versão, arrays `assets` e `projects`, limite de registros, IDs, nomes, Data URLs, IDs duplicados por categoria e campo `data` dos projetos.

Importação: valida snapshot, tamanho, converte imagens, grava assets e projetos e retorna contagens.

Achado estático: a importação grava registros individualmente, sem transação/rollback global. Uma falha intermediária pode deixar restauração parcial. Ausência de assinatura/autenticação do backup foi observada; isso não prova que todo backup seja malicioso nem substitui validação estrutural.

### 4.4. `shared/tileset-check.js`

Módulo descrito como verificação conservadora de bordas, sem alterar a imagem. Função principal: `analyze(imageData, columns, rows, options)`. Limite padrão: 4.000.000 pixels. Colunas e linhas: 1–32. Opções: `alphaThreshold`, `maxTransparentRatio`, `checkRepeatSeams`, `colorTolerance`, `maxPixels`.

Analisa transparência nas bordas, diferenças entre extremidades, repetição horizontal/vertical e divisibilidade da imagem pela grade. Nenhuma vulnerabilidade confirmada foi registrada neste módulo na conversa.

### 4.5. `index.html`

Interface da Biblioteca Central. Elementos descritos: busca, filtro, assets, projetos, backup, restauração, download e exclusão. A extração relata uso de `textContent` para nomes/metadados, `URL.createObjectURL()` e `URL.revokeObjectURL()`, `JSON.stringify()` e `JSON.parse()`.

Input de backup observado:

```html
<input id="backupFile"
       type="file"
       accept="application/json,.json"
       hidden>
```

Limite de tamanho da interface: 120 MB. Restauração solicita confirmação do usuário.

## 5. Registro de achados SEC

**Nota de classificação:** os rótulos abaixo são IDs históricos do dossiê. Não representam severidade CVSS nem prova de exploração.

| ID | Arquivo/área | Observação | Classificação correta |
|---|---|---|---|
| SEC-001 | `creator-bridge.js` | Aceita `event.origin === "null"` e não restringe suficientemente `event.source` | Achado estático preliminar; explorabilidade não demonstrada |
| SEC-002 | `asset-library.js` | Envia `postMessage` para `"*"`; receptor de resposta verifica a janela pai, mas a origem não foi validada explicitamente | Achado estático; avaliar contexto e threat model |
| SEC-003 | `library-backup.js` | Importação salva registros individualmente, sem atomicidade/rollback global | Ausência de controle observada no código, segundo a extração |
| SEC-004 | `library-backup.js` | Sem assinatura/autenticidade criptográfica do backup | Ausência de controle observada; assinatura não substitui validação |
| SEC-005 | `asset-library.js` | MIME declarado é usado como validação de imagem | Achado estático; conteúdo real precisa ser decodificado/validado |
| SEC-006 | Distribuição | Integridade de ZIPs não verificada no fluxo descrito | Pendente de inspeção do pipeline e implementação |
| SEC-007 | Backup/projetos | Validação estrutural de projetos descrita como incompleta | Achado preliminar; requer leitura atual do código e schema |

Não houve prova de execução remota, acesso indevido, exploração, infecção por ransomware, adulteração de release ou falha real de recuperação. Não rotular os itens como vulnerabilidades exploráveis confirmadas sem teste reproduzível.

## 6. Riscos operacionais e controles discutidos

### 6.1. Conta/repositório

Ameaças possíveis: comprometimento de conta de integrante, alteração de código/workflows, artefatos adulterados, publicação maliciosa ou alteração de configurações.

Controles propostos: MFA/passkeys ou chaves físicas, privilégio mínimo, branch protegida, Pull Requests obrigatórios, aprovação independente, bloqueio de force push/exclusão de branch e revisão das permissões.

### 6.2. GitHub Actions e cadeia de suprimentos

Ameaças possíveis: permissões excessivas do `GITHUB_TOKEN`, secrets expostos, Actions de terceiros não fixadas, execução não confiável em eventos de PR, publicação automática e adulteração de artefatos.

Controles propostos: permissões mínimas por job, pinning de Actions por SHA, revisão dos workflows, proteção de environments/secrets, separação entre build e publicação, aprovação para release e manifesto de hashes.

O workflow efetivo não foi inspecionado no dossiê; todos esses pontos permanecem como itens de auditoria, não achados confirmados sobre YAML específico.

### 6.3. Ransomware e backup

Cenário hipotético: ransomware em uma estação criptografa arquivos locais; sincronização/commit transmite versões danificadas; outros integrantes recebem conteúdo comprometido; disponibilidade e dados são afetados.

Estratégia proposta: 3-2-1-1-0 (três cópias, dois tipos de mídia, uma cópia externa, uma offline/imutável, zero erros em testes de restauração). GitHub não deve ser tratado como única cópia de backup. IndexedDB local precisa de exportação e restauração verificadas.

## 7. Propostas e decisões — não confundir status

Proposta histórica de versão futura: **V4.2 Security Hardening**.

Componentes sugeridos:
- Integrity Guard;
- SHA-256;
- Backup Protection;
- Safe Import;
- Secure Bridge;
- Startup Security;
- Security Logger.

Nenhum componente acima deve ser considerado implementado por causa da proposta.

Decisões/informações relatadas pelo autor:
- aplicação local no Windows;
- uso por equipe;
- compartilhamento via GitHub/cloud;
- GitHub Actions habilitado;
- ZIP como distribuição;
- sem aprovação independente obrigatória, no momento relatado;
- proteção de `main` desconhecida.

A proposta de tornar o repositório público foi alternativa para permitir leitura e não é requisito permanente. O autor informou que o tornou público, mas a ferramenta continuou recebendo 404. O dossiê recomenda não manter o repositório público apenas para viabilizar análise.

## 8. Pendências técnicas e ordem recomendada

### P0 — governança e superfície de comunicação

1. Inspecionar estado atual de Rulesets/branch protection da `main`.
2. Confirmar exigência de Pull Request e aprovação independente.
3. Revisar o receptor do `creator-bridge.js`: origens permitidas, identidade da janela, origem opaca, lista de ações e validação de payloads.
4. Revisar o protocolo de `asset-library.js`: destino de mensagem, `event.origin`, `event.source`, autorização de ações e schema.
5. Inspecionar workflows reais do Actions, gatilhos, permissões, secrets, dependências externas e fluxo de publicação ZIP.

### P1 — integridade e dados

1. Validar snapshot completo antes de qualquer escrita.
2. Tornar importação transacional ou implementar staging + rollback comprovável.
3. Validar estrutura e tamanho de projetos, campos e imagens.
4. Decodificar imagens e verificar formato real, dimensões e limites de recursos; tratar SVG separadamente se aceito.
5. Implementar manifesto SHA-256 ligado a commit/release e verificar antes da instalação.
6. Avaliar assinatura assimétrica de artefatos; separar a chave privada de assinatura do código e do workflow não confiável.
7. Implementar backup independente e testar restauração em ambiente isolado.

### P2 — cobertura adicional

1. Auditar inicializadores CMD, PowerShell e Python.
2. Auditar bundle JavaScript e módulos legacy.
3. Auditar integração Godot, editor de mapas e Pixel Art.
4. Inventariar dependências e versões.
5. Criar testes automatizados de segurança e regressão.
6. Executar testes controlados em Windows e simulação de recuperação.

## 9. Critérios de evidência para encerrar cada pendência

Cada correção deverá conter:
- ID do achado;
- arquivo e trecho;
- ameaça e pré-condições;
- comportamento esperado;
- patch/commit;
- teste reproduzível antes/depois;
- resultado de CI no SHA correto;
- teste manual quando depender de Windows, navegador ou integração;
- riscos residuais e compatibilidade;
- status atualizado na Skill e no registro histórico.

Não fechar pendência por recomendação escrita, análise teórica ou CI de workflow não relacionado.

## 10. Escopo narrativo

A conversa não criou nem definiu personagens, lore, geografia ou cânone do mangá. “Personagens”, “animais”, “cenários” e outras categorias citadas são categorias da Biblioteca Central. Manter este conhecimento no domínio de ferramenta/editor/infraestrutura.

## 11. Índice de referências e fontes citadas

- Repositório: https://github.com/apoenalore/GameCreator
- Link da conversa original, sem texto recuperável segundo o extrator: https://chatgpt.com/share/6ae7f65e-9d10-83ea-85bd-b3641ebefdaa
- Workflow da entrega V4.1: https://github.com/apoenalore/GameCreator/actions/runs/41347018076
- Arquivos examinados na conversa de origem: `index.html`, `shared/asset-library.js`, `shared/creator-bridge.js`, `shared/library-backup.js`, `shared/tileset-check.js`.
- Pacote V4.1: `Apoena-GameCreator-V4.1.zip`, 76 arquivos de runtime segundo o manifesto; conteúdo ZIP não integralmente inspecionado.
- Imagens: `1000066266.jpg` e `1000066265.jpg`; inspeção visual integral pendente.
- TXT: `MANIFESTO-ARQUIVOS.txt` e `LEIA-ME-ENTREGA.txt`; conteúdos foram usados na extração, mas os binários não são preservados por este registro.

## 12. Declaração final

Esta página preserva o dossiê recebido e suas limitações. A auditoria do repositório permanece **PARCIAL / NÃO CONCLUÍDA**. Não há evidência neste registro de patch de segurança, commit de hardening, testes de exploração ou publicação V4.2.
