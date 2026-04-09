Crie uma experiência visual e funcional para investimentos dentro do aplicativo de finanças pessoais, integrada ao histórico, dashboard e área de análise.

OBJETIVO
Fazer com que investimentos sejam fáceis de registrar, identificar, acompanhar e analisar, sem misturá-los com despesas comuns.

PRINCÍPIO DE UX
Cada investimento deve ser tratado como um item identificável, com nome próprio e histórico próprio.

Exemplos:
- Tesouro Selic 2029
- CDB Banco X
- Fundo ABC
- Reserva de Emergência XP

TELAS E ÁREAS
Adicionar:
1. seção de investimentos no dashboard
2. filtros de investimento no histórico
3. cards e gráficos de investimentos
4. fluxo para registrar aporte, resgate e rendimento
5. visão consolidada por investimento e por categoria
6. detalhamento individual de cada investimento

VISÃO POR INVESTIMENTO
Cada investimento deve ter uma visualização própria com:
- nome do investimento
- categoria
- instituição
- valor investido atual
- total aportado
- total resgatado
- total de ganhos
- histórico de movimentações
- status

HISTÓRICO
No histórico, mostrar investimentos junto com receitas e despesas, com filtro específico.
Cada item de investimento deve indicar:
- nome do investimento
- subtipo: aporte, resgate ou rendimento
- categoria
- data
- valor
- investimento relacionado

KPIs DE INVESTIMENTOS
Exibir:
- total investido
- saldo investido atual
- aportes no período
- resgates no período
- ganhos no período
- ganhos acumulados
- número de investimentos ativos
- investimento com maior saldo
- investimento com maior ganho

GRÁFICOS OBRIGATÓRIOS
1. gráfico de investimentos por categoria no filtro atual
2. gráfico de investimentos por categoria em todos os tempos
3. gráfico de evolução dos investimentos
4. gráfico de rendimentos por período
5. gráfico de resgates por período
6. gráfico por investimento individual
7. gráfico de distribuição da carteira por investimento

REGISTRO DE APORTE
Fluxo:
- usuário escolhe investimento existente ou cria novo
- informa valor
- registra aporte
- sistema vincula ao investimento correto
- atualiza histórico, KPIs e gráficos

REGISTRO DE RESGATE
Fluxo:
- usuário escolhe investimento
- informa valor
- sistema valida saldo disponível
- reduz saldo investido
- aumenta caixa
- atualiza histórico, KPIs e gráficos

REGISTRO DE RENDIMENTO
Fluxo:
- usuário escolhe investimento
- informa valor do ganho
- sistema vincula ao investimento correto
- atualiza saldo investido, KPI de ganhos e gráficos

COMPORTAMENTO DO AGENTE
Sempre identificar a qual investimento o usuário está se referindo.
Se houver mais de um investimento e o usuário não especificar:
- perguntar qual investimento deve ser usado
- não assumir automaticamente

Exemplo:
“Você quer registrar esse rendimento em qual investimento?”

VISUAL
- investimentos devem ter visual próprio
- não usar aparência de despesa para aporte
- resgate deve ter identidade visual diferente de receita comum
- rendimento deve parecer ganho de investimento, não salário
- manter estilo mobile-first, limpo e elegante

OBJETIVO FINAL
Fazer com que o usuário consiga identificar claramente cada investimento, registrar várias movimentações no mesmo investimento e acompanhar aportes, resgates e ganhos com clareza e consistência.
