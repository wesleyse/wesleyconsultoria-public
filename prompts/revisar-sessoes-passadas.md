# Faça seu agente revisar as próprias sessões passadas

Funciona com Claude Code, Codex, Cursor ou qualquer agente de código que consiga ler o próprio histórico. Adapte a lista de "evidências" ao que o seu agente tem acesso.

---

Revise meu trabalho recente dos últimos 30 dias, ou todo o histórico disponível se for mais curto, e identifique fluxos de trabalho manuais repetidos que valham a pena empacotar.

Use as evidências disponíveis nesta ordem:
1. Sessões recentes, transcrições e resumos de tarefas deste agente.
2. Arquivos de memória e resumos de conversas, para encontrar padrões repetidos entre sessões.
3. Skills existentes, agentes customizados, arquivos de regras (CLAUDE.md / AGENTS.md) e automações, para reaproveitar ou estender o que já existe em vez de duplicar.

Procure de forma ampla por trabalho repetido, demorado, propenso a erro, pesado em contexto, ou que se beneficie de um processo consistente. Inclua fluxos de código, pesquisa, escrita, planejamento, comunicação, operações, análise e administração pessoal.

Só aja sobre um candidato quando ele:
- ocorreu pelo menos duas vezes, ou claramente tende a se repetir e custa caro repetir;
- tem entradas estáveis, um procedimento repetível e uma saída ou condição de parada clara;
- melhoraria de forma significativa a velocidade, qualidade, consistência ou confiabilidade;
- ainda não está adequadamente coberto.

Escolha a menor forma adequada:
- Regra: uma instrução curta adicionada ao CLAUDE.md / AGENTS.md.
- Skill: um fluxo de trabalho ou playbook reutilizável.
- Subagente customizado: um papel especialista delimitado, ou tarefa de investigação adequada para delegação.
- Automação: uma checagem, relatório, lembrete ou monitor agendado ou recorrente.
- Pular: trabalho pontual demais, ambíguo, sensível ou com pouca evidência para empacotar.

Primeiro produza uma shortlist compacta com:
- fluxo de trabalho repetido
- evidências e datas
- frequência/confiança
- forma recomendada: regra, skill, subagente, automação, estender existente, ou pular
- por que vale ou não vale a pena criar

Depois crie apenas os itens faltantes de alta confiança. Mantenha-os enxutos, práticos, fiéis às fontes e fáceis de validar. Não crie ativos especulativos, sobrepostos ou amplos demais.

Finalize com:
- o que você criou ou estendeu
- o que você deliberadamente pulou
- o que precisa de mais evidência antes de empacotar
