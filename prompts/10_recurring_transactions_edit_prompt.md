Implemente regras claras e seguras para edição, correção, exclusão e reprogramação de transações recorrentes no aplicativo de finanças pessoais.

OBJETIVO
Garantir que toda recorrência possa ser corrigida sem gerar duplicidade, inconsistência no histórico, erros no dashboard ou confirmações falsas no chat.

MODELO DE DADOS RECOMENDADO
Toda recorrência deve possuir uma entidade própria com estes campos mínimos:
- recurrence_id
- tipo_transacao: receita ou despesa
- descricao
- categoria
- valor
- forma_pagamento
- data_inicio
- frequencia: semanal, mensal, anual
- intervalo: ex. a cada 1 mês
- quantidade_ocorrencias ou data_fim
- status: ativa, pausada, encerrada, cancelada
- created_at
- updated_at

Cada ocorrência gerada pela recorrência deve possuir:
- transaction_id
- recurrence_id
- data_ocorrencia
- competencia
- valor
- categoria
- descricao
- forma_pagamento
- status: ativa, editada, excluida, substituida, cancelada
- override_local: true ou false
- replaced_by_transaction_id, se existir
- created_at
- updated_at

PRINCÍPIO CENTRAL
Recorrência é uma série. Ocorrência é um item da série.
Editar a série não é o mesmo que editar apenas uma ocorrência.
O sistema deve tratar isso de forma explícita.

ESCOPO OBRIGATÓRIO DE ALTERAÇÃO
Sempre que o usuário pedir edição, correção, exclusão ou reprogramação de uma recorrência, o sistema deve identificar e aplicar um destes escopos:

1. apenas esta ocorrência
2. esta ocorrência e as próximas
3. toda a série

Se houver ambiguidade, o agente deve perguntar qual escopo aplicar antes de executar.

Exemplo:
“Você quer corrigir apenas este aluguel, este e os próximos, ou toda a série?”

REGRAS PARA EDIÇÃO DE RECORRÊNCIA

CASO 1 — Editar apenas esta ocorrência
- não alterar a definição principal da recorrência;
- criar override local para a ocorrência específica;
- marcar a ocorrência original como editada ou substituída;
- manter as demais ocorrências futuras inalteradas;
- refletir apenas essa mudança no histórico e dashboard do período correspondente.

CASO 2 — Editar esta ocorrência e as próximas
- manter o histórico passado intacto;
- encerrar logicamente a série anterior até a ocorrência imediatamente anterior;
- criar nova configuração de recorrência a partir da data corrigida;
- marcar a ocorrência atual incorreta e futuras antigas afetadas como substituídas ou canceladas;
- garantir que apenas a nova sequência fique válida dali em diante.

CASO 3 — Editar toda a série
- atualizar a configuração da recorrência inteira;
- regenerar as ocorrências futuras ainda não consolidadas;
- manter rastreabilidade das ocorrências que foram substituídas;
- se houver ocorrências já realizadas e confirmadas no passado, não alterar retroativamente sem confirmação explícita.

REGRAS PARA EXCLUSÃO DE RECORRÊNCIA

CASO 1 — Excluir apenas esta ocorrência
- marcar somente a ocorrência selecionada como excluída;
- manter a recorrência principal ativa;
- não gerar novo item para aquela competência;
- remover essa ocorrência do histórico visível e dos cálculos.

CASO 2 — Excluir esta ocorrência e as próximas
- manter ocorrências passadas válidas;
- cancelar as ocorrências futuras a partir do ponto escolhido;
- atualizar a recorrência para que não gere novos lançamentos dali em diante;
- remover essas ocorrências futuras dos cálculos e visualizações.

CASO 3 — Excluir toda a série
- cancelar a recorrência principal;
- marcar todas as ocorrências futuras não consolidadas como canceladas ou excluídas;
- preservar histórico passado já realizado, salvo se o usuário pedir remoção retroativa explícita.

REGRAS DE CORREÇÃO DE DATA
Ao corrigir a data de uma recorrência:
- nunca criar uma nova ocorrência válida sem invalidar a antiga correspondente;
- a data antiga incorreta não pode continuar entrando no histórico e dashboards;
- a nova data passa a valer conforme o escopo escolhido;
- evitar coexistência de item antigo errado + item novo correto para a mesma intenção financeira.

Exemplo esperado:
Se um aluguel recorrente foi criado incorretamente para 03/05/2026 e o usuário corrigiu para 05/04/2026:
- o item antigo incorreto deve ser marcado como substituído ou excluído;
- o item correto deve ser o único ativo para a competência afetada;
- o dashboard do mês deve refletir somente a ocorrência válida.

REGRAS DE STATUS
Somente ocorrências com status “ativa” entram em:
- histórico visível padrão;
- cards do dashboard;
- gráficos;
- maiores gastos;
- receitas vs despesas;
- projeções;
- indicadores avançados.

Ocorrências com status:
- editada
- excluida
- substituida
- cancelada

não devem entrar em cálculos nem aparecer como válidas.

REGRAS DE PERSISTÊNCIA
O agente nunca deve confirmar:
- “corrigido”
- “excluído”
- “atualizado”
- “reagendado”

antes que a alteração tenha sido efetivamente persistida com sucesso.

Fluxo obrigatório:
1. identificar recorrência e ocorrência alvo;
2. identificar escopo;
3. aplicar alteração na base;
4. atualizar ocorrências derivadas;
5. recalcular histórico válido;
6. recalcular dashboards afetados;
7. só então confirmar ao usuário.

Se qualquer etapa falhar:
- não confirmar sucesso;
- informar falha com clareza;
- oferecer nova tentativa ou revisão.

REGRAS DE DASHBOARD APÓS EDIÇÃO
Após qualquer alteração em recorrência:
- atualizar imediatamente o histórico do período afetado;
- recalcular saldo, receitas, despesas e gráficos;
- garantir que itens antigos substituídos não continuem sendo somados;
- garantir que listas de maiores gastos e gráficos por categoria respeitem apenas as ocorrências válidas.

REGRA DE COMPETÊNCIA
Toda ocorrência recorrente deve ter competência clara, usada para filtros mensais e relatórios.
A competência deve ser consistente com a data efetiva da ocorrência válida.

REGRAS DE UX
Quando o usuário editar uma recorrência, mostrar de forma clara:
- qual item será alterado;
- qual escopo será afetado;
- qual item antigo deixará de valer, quando aplicável;
- qual será o novo cronograma.

Exemplo de confirmação antes de executar:
“Vou corrigir este aluguel de R$ 850,00 para o dia 05/04/2026 e aplicar essa mudança também aos próximos meses. O lançamento antigo incorreto deixará de contar no histórico válido. Posso confirmar?”

Exemplo de confirmação após sucesso:
“Pronto. A recorrência foi corrigida e o lançamento antigo incorreto deixou de valer. O histórico e os indicadores já foram atualizados.”

AUDITORIA INTERNA
Registrar internamente:
- recurrence_id
- transaction_id afetado
- tipo de ação
- escopo aplicado
- data/hora
- valor anterior
- valor novo
- data anterior
- data nova
- referência para ocorrência substituta, quando existir

OBJETIVO FINAL
Garantir que correções e exclusões de recorrências sejam confiáveis, rastreáveis e consistentes, sem duplicidade, sem lançamentos fantasmas e sem divergência entre chat, histórico e dashboard.
