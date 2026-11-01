# Apoena — análise e plano de chefes, níveis e missões

Data: 2026-11-01. Hora do registro não disponível na fonte.
Status: análise estática e PROPOSTA DE GAMEPLAY para prototipação. Nenhuma mudança de código, cânone ou parâmetro publicada nos repositórios. Números abaixo são hipóteses de balanceamento, não resultados de testes com jogadores.

## 1. Fontes e cobertura

| Repositório | Revisão examinada | Escopo |
|---|---|---|
| apoenalore/apoenaskil | `9f916b66deb2328eafd5c8c9e9038bcf6e5567f2` | Inventário completo; recuperação dos 111 arquivos textuais; busca transversal e leitura dirigida das regras, fontes, Aurium, progressão, sistemas, feras e lacunas. Não equivale a nova auditoria página a página dos PDFs originais. |
| apoenalore/GameCreator | `0bd916157d9bfab6c6c9b121c26050f94918cf80` | Inventário completo; documentação e módulos menores de 100 KB recuperados, com exame dos contratos de catálogo, objetos e plano geral. Fontes HTML de aproximadamente 16 MB e bundles/legados grandes não foram lidos integralmente. A tentativa de obter o HTML V4 retornou conteúdo vazio, embora com SHA. Busca indexada sem resultados não prova ausência nesses arquivos. |
| apoenalore/Apoena-pixel-art-html | `a54eb4328640f97cd1e4020f7fa85c96c3070017` | Inventário e recuperação dos 34 arquivos; exame do combate HTML, exploração, script principal Godot, layouts e documentação de coop/ecologia. |

A análise usa snapshots da branch `main`. Não abrange todas as branches, histórico completo de commits, issues/PRs, imagens originais ou execução Android/Godot. Não é uma declaração de auditoria integral de cada linha dos três projetos.

Fontes centrais:

