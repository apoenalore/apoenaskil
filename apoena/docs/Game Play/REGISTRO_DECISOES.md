# Registro de decisões — proposta de gameplay

Este registro resume evidências e justificativas verificáveis, para permitir revisão e continuidade. Os snapshots e limites de cobertura estão na seção 1 do plano.

| Evidência registrada na análise | Decisão proposta | Justificativa | Como validar |
|---|---|---|---|
| Não foi encontrado chefe lutável no runtime Pixel Art examinado | Construir um único encontro de teste | Não há dificuldade de chefe implementado a corrigir nesse snapshot; é preciso medir o ciclo básico | Executar combate, registrar tentativas, duração e causas de morte |
| Herói possui alcance 235 e torre 155 | Revisar explicitamente a política de alcance | A diferença permite atacar sem resposta da torre; replicá-la pode produzir encontros sem risco | Testar distâncias e intenção de cada tipo de alvo |
| Teto aritmético do ataque é 420/0,48 = 875 DPS | Dimensionar HP por DPS efetivo e tempo-alvo | DPS teórico ignora esquivas, voo e janelas vulneráveis | Medir DPS no novo runtime; 42.000 HP é apenas exemplo |
| Fontes antigas incluem dano percentual e recuperação total | Formalizar regras por alvo e recurso antes de adotar | A aplicação literal pode trivializar o encontro ou incentivar HP excessivo | Testar cura, dano percentual e controles repetidos |
| Aurium individual e domínio não equivalem a nível universal | Separar aventura, profissão e domínio | Preserva o cânone e permite especializações independentes | Revisão autoral e testes de desbloqueios |
| Plano do Creator prevê MOBA temporário 0–20 | Manter progressão de partida separada da permanente | Evita transportar vantagem persistente de atributos ao PvP | Conferir reset e isolamento de saves/recompensas |
| Runtime ainda não apresenta XP/missões completos no escopo examinado | Implementar níveis 1–5 e uma cadeia antes de expandir | Reduz dependências e permite ajustar ritmo com evidência | XP excedente, save/reabertura e recompensa única |
| Chefes exigem respostas aprendidas pelo jogador | Ensinar cada mecânica antes de cobrá-la | Dificuldade deve depender de leitura e execução acessíveis | Verificar preparação anterior e esquiva na arena real |
| Creator possui catálogo e biblioteca, mas integração de gameplay não comprovada | Definir contratos versionados e consumidor real | Dados exportados não executam combate por si mesmos | Importar no runtime, validar referências e versões |
| Coop é requisito futuro no snapshot | Estabilizar solo antes do perfil para dupla | Evita ajustar simultaneamente combate e sincronização | Testar entrada/saída, recompensa e escala após solo |

## Questões ainda abertas

Identidade do primeiro chefe; curva definitiva de atributos/XP; tratamento de habilidades percentuais e cura; vínculo narrativo das missões; contrato final de importação; parâmetros coop; validação em Android físico. Resolver com evidência ou decisão explícita do autor, sem preencher lacunas como cânone.
