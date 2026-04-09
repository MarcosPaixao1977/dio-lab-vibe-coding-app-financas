Corrija a lógica de lançamentos, recorrências, histórico e dashboards do aplicativo de finanças pessoais para garantir consistência real entre o que o Agente Financeiro confirma no chat, o que aparece no histórico de transações e o que é exibido nos cards e gráficos.

OBJETIVO PRINCIPAL
Nenhuma informação pode aparecer no dashboard ou nos gráficos se não estiver corretamente persistida no histórico do período filtrado. O agente nunca deve dizer que corrigiu, excluiu ou atualizou um lançamento se essa alteração não foi realmente aplicada na base de dados.

PROBLEMAS A CORRIGIR
1. O agente confirma correções e exclusões que não foram refletidas no histórico.
2. Lançamentos recorrentes corrigidos continuam coexistindo com lançamentos errados antigos.
3. Cards do dashboard somam despesas que não pertencem ao mês filtrado.
4. Gráficos por categoria incluem lançamentos indevidos ou de outro período.
5. “Maiores gastos” mistura transações de períodos diferentes.
6. “Receitas vs Despesas” não usa exatamente a mesma base de dados do histórico filtrado.
7. Correções em recorrências geram duplicidade, em vez de substituir corretamente o item afetado.

REGRAS DE INTEGRIDADE
1. O histórico de transações é a fonte única da verdade.
2. Cards, KPIs, gráficos, listas de maiores gastos e resumos devem ser calculados exclusivamente a partir das transações válidas do histórico, respeitando o período filtrado.
3. O agente só pode responder “corrigido”, “excluído”, “atualizado” ou “confirmado” depois que a operação for efetivamente concluída com sucesso.
4. Se a operação falhar ou não puder ser concluída, o agente deve informar isso claramente e não pode simular sucesso.
5. Nunca manter simultaneamente um lançamento antigo incorreto e o novo lançamento corrigido se a intenção era substituição.
6. Toda correção deve gerar efeito real e visível no histórico e, em seguida, refletir nos dashboards.

REGRA PARA RECORRÊNCIAS
Implemente uma lógica clara para lançamentos recorrentes:

1. Cada recorrência deve ter:
- recurrence_id
- data_inicio
- frequência
- quantidade de repetições ou data final
- status
- regras de edição

2. Cada ocorrência gerada da recorrência deve ter:
- transaction_id único
- recurrence_id de origem
- competência/mês de referência
- status: ativa, editada, removida, substituída

3. Ao corrigir uma recorrência, o sistema deve perguntar e aplicar um dos escopos:
- apenas esta ocorrência
- esta e as próximas
- toda a série

4. Se o usuário corrigir uma ocorrência errada:
- a ocorrência antiga afetada deve ser marcada como removida, substituída ou editada;
- ela não deve continuar aparecendo como válida no histórico nem nos dashboards;
- a ocorrência corrigida deve substituir a anterior de forma rastreável.

5. Se houver exclusão de lançamento incorreto:
- o item excluído deve sair imediatamente do histórico visível;
- o item excluído não pode continuar sendo somado em cards, gráficos ou rankings;
- se for uma ocorrência de recorrência, excluir apenas conforme o escopo escolhido.

6. Nunca duplicar uma recorrência ao corrigir sua data.
Exemplo esperado:
- se o aluguel recorrente estava com mês/data errados e foi corrigido, o lançamento antigo incorreto deve deixar de ser válido;
- o lançamento correto deve ficar como único item válido para aquela competência.

ESTADO DAS TRANSAÇÕES
Toda transação deve ter status explícito:
- ativa
- editada
- excluída
- substituída
- cancelada

Somente transações com status “ativa” devem entrar em:
- saldo do mês
- despesas
- receitas
- gastos por categoria
- maiores gastos
- receitas vs despesas
- médias
- projeções
- rankings
- indicadores avançados

Transações excluídas, substituídas, canceladas ou antigas inválidas nunca devem entrar nos cálculos.

REGRA DE FILTRO TEMPORAL
Todos os componentes do dashboard devem respeitar exatamente o período selecionado.