- [Regras e lacunas do universo](https://github.com/apoenalore/apoenaskil/blob/9f916b66deb2328eafd5c8c9e9038bcf6e5567f2/apoena/docs/knowledge-gaps-and-contradictions.md).
- [Sistema de Aurium](https://github.com/apoenalore/apoenaskil/blob/9f916b66deb2328eafd5c8c9e9038bcf6e5567f2/apoena/skills/apoena-aurium-system/SKILL.md).
- [Progressão e economia](https://github.com/apoenalore/apoenaskil/blob/9f916b66deb2328eafd5c8c9e9038bcf6e5567f2/apoena/skills/apoena-progression-economy/SKILL.md).
- [Plano geral do Creator](https://github.com/apoenalore/GameCreator/blob/0bd916157d9bfab6c6c9b121c26050f94918cf80/PLANO_GERAL_APOENA.md).
- [Combate HTML atual](https://github.com/apoenalore/Apoena-pixel-art-html/blob/a54eb4328640f97cd1e4020f7fa85c96c3070017/index.html#L34).
- [Runtime Godot atual](https://github.com/apoenalore/Apoena-pixel-art-html/blob/a54eb4328640f97cd1e4020f7fa85c96c3070017/scripts/mundo_2_5d.gd).

## 2. Diagnóstico

1. **Não há chefe lutável no runtime Pixel Art examinado.** O HTML MOBA contém herói, tropas, torres e projéteis. A exploração HTML e o script Godot concentram movimento, desenho, clima e ecossistema. `docs/TERRAS_E_COOP.md` classifica dungeons, monstros, dragão e coop como requisitos futuros.
2. **A progressão ainda precisa de implementação nesse runtime.** No MOBA HTML, `reset()` fixa HP em 4.000, ATK em 420 e velocidade em 175. A estrutura do herói não contém nível/XP. O plano do Creator já prevê MOBA temporário 0–20 e três camadas permanentes: personagem, mundo e menu.
3. **Há assimetria de alcance.** Ataque do herói busca alvo até 235 unidades; torre dispara até 155. Isso permite atingir uma torre fora do alcance dela. Não prova, sozinho, um defeito de design; precisa de decisão de combate antes de replicar a lógica em chefes.
4. **O ataque atual tem intervalo mínimo de 0,48 s.** Seu teto aritmético é 420 / 0,48 = 875 de dano por segundo, sem considerar voo, movimentação, aquisição de alvo ou falhas. Esse intervalo existe no protótipo; não representa confirmação da regra definitiva de habilidades sem cooldown do universo.
5. **As fontes antigas não são a implementação atual.** Registros recuperados citam Q de 20% de HP, R de 100% e F de recuperação total. Não estão implementados no HTML Pixel Art examinado. Aplicá-los literalmente a chefes poderia trivializar lutas ou exigir HP artificialmente alto.
6. **O Creator já oferece fundações aproveitáveis.** Biblioteca, spritesheets, metadados de objetos e catálogo portátil de itens/receitas existem como módulos. O catálogo portátil explícito tem `items`, `recipes` e `assets`; ainda precisa de contrato específico para chefes, progressão e missões, além do consumidor no jogo.

## 3. Regras para respeitar Apoena

- Nível de jogo mede avanço de gameplay. Não deve virar uma escala canônica de Aurium.
- Manifestação, Controle Elemental e Domínio Ambiental permanecem fases de domínio, não níveis automáticos de força.
- Cada reserva de Aurium é individual: dois personagens com 100% não têm poder equivalente.
- Profissão, competência e manifestação evoluem em trilhas distintas. Um ferreiro pode desenvolver combate e outras profissões.
- Apoena inicial não deve ganhar manifestação elemental apenas por atingir determinado nível. Os marcos narrativos precisam ser respeitados.
- Não presumir que feras ancestrais são chefes destinados à morte ou montarias. O Guardião dos Ventos escolhe voluntariamente seu vínculo; não deve ser convertido em recompensa de domesticação automática.
- Não identificar o dragão da dungeon com entidades cosmológicas sem decisão do autor.
- A derrota prevista numa prova do Modo História deve ter conclusão narrativa clara e recompensar o avanço da história. Não deve parecer um chefe normal que exige tentativas infinitas.

## 4. Chefes difíceis e vencíveis

### Estrutura comum

Todo golpe deve passar por **aviso → execução → recuperação**. O jogador precisa reconhecer a ameaça, ter uma resposta possível e receber uma oportunidade de atacar depois. A dificuldade cresce pela combinação de padrões conhecidos, e não apenas por HP, velocidade e dano maiores.

| Parâmetro inicial de teste | Primeiro chefe | Chefe intermediário |
|---|---|---|
| Duração desejada de uma tentativa bem-sucedida | 60–90 s | 90–150 s |
| Aviso de ataque perigoso | 0,9–1,2 s | 0,7–1,0 s |
| Recuperação após golpe pesado | 1,2–1,8 s | 1,0–1,5 s |
| Dano de golpe leve, contra equipamento de referência | 8–12% do HP do jogador | 10–15% |
| Dano de golpe pesado evitável | 20–25% | 25–35% |
| Fases | 2 | 2–3 |
| Ataques principais | 3 | 3–5 |

Os percentuais são alvos para calibrar o dano contra uma ficha de referência. Não significam que todo jogador, independentemente de armadura e nível, sempre perderá a mesma porcentagem de vida.

Proteções de justiça:

- Nenhum golpe sem aviso deve eliminar um personagem saudável dentro da faixa recomendada.
- Cada execução só causa os impactos previstos; permanecer dentro de uma hitbox não deve multiplicar dano por quadro.
- Ataques em área precisam deixar rota de fuga alcançável na velocidade atual do personagem. Não basta existir um pixel seguro do outro lado da arena.
- Ataques consecutivos não podem manter o jogador permanentemente atordoado.
- Invulnerabilidade do chefe, se houver, tem motivo legível, duração finita e condição de encerramento.
- Mudança de fase não recompõe toda a vida nem causa golpe instantâneo sem aviso.
- Sempre existe uma forma de causar dano com equipamentos e competências acessíveis antes da luta; afinidade elemental oferece vantagem, sem exigir uma manifestação indisponível.
- Não exigir item raro aleatório ou gasto de recurso irreversível a cada tentativa.
- Reinício próximo, sem caminhada longa; ajuda opcional após derrotas, com dicas antes de redução de dificuldade. Ajustes numéricos só em nova tentativa e com opção do jogador.

### Primeiro protótipo: chefe de dungeon, identidade pendente

Usar um identificador técnico, `boss_dungeon_01`, até definir criatura, aparência e lugar narrativo. Não atribuir nome/poder canônico por conta própria.

1. **Ataque frontal:** cone visível; permite sair pela lateral.
2. **Investida:** direção fixada ao fim do aviso; não persegue o jogador durante todo o golpe. Termina com recuperação.
3. **Área no chão:** local marcado antes da execução; mantém corredor seguro.

Fase 1 até 50% de vida: apresenta os três ataques separadamente. Fase 2: combina dois padrões já apresentados, sem aumentar simultaneamente velocidade, dano e alcance. Evitar lacaios na primeira versão para isolar o balanceamento.

### Como calcular HP

`HP do chefe ≈ DPS efetivo de referência × duração-alvo em segundos`.

Exemplo exclusivamente ilustrativo: teto de ataque HTML de 875 DPS, com 60% de aproveitamento durante esquivas e reposicionamento, resulta em 525 DPS efetivos. Para 80 s, um ponto inicial seria 42.000 HP. **Isso não recomenda transplantar 42.000 HP para Godot.** Primeiro é necessário medir o combate novo. A janela vulnerável e a defesa devem entrar no DPS efetivo sem desconto duplicado.

Não ajustar a vida a cada ataque do jogador. Definir a ficha no início do encontro com base no conteúdo e dificuldade escolhida. O jogador precisa sentir que equipamento melhor encurta a luta.

### Habilidades percentuais e recuperação

Se Q/R/F antigos forem retomados, criar regras explícitas por categoria de alvo, exibidas na descrição. Possibilidades para teste: componente percentual limitado contra chefes; teto por acerto; resistência temporária a controles repetidos; cura limitada por carga ou recurso de combate. Não trocar silenciosamente a fórmula de uma habilidade nem presumir que ATK aumenta todo dano percentual. A solução final depende da regra Apoena que ainda precisa de formalização.

Não introduzir cooldown genérico como solução automática. Reserva, duração da ação, recuperação de animação e limite de cargas podem ser avaliados separadamente, preservando a proposta de habilidades movidas por Aurium.

## 5. Sistema de evolução

### Separação de dados

| Camada | O que progride | Efeito |
|---|---|---|
| Personagem de História/Exploração | Nível, experiência, equipamentos e competências | Capacidades daquele personagem/save |
| Profissões | Prática contextual e tarefas próprias | Receitas, qualidade e opções profissionais |
| Domínio elemental | Treino e desafios específicos autorizados | Uso mais competente das manifestações disponíveis |
| Mundo | Relações, construções e acesso a regiões | Mudanças persistentes naquele mundo |
| Menu/perfil | Opções e estruturas desbloqueadas | Conveniência e conteúdo; evitar vantagem permanente de combate no PvP |
| MOBA | Nível temporário 0–20 por partida | Reinicia a cada partida; saldo separado do permanente |

Proposta para a primeira versão: implementar e testar **níveis 1–20 de aventura**, sem declarar esse o teto definitivo do jogo. O MOBA conserva seu plano separado 0–20.

Curva inicial de XP para ir de L a L+1, para L de 1 a 19:

`XP_próximo(L) = 100 + 40 × (L−1) + 10 × (L−1)²`.

Exemplos: 1→2 = 100; 5→6 = 420; 10→11 = 1.270; 19→20 = 4.060. XP excedente atravessa vários níveis sem se perder. Ao chegar ao limite da versão, manter registro de XP total e informar como o excedente será tratado.

Meta inicial de ritmo: níveis 1–5 em aproximadamente 1–2 horas, 6–10 em mais 3–5 horas; medir com jogadores e ajustar. Essa meta não está comprovada pela fórmula. Recompensas e duração das atividades precisam ser ajustadas juntas.

Recompensas como frações do custo do nível recomendado da missão, fixadas na criação/aceitação para impedir manipulação:

- Objetivo curto: 10–15%.
- Missão secundária substancial: 20–30%.
- Marco principal: 35–50%.
- Primeiro chefe da região: 40–60%, junto com desbloqueio relevante.

Separar a recompensa da missão da recompensa do chefe para não pagar o mesmo marco duas vezes. Inimigos comuns complementam o avanço; a campanha não deve exigir repetição obrigatória de uma única atividade.

Cada nível oferece crescimento moderado e pontos de escolha. Desbloqueios maiores vêm de marcos e competências. Não multiplicar vida, dano, defesa e regeneração exponencialmente ao mesmo tempo. Não conceder manifestação ou transformação da manopla por nível sem decisão narrativa.

Profissões ganham experiência por resultados úteis e desafios apropriados. Evitar premiar repetição ilimitada de fabricar/desmontar o mesmo item ou plantar a semente gratuita de teste. Progressão de agricultura não deve depender apenas de esperar um ciclo anual simulado.

## 6. Missões conforme a evolução

Uma missão só é oferecida quando seus pré-requisitos forem atendidos: modo, marcos anteriores, região, competência, ferramentas e estado do mundo. Nível é uma informação adicional, não substitui esses requisitos.

| Faixa de aventura proposta | Objetivo de aprendizagem | Missões e fechamento |
|---|---|---|
| 1–3 | Movimento, interação e sobrevivência básica | Explorar local seguro, coletar recurso comum, entregar uma encomenda; recompensa com ferramenta básica |
| 4–6 | Equipamento, recurso de combate e esquiva | Preparar consumível, praticar aviso/ataque, realizar tarefa externa curta; minichefe opcional |
| 7–10 | Preparação de dungeon e leitura de padrões | Investigar acesso, aprender os três padrões em situações simples, preparar equipamento; primeiro chefe |
| 11–15 | Escolhas de especialização e problemas do mundo | Rotas por profissão, exploração ou combate; dungeon com duas fases mais elaboradas |
| 16–20 | Combinar competências e assumir desafios opcionais | Cadeias de região, chefes de três fases e desafios de domínio; sem exigir automaticamente todo elemento |

Estas faixas organizam o protótipo, não fixam capítulos da obra. História conserva sua sequência autoral; Exploração Livre oferece alternativas de profissão e não força todo jogador a caçar ou matar chefes.

Progressão sugerida de uma cadeia: aprender uma ação → aplicá-la com baixo risco → combiná-la com outra → enfrentar o chefe que exige essa combinação. Após uma derrota, oferecer uma dica contextual ou tarefa opcional de preparação, sem tirar a missão principal nem inflar o chefe.

O quadro de missões pode manter até três sugestões relevantes: principal, secundária e profissional. O diário conserva as aceitas. Mostrar nível recomendado, risco, ferramentas necessárias e recompensa antes de aceitar.

Se uma planta necessária morrer, oferecer replantio, outra fonte ou objetivo alternativo. Não prender a história a um recurso finito, a um NPC que se tornou inacessível ou a uma estação distante. Missões ecológicas podem aproveitar umidade, germinação e dispersão já presentes, mas coleta/inventário/recompensas ainda precisam ser conectados ao runtime.

### Modelo de missão proposto

Campos: `id`, `version`, `mode`, `prerequisites`, `recommended_level`, `required_capabilities`, `objectives`, `rewards`, `repeat_policy`, `failure_policy`, `world_effects` e `content_version`.

Estados: indisponível, disponível, aceita, em andamento, pronta para entrega, concluída e falha recuperável. Objetivos são atualizados por eventos confirmados: `item_collected`, `recipe_crafted`, `region_entered`, `boss_defeated` e equivalentes. Cada evento tem identidade para impedir contagem duplicada. Recompensa é aplicada uma única vez, com conclusão e concessão registradas de forma consistente.

## 7. Cooperação e MOBA

Coop ainda é futuro. A redução fixa de 30% no dano do convidado é apenas uma proposta antiga e não resolve qualquer diferença de nível.

Quando o solo estiver estável, testar um perfil específico para dois participantes. Ponto inicial experimental: vida ×1,6–1,8, com dano do chefe próximo ao solo; medir conforme dano real da dupla e habilidades de suporte. Travar o perfil no começo. Não dobrar simultaneamente vida e dano.

Para convidados muito fortes, oferecer sincronização de atributos para a faixa da atividade, preservando habilidades autorizadas e explicando a regra. Sem sincronização, o jogador pode optar por uma sessão livre de ajuda. Entrada/saída não pode curar o chefe nem duplicar recompensa. Cada mundo recebe somente os resultados previstos pela política da missão; não copiar o progresso inteiro do anfitrião.

No MOBA, chefe é objetivo estratégico com recompensa de partida e janela curta de exposição. Não reutilizar automaticamente o chefe longo de campanha. Progressão permanente do perfil deve liberar opções/cosméticos/conveniência, sem começar partidas com HP/ATK superiores aos dos outros jogadores.

## 8. Implementação por fatias, WIP = 1

1. **Runtime de combate solo:** dano, alcance, acerto por execução, invulnerabilidade de transição, morte e reinício. Uma arena e uma ficha de personagem de referência.
2. **Primeiro chefe:** três ataques, duas fases, telemetria de tentativas e nenhuma dependência de rede. Validar antes de criar vários chefes.
3. **Progressão 1–5 e uma cadeia curta:** XP, excesso entre níveis, equipamentos, recompensa única e save. Expandir para 20 depois de medir ritmo.
4. **Autoria no Creator:** extensão versionada de definições de encontros, missões e progressão; referências estáveis a assets, itens e regiões; validação de ciclos e referências ausentes. Reutilizar biblioteca/inventário existentes.
5. **Importação/exportação:** consumidor Godot real, mensagens para conteúdo incompatível, migração de saves com backup e preservação de zero/valores válidos. Não presumir que PNG/JSON exportado já implementa gameplay.
6. **Expansão de conteúdo:** novas missões/chefes, profissões, domínio e, posteriormente, coop. Validação Android físico em etapa própria.

Contratos sugeridos: `apoena.encounters.v1`, `apoena.quests.v1`, `apoena.progression.v1`. São nomes propostos, ainda não presentes como integração comprovada. Editor descreve; runtime executa. Lógica visual, scripts de combate e dados ficam separados para reduzir divergência HTML/Godot.

## 9. Critérios de validação

- Build mínimo vence o chefe com ataque básico e respostas acessíveis; nenhum requisito essencial fica depois do próprio chefe.
- Builds físicas, elementais e de suporte previstas são avaliadas; imunidades não geram bloqueio absoluto.
- Duração, dano recebido por padrão, causa de morte, recurso restante e progresso por fase são registrados por tentativa.
- Validar DPS baixo/médio/alto, resistência alta, ausência de consumível e repetição de cura/controle; comparar com a ficha de referência.
- Verificar saída alcançável de cada área em arena real, câmera mobile e velocidade mínima permitida.
- Testar apenas um dano por golpe previsto; múltiplos projéteis, dano contínuo e controle têm políticas próprias.
- XP e recompensa não duplicam após reconexão/recarregamento; conclusão continua íntegra após falha de save.
- Save/reabertura conserva nível, XP excedente, missões, profissão e desbloqueios; save anterior não é apagado.
- Testes automatizados verificam regras; testes com jogadores medem justiça, clareza e ritmo. Uma simulação numérica sozinha não comprova diversão nem dificuldade adequada.

## 10. Recomendação

Começar por **um chefe vencível, níveis 1–5 e uma cadeia de missões de preparação** no Pixel Art. Usar os resultados para consolidar o contrato de autoria no Creator e só então multiplicar chefes e regiões. Preservar as trilhas independentes de profissão/domínio e o MOBA temporário 0–20. O principal problema atual é construir e medir o ciclo de combate e evolução; ainda não existe evidência para atribuir a dificuldade a um chefe já implementado nesse runtime.
