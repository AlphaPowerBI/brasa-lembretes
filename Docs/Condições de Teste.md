# Condições de Teste

Este documento consolida as condições de teste derivadas dos [Casos de Teste em Gherkin](./Casos%20de%20Teste%20em%20Gherkin.md), identificados de CT-001 a CT-124. A prioridade indica a importância de validar cada condição para o funcionamento e a experiência de uso da aplicação.

## Requisitos Testados

- Cadastro de lembretes únicos e recorrentes, validação dos campos e limites de conteúdo.
- Exibição, ordenação, agrupamento e contagem de lembretes futuros.
- Edição e exclusão de lembretes, incluindo confirmação e preservação de dados relacionados.
- Exibição e tratamento de alertas no horário agendado, inclusive em fila.
- Conclusão de lembretes únicos, avanço de ocorrências recorrentes e adiamento.
- Consulta, ordenação, persistência e limpeza do histórico de concluídos.
- Persistência local, recuperação diante de dados inválidos, sincronização entre abas e resiliência de schema.
- Atualização automática do relógio, dos tempos relativos e dos alertas.
- Comportamento temporal sob transições de fuso horário, horário de verão (DST), suspensão/hibernação e ajuste do relógio do sistema.
- Tolerância a limites físicos de armazenamento local (`QuotaExceededError`) e desempenho sob volume de dados.
- Regras de borda para anos bissextos e meses de duração variável em datas recorrentes.
- Responsividade, acessibilidade, compatibilidade entre navegadores e sanitização de segurança (XSS).

## Condições

| ID | Condição de Teste | Prioridade |
| ---: | --- | --- |
| 1 | Validar o cadastro de lembretes únicos: preenchimento dos campos obrigatórios e opcionais, rejeição de dados inválidos, limites e tratamento de texto, fechamento e reabertura do formulário e salvamento por teclado (CT-001 a CT-019). | Alta |
| 2 | Validar a criação de lembretes recorrentes nas frequências diária, semanal e mensal, incluindo a seleção da frequência e a apresentação de uma única ocorrência na lista de futuros (CT-020 a CT-022). | Alta |
| 3 | Validar a listagem de lembretes futuros: estado vazio e exemplos, ordenação cronológica, agrupamento por dia, contador, horário e tempo relativo, e ausência de alerta antes do vencimento (CT-023 a CT-033). | Alta |
| 4 | Validar a edição de lembretes: carregamento dos dados existentes, alteração de campos e frequência, reordenação, validações, cancelamento e atualização de lembretes adiados ou mensais (CT-034 a CT-043). | Alta |
| 5 | Validar a exclusão de lembretes com confirmação ou cancelamento, atualização do estado vazio, exclusão de recorrências, persistência da remoção e preservação do histórico (CT-044 a CT-050). | Alta |
| 6 | Validar a exibição dos alertas no horário correto, conteúdo e frequência apresentados, fila de alertas, retomada após ausência ou troca de aba, foco, comportamento de fechamento, som e apresentação em telas pequenas (CT-051 a CT-063). | Alta |
| 7 | Validar o tratamento de alertas como vistos: conclusão de lembrete único, registro no histórico, avanço de recorrências para a próxima ocorrência e consistência entre lembretes recorrentes e concluídos (CT-064 a CT-069). | Alta |
| 8 | Validar o adiamento de alertas: opções rápidas e data/hora personalizada, rejeição de horários inválidos, atualização do contador e do estado do lembrete, manutenção da recorrência e continuidade da fila (CT-070 a CT-080). | Alta |
| 9 | Validar o histórico de concluídos: visibilidade e contagem, ordenação, conteúdo, persistência, limpeza e apresentação segura de texto (CT-081 a CT-088). | Média |
| 10 | Validar a persistência e o armazenamento no navegador: recuperação após recarga ou reabertura, isolamento entre navegadores, tratamento de dados inválidos ou armazenamento indisponível, modo anônimo e sincronização entre abas (CT-089 a CT-098). | Alta |
| 11 | Validar a atualização automática das informações de tempo, incluindo relógio, tempo relativo, disparo de alertas e atualização do próximo lembrete sem recarregar a página (CT-099 a CT-102). | Alta |
| 12 | Validar a usabilidade em diferentes tamanhos de tela e navegadores, incluindo navegação por teclado, leitores de tela, alvos de toque, movimento reduzido, avisos temporários e funcionamento sem fontes externas (CT-103 a CT-114). | Média |
| 13 | Validar o comportamento sob alterações de tempo e energia: transições de horário de verão (DST), alteração de fuso horário, manipulação manual do relógio do sistema e recuperação de alertas após suspensão ou hibernação do dispositivo (CT-115, CT-116, CT-119 e CT-120). | Alta |
| 14 | Validar o comportamento sob limites de armazenamento e carga: tratamento gracioso de estouro de cota do navegador (localStorage cheio), integridade dos dados existentes diante de falhas de gravação e responsividade da interface com grande volume de lembretes (CT-117 e CT-118). | Média |
| 15 | Validar regras de borda avançadas de recorrência: avanço de lembretes diários e mensais no dia 29 de fevereiro em anos bissextos e preservação do dia base em anos comuns subsequentes (CT-122 e CT-123). | Média |
| 16 | Validar resiliência de schema e segurança de entrada: compatibilidade com versões antigas ou chaves corrompidas sem campos obrigatórios e sanitização contra injeção de scripts (XSS) no campo de descrição (CT-121 e CT-124). | Alta |