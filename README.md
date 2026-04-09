# 💬 App de Finanças Pessoais Desenvolvido por Marcos Paixão com IA Conversacional para Bootcamp DIO

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-2ea44f)
![Lovable](https://img.shields.io/badge/build-Lovable-8b5cf6)
![IA](https://img.shields.io/badge/IA-agente%20financeiro-0ea5e9)
![Foco](https://img.shields.io/badge/foco-finanças%20pessoais-16a34a)
![Modo](https://img.shields.io/badge/abordagem-prompt--driven-f59e0b)

> Aplicativo de finanças pessoais com interface conversacional, construído com apoio do **Lovable** e orientado por prompts estruturados.

---

## 📌 Visão Geral

Este projeto consiste em um aplicativo de finanças pessoais com interface conversacional, criado com apoio do **Lovable** e orientado por prompts estruturados.

O objetivo do produto é permitir que o usuário organize sua vida financeira de forma simples, natural e prática, usando conversa com um **Agente Financeiro**, além de dashboards, histórico, metas, alertas e, posteriormente, uma camada de **investimentos**.

O desenvolvimento foi conduzido por etapas, com prompts específicos para arquitetura do produto, comportamento do agente, regras funcionais, consistência dos dados, recorrências, dashboards e correções de fluxo.

Link do Aplicativo: https://conversa-e-organiza.lovable.app
---

## 🚦 Status do Projeto

**Status atual:** Em desenvolvimento e evolução contínua

### O projeto já contempla
- estrutura principal do app;
- agente financeiro conversacional;
- histórico de transações;
- dashboards com KPIs e gráficos;
- metas financeiras;
- recorrências;
- filtros e totalizadores;
- correções de consistência de dados;
- evolução para investimentos.

### O projeto está evoluindo em frentes como
- tratamento mais robusto de investimentos;
- integridade entre histórico, cards e gráficos;
- refinamento de UX;
- ajustes finos em regras de negócio;
- melhorias na previsibilidade do agente.

---

## 🎯 Objetivo do Projeto

Criar um aplicativo mobile-first de finanças pessoais com foco em:

- registro de receitas e despesas em linguagem natural;
- categorização automática;
- metas financeiras;
- dashboards com KPIs e gráficos;
- histórico filtrável e editável;
- recorrências;
- alertas e insights;
- agente financeiro acolhedor e especializado;
- evolução futura para controle de investimentos.

---

## 🧰 Tecnologias e Abordagem

O projeto foi construído com apoio do **Lovable**, usando uma abordagem orientada por prompts.

Em vez de começar apenas por telas, a construção foi guiada por blocos de instrução que definiram:

- escopo do produto;
- comportamento do agente;
- regras funcionais;
- consistência de dados;
- lógica de recorrência;
- estrutura de dashboards;
- correção de erros de data;
- integridade na criação de metas;
- evolução para investimentos.

---

# 🗂️ Sumário

- [📌 Visão Geral](#-visão-geral)
- [🚦 Status do Projeto](#-status-do-projeto)
- [🎯 Objetivo do Projeto](#-objetivo-do-projeto)
- [🧰 Tecnologias e Abordagem](#-tecnologias-e-abordagem)
- [🖼️ Screenshots](#️-screenshots)
- [🧱 Estrutura de Prompts Utilizados](#-estrutura-de-prompts-utilizados)
  - [1. APP PROMPT](#1-app-prompt)
  - [2. AI AGENT PROMPT](#2-ai-agent-prompt)
  - [3. FUNCTIONAL RULES PROMPT](#3-functional-rules-prompt)
  - [4. EXPENSE EXTRACTION PROMPT](#4-expense-extraction-prompt)
  - [5. PROACTIVE ALERTS PROMPT](#5-proactive-alerts-prompt)
  - [6. DEBT PROFILE PROMPT](#6-debt-profile-prompt)
  - [7. RE-ENGAGEMENT PROMPT](#7-re-engagement-prompt)
  - [8. SCOPE CONTROL PROMPT](#8-scope-control-prompt)
  - [9. DATA CONSISTENCY PROMPT](#9-data-consistency-prompt)
  - [10. RECURRING TRANSACTIONS EDIT PROMPT](#10-recurring-transactions-edit-prompt)
- [📈 Evolução do Projeto: Camada de Investimentos](#-evolução-do-projeto-camada-de-investimentos)
  - [11. GOAL CREATION INTEGRITY PROMPT](#11-goal-creation-integrity-prompt)
  - [12. INVESTMENTS MODEL PROMPT](#12-investments-model-prompt)
  - [13. INVESTMENTS UX & DASHBOARD PROMPT](#13-investments-ux--dashboard-prompt)
- [🤔 Por que os prompts de investimento foram separados?](#-por-que-os-prompts-de-investimento-foram-separados)
- [🧠 Aprendizados do Projeto](#-aprendizados-do-projeto)
- [🛡️ Diretriz de Construção Utilizada](#️-diretriz-de-construção-utilizada)
- [💭 Reflexão sobre o processo](#-reflexão-sobre-o-processo)
- [📍 Estado Atual do Projeto](#-estado-atual-do-projeto)
- [🚀 Próximos Passos Possíveis](#-próximos-passos-possíveis)
- [📝 Observação Final](#-observação-final)

---

# 🖼️ Screenshots

> Abaixo estão alguns exemplos visuais do aplicativo em construção.

## Acesso ao Sistema
<img width="499" height="480" alt="image" src="https://github.com/user-attachments/assets/5922af93-c06c-4e1a-b5d5-e9d4c9d2de9e" />

## Home
<img width="559" height="1072" alt="image" src="https://github.com/user-attachments/assets/a690243b-340e-41ce-9e84-5bb825d36f6f" />

## Dashboard
<img width="540" height="886" alt="image" src="https://github.com/user-attachments/assets/a941cf5c-9ea4-4112-bbac-025fa95f45cf" />
<img width="510" height="968" alt="image" src="https://github.com/user-attachments/assets/8a75ea9d-8bda-4b0a-a1e4-6fa7207fc391" />
<img width="514" height="752" alt="image" src="https://github.com/user-attachments/assets/464253c5-4d5f-4f1c-8ce9-90d11a1a34c9" />
<img width="523" height="899" alt="image" src="https://github.com/user-attachments/assets/0f3b948c-a6a6-4c04-911f-5c8a3de91090" />

## Histórico
<img width="526" height="492" alt="image" src="https://github.com/user-attachments/assets/80cbc85d-f796-4840-a9ac-15f0d24885ba" />

## Investimentos
<img width="558" height="1079" alt="image" src="https://github.com/user-attachments/assets/7da3fe4b-0fa9-489c-ad63-6bed629b300d" />

## Metas
<img width="545" height="1048" alt="image" src="https://github.com/user-attachments/assets/928ff563-b5a8-4dfa-b04a-764ef4359ef2" />


# 🧱 Estrutura de Prompts Utilizados

Abaixo estão os **10 prompts principais** utilizados na construção do aplicativo.

---

## 1. APP PROMPT

Prompt principal responsável por definir a estrutura geral do produto.

### ✅ Finalidade
- criar o aplicativo de finanças pessoais;
- definir público-alvo;
- definir telas principais;
- orientar a experiência mobile-first;
- estruturar dashboard, chat, metas, histórico, relatórios e upload.

### 🧩 Papel no projeto
Foi a base inicial do aplicativo e serviu como direcionador de produto e interface.

### 📄 Arquivo
[`prompts/01_app_prompt.md`](./prompts/01_app_prompt.md)

---

## 2. AI AGENT PROMPT

Prompt para definição do comportamento do **Agente Financeiro**.

### ✅ Finalidade
- definir tom de voz;
- orientar linguagem acolhedora;
- manter respostas simples;
- determinar como o agente deve registrar gastos, receitas, metas e resumos;
- impedir comportamento julgador.

### 🧩 Papel no projeto
Deu identidade ao agente e ajudou a manter o foco do produto em finanças pessoais.

### 📄 Arquivo
[`prompts/02_ai_agent_prompt.md`](./prompts/02_ai_agent_prompt.md)

---

## 3. FUNCTIONAL RULES PROMPT

Prompt com as regras operacionais do agente.

### ✅ Finalidade
- definir como interpretar intenções;
- organizar confirmação de lançamentos;
- padronizar categorias;
- garantir clareza, controle e segurança nas respostas.

### 🧩 Papel no projeto
Foi importante para transformar o agente em algo funcional, e não apenas “bem escrito”.

### 📄 Arquivo
[`prompts/03_functional_rules_prompt.md`](./prompts/03_functional_rules_prompt.md)

---

## 4. EXPENSE EXTRACTION PROMPT

Prompt específico para extração silenciosa de dados financeiros.

### ✅ Finalidade
- extrair tipo de transação;
- identificar valor;
- identificar data;
- sugerir categoria;
- detectar forma de pagamento;
- devolver dados estruturados em JSON interno.

### 🧩 Papel no projeto
Separou a análise de dados da resposta ao usuário, melhorando a base para automação.

### 📄 Arquivo
[`prompts/04_expense_extraction_prompt.md`](./prompts/04_expense_extraction_prompt.md)

---

## 5. PROACTIVE ALERTS PROMPT

Prompt para alertas proativos e insights automáticos.

### ✅ Finalidade
- detectar padrões relevantes;
- alertar sobre categorias acima da média;
- apontar metas sem progresso;
- informar de forma útil e não invasiva.

### 🧩 Papel no projeto
Criou uma camada de inteligência proativa no produto.

### 📄 Arquivo
[`prompts/05_proactive_alerts_prompt.md`](./prompts/05_proactive_alerts_prompt.md)

---

## 6. DEBT PROFILE PROMPT

Prompt específico para usuários com perfil endividado.

### ✅ Finalidade
- ajustar linguagem para maior sensibilidade emocional;
- evitar culpa;
- acolher o usuário;
- orientar com passos simples e realistas.

### 🧩 Papel no projeto
Melhorou a experiência para usuários financeiramente fragilizados, tornando o agente mais humano e seguro.

### 📄 Arquivo
[`prompts/06_debt_profile_prompt.md`](./prompts/06_debt_profile_prompt.md)

---

## 7. RE-ENGAGEMENT PROMPT

Prompt para reengajamento de usuários inativos.

### ✅ Finalidade
- retomar o contato sem pressão;
- evitar culpa;
- oferecer retorno simples ao app;
- reforçar presença e acolhimento.

### 🧩 Papel no projeto
Ajudou a definir mensagens de retorno ao uso do aplicativo.

### 📄 Arquivo
[`prompts/07_re_engagement_prompt.md`](./prompts/07_re_engagement_prompt.md)

---

## 8. SCOPE CONTROL PROMPT

Prompt de controle de escopo do agente.

### ✅ Finalidade
- impedir que o agente se comporte como chatbot generalista;
- manter foco em finanças pessoais;
- limitar respostas fora do escopo;
- redirecionar o usuário com elegância para o propósito do app.

### 🧩 Papel no projeto
Foi essencial para preservar o posicionamento do produto como app financeiro especializado.

### 📄 Arquivo
[`prompts/08_scope_control_prompt.md`](./prompts/08_scope_control_prompt.md)

---

## 9. DATA CONSISTENCY PROMPT

Prompt para integridade de dados entre chat, histórico e dashboard.

### ✅ Finalidade
- impedir confirmações falsas do agente;
- garantir que histórico seja a fonte da verdade;
- evitar divergências entre lançamentos e gráficos;
- corrigir inconsistências de recorrência, exclusão e edição.

### 🧩 Papel no projeto
Foi um dos prompts mais importantes para estabilizar o comportamento real do sistema.

### 📄 Arquivo
[`prompts/09_data_consistency_prompt.md`](./prompts/09_data_consistency_prompt.md)

---

## 10. RECURRING TRANSACTIONS EDIT PROMPT

Prompt técnico para edição e exclusão de recorrências.

### ✅ Finalidade
- tratar corretamente séries recorrentes;
- definir escopos de edição;
- evitar duplicidade;
- garantir consistência entre ocorrência, série, histórico e dashboard.

### 🧩 Papel no projeto
Foi criado para resolver problemas específicos com recorrências, correções e exclusões.

### 📄 Arquivo
[`prompts/10_recurring_transactions_edit_prompt.md`](./prompts/10_recurring_transactions_edit_prompt.md)

---

# 📈 Evolução do Projeto: Camada de Investimentos

Durante o desenvolvimento do aplicativo, surgiu a necessidade de evoluir o produto para além do controle de receitas e despesas, incorporando também uma camada de **investimentos**.

Essa evolução não fazia parte do núcleo inicial do app e, por isso, foi tratada em uma etapa posterior com **3 prompts separados**, específicos para modelagem, experiência e dashboards de investimentos.

Essa separação foi intencional, pois os investimentos foram adicionados como uma **evolução funcional do aplicativo** conforme o produto amadureceu.

---

## 11. GOAL CREATION INTEGRITY PROMPT

Prompt criado para garantir integridade na criação de metas.

### ✅ Finalidade
- impedir que o agente confirme a criação de metas inexistentes;
- exigir persistência real antes da confirmação;
- sincronizar meta com dashboard e interface.

### 🧩 Papel no projeto
Foi criado quando surgiram inconsistências no fluxo de metas e passou a reforçar a confiabilidade do agente.

### 📄 Arquivo
[`prompts/11_goal_creation_integrity_prompt.md`](./prompts/11_goal_creation_integrity_prompt.md)

---

## 12. INVESTMENTS MODEL PROMPT

Prompt para modelagem de investimentos como uma terceira natureza financeira.

### ✅ Finalidade
- tratar investimento de forma separada de receita e despesa;
- modelar aportes, rendimentos e resgates;
- permitir identificação individual de cada investimento;
- manter histórico e saldo por investimento.

### 🧩 Papel no projeto
Foi o prompt central da evolução de investimentos e definiu a regra de negócio dessa nova camada.

### 📄 Arquivo
[`prompts/12_investments_model_prompt.md`](./prompts/12_investments_model_prompt.md)

---

## 13. INVESTMENTS UX & DASHBOARD PROMPT

Prompt para experiência visual e funcional da área de investimentos.

### ✅ Finalidade
- exibir KPIs de investimentos;
- criar gráficos específicos;
- mostrar histórico de aportes, resgates e rendimentos;
- integrar a camada de investimentos ao restante do app.

### 🧩 Papel no projeto
Complementou a modelagem de investimentos com a parte de interface, dashboards e navegação.

### 📄 Arquivo
[`prompts/13_investments_ux_dashboard_prompt.md`](./prompts/13_investments_ux_dashboard_prompt.md)

---

# 🤔 Por que os prompts de investimento foram separados?

Os prompts de investimento foram separados porque:

- não faziam parte do escopo inicial mínimo do app;
- surgiram como evolução natural do produto durante o desenvolvimento;
- exigiam uma nova regra de negócio;
- precisavam de tratamento distinto de receitas e despesas;
- impactavam histórico, KPIs, gráficos, patrimônio e experiência geral do usuário.

Em outras palavras, os prompts de investimento representam uma **segunda fase de maturidade do aplicativo**, adicionando controle patrimonial à organização financeira pessoal.

---

# 🧠 Aprendizados do Projeto

Ao longo da construção do aplicativo, alguns pontos se mostraram críticos:

- o agente precisa ser simpático, mas não pode confirmar ações sem persistência real;
- histórico e dashboard precisam usar exatamente a mesma base de dados;
- recorrências exigem regras próprias;
- datas financeiras devem ser tratadas como **data civil**, sem erro de timezone;
- investimentos não podem ser tratados como despesas comuns;
- prompts destrutivos ou ambíguos podem causar retrabalho e aumento de custo em créditos.

---

# 🛡️ Diretriz de Construção Utilizada

Durante a evolução do projeto, tornou-se importante reforçar uma regra para o Lovable:

- **não remover nada existente**;
- **não substituir páginas prontas**;
- **não reestruturar desnecessariamente**;
- **aplicar apenas ajustes incrementais**;
- **preservar tudo que já estava funcionando**.

Essa diretriz foi importante para evitar que alterações corretivas consumissem créditos desnecessariamente.

---

# 💭 Reflexão sobre o processo

## ✅ O que funcionou bem?

Alguns pontos funcionaram especialmente bem durante o processo:

- a divisão do desenvolvimento em blocos de prompts;
- a separação entre produto, comportamento do agente e regras operacionais;
- a especialização progressiva do agente;
- o uso de prompts específicos para corrigir problemas reais encontrados durante o uso;
- a evolução incremental do aplicativo, sem depender de uma reconstrução total a cada ajuste.

Também funcionou bem o fato de transformar problemas observados no app em prompts cada vez mais específicos, técnicos e direcionados.

---

## ⚠️ O que não funcionou como o esperado?

Nem tudo saiu como o esperado logo de início.

Os principais pontos de dificuldade foram:

- o agente confirmava ações que não haviam sido persistidas de fato;
- histórico, dashboard e gráficos nem sempre usavam a mesma base de dados;
- recorrências geravam inconsistências e duplicidades;
- datas sofriam deslocamento de um dia por erro de timezone;
- algumas mudanças no Lovable eram interpretadas como substituição de estrutura, e não como ajuste incremental;
- prompts mais genéricos ou interpretativos demais abriam margem para resultados indesejados.

Esses problemas mostraram que, em sistemas com regra de negócio, bons textos não bastam: é preciso especificar com precisão como o sistema deve se comportar.

---

## 🤖 O que aprendeu sobre conversar com IAs?

O processo trouxe aprendizados importantes sobre como conversar com IAs para construir produto:

- quanto mais específico o prompt, melhor o resultado;
- prompts genéricos tendem a gerar interpretações amplas demais;
- separar os problemas em blocos menores funciona melhor do que tentar resolver tudo em um único prompt;
- é fundamental explicitar o que **não deve ser removido ou substituído**;
- para regras sensíveis, como datas, recorrências, metas e investimentos, é melhor usar instruções mais técnicas e operacionais;
- a IA responde melhor quando recebe contexto + regra + limite + resultado esperado.

Na prática, o maior aprendizado foi que conversar bem com IAs não é só “pedir algo”. É **estruturar a intenção com clareza, restrições e critério de sucesso**.

---

# 📍 Estado Atual do Projeto

O aplicativo foi sendo evoluído em camadas:

1. estrutura principal do app;
2. comportamento do agente financeiro;
3. regras operacionais;
4. integridade de dados;
5. dashboards e histórico;
6. correção de recorrências;
7. criação confiável de metas;
8. evolução para investimentos.

---

# 🚀 Próximos Passos Possíveis

Possíveis evoluções futuras do projeto:

- orçamento por categoria;
- patrimônio líquido consolidado;
- conciliação bancária / Open Finance;
- carteira consolidada de investimentos;
- indicadores avançados de rentabilidade;
- metas vinculadas a investimentos;
- alertas patrimoniais;
- análises por perfil financeiro.

---

# 📝 Observação Final

Este projeto demonstra uma abordagem prática de construção orientada por prompts, na qual a evolução do produto foi guiada por regras de negócio, UX, consistência e especialização progressiva do agente.

Os 10 prompts principais estruturaram o núcleo do aplicativo, enquanto os 3 prompts de investimento registram uma etapa posterior de evolução funcional do produto durante o seu desenvolvimento.