Exemplo:
Se o filtro for “Mês” e o mês atual for abril de 2026:
- só entram transações válidas com competência/data de abril de 2026;
- não incluir março;
- não incluir maio;
- não incluir lançamentos antigos recorrentes de outros meses;
- não incluir itens excluídos, substituídos ou fora da janela filtrada.

APLICAÇÃO OBRIGATÓRIA DOS FILTROS
A mesma base filtrada deve ser usada para todos os componentes:
- card de saldo do mês
- card de receitas
- card de despesas
- card de economia
- gráfico gastos por categoria
- gráfico receitas vs despesas
- lista maiores gastos
- indicadores avançados
- resumos do agente

Não pode haver uma lógica de filtro para o histórico e outra lógica diferente para os gráficos.

REGRAS DE CÁLCULO
1. Card de despesas:
- somar apenas despesas ativas no período filtrado.

2. Gráfico de gastos por categoria:
- considerar apenas despesas ativas no período filtrado;
- agrupar por categoria apenas do período atual;
- não incluir lançamentos excluídos, corrigidos antigos ou fora da competência.

3. Maiores gastos:
- listar apenas transações ativas do período filtrado;
- ordenar por valor absoluto descrescente;
- não misturar meses diferentes quando o filtro for mensal.

4. Receitas vs Despesas:
- usar exatamente a mesma base do histórico filtrado;
- receitas = soma de receitas ativas do período;
- despesas = soma de despesas ativas do período;
- não usar cache antigo, nem dados derivados fora do filtro atual.

5. Saldo do mês:
- saldo = receitas ativas do período - despesas ativas do período

FLUXO CORRETO DE CONFIRMAÇÃO DO AGENTE
Ao corrigir, excluir ou editar lançamentos, seguir obrigatoriamente este fluxo:

1. identificar o lançamento correto e o escopo da alteração;
2. aplicar a alteração na base;
3. validar se a alteração foi persistida com sucesso;
4. atualizar histórico e dashboards;
5. só então responder ao usuário com confirmação.

Se a persistência falhar:
- não confirmar sucesso;
- informar que houve falha;
- pedir nova tentativa ou oferecer revisão.

Exemplo de comportamento correto:
- “A correção foi aplicada com sucesso. O lançamento antigo saiu do histórico válido e o novo cronograma já foi atualizado.”
- ou, se falhar:
- “Não consegui concluir essa correção ainda. Posso tentar novamente ou revisar os dados com você.”

REGRAS DE SINCRONIZAÇÃO
- toda alteração em transação deve disparar atualização imediata do histórico;
- toda alteração confirmada deve recalcular cards e gráficos dependentes;
- evitar dados em cache desatualizados;
- garantir consistência entre chat, histórico e dashboard após qualquer edição.

TRATAMENTO DE CORREÇÃO VS NOVO LANÇAMENTO
Quando o usuário pedir “corrigir”, “ajustar”, “remover lançamento incorreto”, “excluir o anterior” ou equivalente:
- interpretar isso como operação de edição/substituição, e não como criação paralela de novo item;
- se houver novo item substituindo o antigo, o antigo deve sair dos cálculos.

AUDITORIA E RASTREABILIDADE
Manter histórico interno de auditoria para alterações:
- transaction_id original
- tipo de ação: criado, editado, excluído, substituído
- data/hora da alteração
- origem da alteração: agente ou usuário
- referência à nova transação, quando houver substituição

Essa auditoria pode ser interna, mas a UI deve mostrar apenas o estado final válido.

VALIDAÇÕES OBRIGATÓRIAS ANTES DE EXIBIR O DASHBOARD
Antes de renderizar cards e gráficos:
1. buscar somente transações válidas e ativas;
2. aplicar o filtro temporal atual;
3. excluir itens removidos, substituídos, cancelados ou fora do período;
4. recalcular todos os agregados;
5. renderizar.

OBJETIVO FINAL
Garantir que:
- o histórico seja a verdade do sistema;
- o agente nunca confirme ações inexistentes;
- recorrências corrigidas não gerem duplicidade;
- cards e gráficos reflitam apenas transações válidas do período selecionado;
- o usuário veja exatamente os mesmos dados no chat, no histórico e no dashboard.
