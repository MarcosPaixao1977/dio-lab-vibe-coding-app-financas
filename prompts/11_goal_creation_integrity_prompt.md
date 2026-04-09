Corrija a lógica de criação de metas no aplicativo de finanças pessoais para garantir que o Agente Financeiro nunca confirme a criação de uma meta sem que ela tenha sido realmente persistida na base de dados e refletida na interface.

OBJETIVO
Garantir que toda meta:
- seja criada de verdade antes da confirmação ao usuário;
- apareça imediatamente na área de metas, dashboard e demais componentes relacionados;
- possa receber aportes, progresso e acompanhamento sem inconsistência.

PROBLEMA A CORRIGIR
Hoje o agente informa mensagens como “Meta criada com sucesso”, mas a meta não é efetivamente criada nem exibida no sistema. Isso gera falsa confirmação e quebra de confiança.

REGRA PRINCIPAL
O agente só pode dizer que uma meta foi criada depois que:
1. os dados da meta forem validados;
2. a meta for persistida com sucesso;
3. a meta puder ser consultada na base;
4. a interface for atualizada com a nova meta.

Se qualquer etapa falhar:
- não confirmar sucesso;
- informar claramente que não foi possível concluir;
- oferecer nova tentativa ou revisão.

CAMPOS MÍNIMOS DE UMA META
Toda meta deve possuir pelo menos:
- goal_id
- nome
- tipo_objetivo
- valor_alvo
- valor_atual
- prazo ou duração, se houver
- status: ativa, concluida, pausada, cancelada
- categoria_objetivo, se aplicável
- created_at
- updated_at

EXEMPLOS DE META
- reserva de emergência
- viagem
- quitar dívida
- investir no Tesouro Direto
- comprar algo específico

FLUXO OBRIGATÓRIO DE CRIAÇÃO DE META
1. identificar intenção de criar meta;
2. coletar os dados mínimos;
3. validar se nome e valor-alvo existem;
4. persistir a meta na base;
5. verificar retorno de sucesso com goal_id válido;
6. atualizar lista de metas, dashboard e indicadores relacionados;
7. só então confirmar ao usuário.

EXEMPLO DE CONFIRMAÇÃO CORRETA
“Pronto. Sua meta foi criada com sucesso e já aparece na área de metas.”

EXEMPLO DE FALHA CORRETA
“Não consegui concluir a criação da meta agora. Posso tentar novamente com você.”

REGRAS DE CONSISTÊNCIA
- a meta criada deve aparecer imediatamente na tela de metas;
- se houver dashboard com metas, ele deve ser atualizado;
- se a meta for usada em gráficos, rankings ou indicadores, os dados devem ser recalculados;
- o agente nunca deve sugerir aporte inicial para uma meta inexistente.

APORTE EM META
Só oferecer registrar aporte se:
- a meta já existir de fato;
- a meta estiver ativa;
- houver goal_id válido.

Se não houver meta persistida:
- não oferecer aporte;
- primeiro concluir a criação.

AUDITORIA
Registrar internamente:
- tipo de ação: criar meta
- goal_id
- dados criados
- data/hora
- origem da ação: agente ou usuário
- status da operação

VALIDAÇÃO FINAL
Antes de responder “meta criada com sucesso”, validar:
- a meta existe na base?
- possui goal_id?
- aparece na lista de metas?
- está disponível para receber aporte?

OBJETIVO FINAL
Eliminar falsas confirmações de criação de meta e garantir que toda meta anunciada pelo agente exista de verdade, esteja persistida e visível no sistema.
