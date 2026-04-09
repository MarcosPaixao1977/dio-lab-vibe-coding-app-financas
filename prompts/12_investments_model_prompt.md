Implemente um modelo completo para tratar investimentos no aplicativo de finanças pessoais como uma terceira natureza financeira, separada de receitas e despesas.

OBJETIVO
Tratar investimento não como despesa comum, mas como movimentação patrimonial própria, com regras, histórico, identificação clara do investimento, aportes, resgates, ganhos, KPIs e gráficos.

PRINCÍPIO CENTRAL
Investimento não é receita e não é despesa operacional.
Investimento representa alocação de patrimônio.

Cada investimento precisa ter uma identidade própria para permitir:
- múltiplos aportes no mesmo investimento;
- registro de rendimentos/ganhos no investimento correto;
- resgates vinculados ao investimento correto;
- histórico consolidado por investimento;
- saldo acumulado por investimento.

REGRA DE NATUREZA FINANCEIRA
O sistema deve suportar pelo menos 3 naturezas principais de movimentação:
1. receita
2. despesa
3. investimento

Dentro de investimento, suportar subtipos:
- aporte
- resgate
- rendimento/juros
- taxa/custo do investimento

IDENTIFICAÇÃO DO INVESTIMENTO
Todo investimento deve possuir uma entidade principal própria, com identificador único e nome claro.

Campos mínimos obrigatórios da entidade de investimento:
- investment_id
- nome_investimento
- identificador_unico
- categoria_investimento
- instituicao
- objetivo
- moeda
- status
- valor_investido_atual
- valor_aportado_total
- valor_resgatado_total
- valor_rendimento_total
- created_at
- updated_at

EXEMPLOS DE NOME/IDENTIFICAÇÃO
- Tesouro Selic 2029
- CDB Banco X
- Reserva Nubank
- Fundo Imobiliário ABC
- Carteira Ações Brasil
- Cripto BTC
- Previdência XP

REGRA DE IDENTIFICAÇÃO
- O nome do investimento deve ser obrigatório.
- Cada aporte, resgate ou rendimento deve estar vinculado a um investment_id existente.
- O agente nunca deve registrar aporte, ganho ou resgate sem identificar a qual investimento a movimentação pertence.
- Se houver ambiguidade, o agente deve perguntar qual investimento deve ser usado.

Exemplo:
“Você quer registrar esse aporte em qual investimento: Tesouro Selic 2029 ou CDB Banco X?”

MODELO DE MOVIMENTAÇÕES DE INVESTIMENTO
Criar movimentações de investimento com:
- transaction_id
- natureza: investimento
- subtipo: aporte, resgate, rendimento, taxa
- investment_id
- nome_investimento
- descricao
- categoria_investimento
- valor
- data
- status
- origem
- observacao

CATEGORIAS DE INVESTIMENTO
Adicionar categorias de investimento como:
- tesouro direto
- renda fixa
- CDB
- LCI/LCA
- ações
- fundos
- previdência
- cripto
- caixa investido
- outros investimentos

REGRA DE IMPACTO FINANCEIRO
1. Receita:
- aumenta caixa/entrada

2. Despesa:
- reduz caixa/saída operacional

3. Investimento / Aporte:
- reduz caixa disponível no momento do aporte
- não deve ser tratado como despesa de consumo
- deve aumentar o saldo do investimento identificado

4. Resgate:
- reduz saldo do investimento identificado
- aumenta caixa disponível
- não deve ser tratado como receita operacional comum

5. Rendimento/Juros:
- aumenta o saldo do investimento identificado ou o ganho acumulado do investimento
- deve ficar separado de salário, renda operacional e receitas comuns
- deve alimentar KPI de ganhos

REGRA DE CONSISTÊNCIA POR INVESTIMENTO
Cada investimento deve manter consolidados:
- total de aportes
- total de resgates
- total de rendimentos
- saldo investido atual
- histórico de movimentações

FÓRMULA RECOMENDADA
valor_investido_atual =
  valor_aportado_total
  + valor_rendimento_total
  - valor_resgatado_total
  - taxas, se houver

REGISTRO DE APORTE
Permitir registrar aporte:
- selecionar investimento existente ou criar novo investimento
- informar valor
- informar data
- vincular ao investment_id
- reduzir caixa disponível
- aumentar saldo investido do investimento

REGISTRO DE RESGATE
Permitir resgate:
- selecionar investimento existente
- informar valor do resgate
- validar que o valor não excede o saldo do investimento
- reduzir saldo investido
- aumentar caixa disponível
- registrar com subtipo “resgate”

REGISTRO DE GANHOS / JUROS
Permitir registrar rendimento:
- selecionar investimento existente
- informar valor do rendimento
- informar data
- aumentar valor_rendimento_total
- atualizar saldo investido atual
- alimentar KPI de ganhos

REGRAS PARA O AGENTE FINANCEIRO
O agente deve entender comandos como:
- criar investimento chamado Tesouro Selic
- registrar aporte de 1000 no Tesouro Selic
- registrar rendimento de 120 no Tesouro Selic
- resgatar 500 do Tesouro Selic
- mostrar meus investimentos
- mostrar ganhos do Tesouro Selic
- analisar meus investimentos

Se o usuário disser apenas:
- “aplicar 1000”
- “resgatar 500”
- “registrar rendimento de 80”

e houver mais de um investimento cadastrado, o agente deve perguntar:
- em qual investimento?
- nunca assumir automaticamente se houver ambiguidade

PÁGINA DE HISTÓRICO
A tela de histórico deve mostrar também investimentos.
Permitir filtros por:
- todos
- receitas
- despesas
- investimentos

Cada item de investimento deve mostrar:
- nome do investimento
- subtipo: aporte, resgate ou rendimento
- categoria do investimento
- data
- valor
- descrição opcional

TOTALIZADORES NO HISTÓRICO
Quando o filtro incluir investimentos, mostrar:
- total de receitas
- total de despesas
- total aportado
- total resgatado
- total de ganhos
- saldo líquido do período

DASHBOARD E KPIs DE INVESTIMENTO
Criar KPIs específicos:
- total investido
- valor atual investido
- total aportado no período
- total resgatado no período
- ganhos/rendimentos acumulados
- rendimento do período
- quantidade de investimentos ativos
- melhor investimento por saldo atual
- melhor investimento por ganhos

GRÁFICOS DE INVESTIMENTO
Criar gráficos:
1. investimentos por categoria no período filtrado
2. investimentos por categoria em todos os tempos
3. evolução dos aportes ao longo do tempo
4. evolução do valor investido total
5. rendimentos por período
6. resgates por período
7. composição por investimento individual

TRATAMENTO NOS CARDS GERAIS
No dashboard geral:
- não somar aportes como despesa operacional;
- separar despesas de consumo de aportes;
- destacar total investido e ganhos;
- se houver patrimônio total, incluir investimentos;
- se houver caixa disponível, aporte reduz caixa e resgate aumenta caixa

OBJETIVO FINAL
Tratar investimentos como uma camada financeira própria, com identificação individual por investimento, permitindo múltiplos aportes, rendimentos e resgates no mesmo ativo/aplicação, sem misturar isso com despesas comuns.
