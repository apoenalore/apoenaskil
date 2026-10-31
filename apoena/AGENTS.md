# Instruções gerais para agentes — Apoena

## Regra prioritária de trabalho

**Primeiro recuperar e preservar tudo; depois organizar; em seguida auditar contradições; somente por último atualizar o cânone com o autor.** Não perder conhecimento para ganhar organização. Versões antigas, desatualizadas, incompletas, descartadas ou contraditórias devem permanecer acessíveis e identificadas. Nenhuma IA pode apagá-las ou substituí-las silenciosamente.

O modo padrão para importar conhecimento de conversas antigas, outras IAs, documentos ou repositórios é **MODO DE RECUPERAÇÃO INTEGRAL**. Leia obrigatoriamente:
- `docs/PROTOCOLO_UNIVERSAL_DE_EXTRACAO_E_TRANSFERENCIA.md`;
- `docs/MODOS_DE_TRABALHO_E_PRESERVACAO.md);
- `docs/source-and-status-legend.md`.

## Antes de qualquer tarefa

1. Leia `/AGENTS.md` na raiz do repositório e o README raiz.
2. Leia este arquivo.
3. Leia o protocolo universal e os modos de trabalho.
4. Consulte `docs/knowledge-recovery-2026-10-30.md), `docs/knowledge-gaps-and-contradictions.md), a legenda de status e os documentos pertinentes.
5. Leia a Skill adequada em `skills/`.
6. Preserve nomes, relações, regras, eventos e características estabelecidas.
7. Nunca transforme hipótese, sugestão ou lacuna em fato canônico.
8. Se fontes divergirem, preserve as versões, mostre a divergência e peça decisão ao autor.
9. Não altere elementos que o autor não pediu para alterar.
10. Em imagens/spritesheets, respeite quadros, enquadramento, transparência e itens que devem permanecer intactos.
11. Classifique informações como cânone confirmado, decisão do autor, recuperado a validar, implementação verificada/histórica, planejado, proposta, descartado ou desconhecido.
12. Sugestões só viram cânone após aprovação explícita.
13. Não confunda protótipos de jogo com cânone do mangá nem misture repositórios.
14. Não alegue recuperação integral se anexos, PDFs ou conversas estiverem inacessíveis ou não examinados.
15. Registre data e hora em novos registros, alterações, decisões, descobertas e relatórios. Use ISO 8601 com fuso quando confiável.
16. Diferencie a data/hora do evento original da data/hora do registro, quando ambas forem conhecidas.
17. Se a hora não estiver disponível, escreva “Hora não disponível na fonte”; não invente nem estime. Se data e hora forem desconhecidas, escreva “Data e hora não disponíveis na fonte”.
18. Se o sistema não fornecer relógio ou fuso confiável, informe a limitação em vez de fabricar timestamp.

## Skills — catálogo completo

### Cânone, cosmologia e lore
- `skills/apoena-primordial-cosmology/SKILL.md`
- `skills/apoena-tupi-anahi-early-earth/SKILL.md`
- `skills/apoena-canon-guardian/SKILL.md`
- `skills/apoena-worldbuilding/SKILL.md`
- `skills/apoena-dimensional-cosmology/SKILL.md`
- `skills/apoena-cave-of-waterfall-rite/SKILL.md`
- `skills/apoena-aurium-system/SKILL.md`
- `skills/apoena-constellations-and-blessings/SKILL.md`
- `skills/apoena-continuity-reviewer/SKILL.md`

### Narrativa e personagens
- `skills/apoena-scriptwriter/SKILL.md`
- `skills/apoena-character-designer/SKILL.md`
- `skills/apoena-character-canon/SKILL.md`

### Mundo, sociedade e ecologia
- `skills/apoena-agar-civilization/SKILL.md`
- `skills/apoena-agar-governance-and-defense/SKILL.md`
- `skills/apoena-human-perspective/SKILL.md`
- `skills/apoena-human-perspective-reviewer/SKILL.md`
- `skills/apoena-ecology-systems/SKILL.md`
- `skills/apoena-ancestral-beasts-and-artifacts/SKILL.md`

### Direção visual e produção de imagens
- `skills/apoena-art-director/SKILL.md`
- `skills/apoena-image-production/SKILL.md`
- `skills/apoena-visual-continuity/SKILL.md`

### Jogos e desenvolvimento
- `skills/apoena-game-systems/SKILL.md`
- `skills/apoena-gameplay-implementation/SKILL.md`
- `skills/apoena-progression-economy/SKILL.md`
- `skills/apoena-godot-prototyping/SKILL.md`
- `skills/apoena-project-architect/SKILL.md`

### Recuperação e produção
- `skills/apoena-knowledge-archivist/SKILL.md`
- `skills/apoena-studio-production/SKILL.md`
- `skills/apoena-spirit-dimension-and-cave-mentors/SKILL.md`

## Regras de escopo

- A perspectiva humana sem Aurium deve ser ativada quando o criador pedir essa lente; não é regra global automática.
- Não misture cânone do mangá, sistemas de jogo, protótipos, ferramentas e infraestrutura.
- Não atualize uma Skill apenas com base em resumo quando a conversa original estiver disponível.
- Cada registro derivado deve apontar para sua fonte e declarar se é literal, paráfrase, resumo ou interpretação.
- O índice de Skills é `skills/INDEX.txt`; mantenha-o sincronizado com os arquivos existentes.

## Preservação visual e de anexos

Em imagens, spritesheets, mapas, PDFs, áudio e vídeo, preserve a referência original, a localização e o estado de inspeção. Uma transcrição ou descrição não substitui o binário original. Se o binário não puder ser armazenado no repositório, registre a pendência sem alegar que foi copiado.

## Atualizações no GitHub

Antes de alterar:
1. identifique branch e commit;
2. inventarie arquivos existentes;
3. preserve registros anteriores;
4. faça alterações aditivas e rastreáveis;
5. atualize o índice e os documentos de controle afetados;
6. confira links e caminhos;
7. registre commit e validação.

**Princípio final:** preservar primeiro, organizar depois, comparar em seguida e atualizar com o autor por último.
