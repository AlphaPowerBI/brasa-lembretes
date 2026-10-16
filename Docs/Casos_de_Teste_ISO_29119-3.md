# Casos de Teste — Brasa Lembretes

*Formato baseado na ISO/IEC/IEEE 29119-3*

**Total de casos: 122  |  Análise de Valor Limite: 36  |  Partição de Equivalência: 52  |  Tabela de Decisão: 34**

Derivados das condições de teste 1 a 16 e dos cenários Gherkin CT-001 a CT-124. Cada caso está em uma tabela individual.

---

## Caso de Teste 1

| Campo | Valor |
| --- | --- |
| **ID** | 1 |
| **Título** | Deve rejeitar e exibir a mensagem "Informe um título para o lembrete." quando o título tem 0 caracteres (limite inferior do título). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-003, CT-007; Condição 1 — Título vazio → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Deixar o título vazio, informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | Exibe "Informe um título para o lembrete."; o campo de título fica inválido e recebe o foco. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 2

| Campo | Valor |
| --- | --- |
| **ID** | 2 |
| **Título** | Deve rejeitar e exibir a mensagem "Informe um título para o lembrete." quando o título contém apenas espaços (classe inválida: título em branco). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-003; Condição 1 — Título só com espaços → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "     " (somente espaços), informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | Exibe "Informe um título para o lembrete."; o campo de título fica inválido e recebe o foco. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 3

| Campo | Valor |
| --- | --- |
| **ID** | 3 |
| **Título** | Deve aceitar o título e exibir o contador 1/80 quando o título informado tem 1 caractere(s) (limite inferior válido). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-008; Condição 1 — Título com 1 a 80 caracteres → aceito |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar no campo de título um texto com 1 caractere(s). | O campo contém 1 caractere(s) e o contador do título exibe "1/80". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O formulário é fechado e o lembrete é criado com o título informado. |

**Pós-Condições**

- Um lembrete único é registrado na lista de Lembretes futuros e persistido no navegador.

---

## Caso de Teste 4

| Campo | Valor |
| --- | --- |
| **ID** | 4 |
| **Título** | Deve aceitar o título e exibir o contador 40/80 quando o título informado tem 40 caractere(s) (representante do interior da faixa válida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-008; Condição 1 — Título com 1 a 80 caracteres → aceito |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar no campo de título um texto com 40 caractere(s). | O campo contém 40 caractere(s) e o contador do título exibe "40/80". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O formulário é fechado e o lembrete é criado com o título informado. |

**Pós-Condições**

- Um lembrete único é registrado na lista de Lembretes futuros e persistido no navegador.

---

## Caso de Teste 5

| Campo | Valor |
| --- | --- |
| **ID** | 5 |
| **Título** | Deve aceitar o título e exibir o contador 79/80 quando o título informado tem 79 caractere(s) (limite imediatamente abaixo do máximo). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-008; Condição 1 — Título com 1 a 80 caracteres → aceito |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar no campo de título um texto com 79 caractere(s). | O campo contém 79 caractere(s) e o contador do título exibe "79/80". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O formulário é fechado e o lembrete é criado com o título informado. |

**Pós-Condições**

- Um lembrete único é registrado na lista de Lembretes futuros e persistido no navegador.

---

## Caso de Teste 6

| Campo | Valor |
| --- | --- |
| **ID** | 6 |
| **Título** | Deve aceitar o título e exibir o contador 80/80 quando o título informado tem 80 caractere(s) (limite superior válido). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-008, CT-016; Condição 1 — Título com 80 caracteres → aceito |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar no campo de título um texto com 80 caractere(s). | O campo contém 80 caractere(s) e o contador do título exibe "80/80". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O formulário é fechado e o lembrete é criado com o título informado. |

**Pós-Condições**

- Um lembrete único é registrado na lista de Lembretes futuros e persistido no navegador.

---

## Caso de Teste 7

| Campo | Valor |
| --- | --- |
| **ID** | 7 |
| **Título** | Deve limitar o campo a 80 caracteres e exibir o contador "80/80" quando 81 caracteres são digitados (limite imediatamente acima do máximo). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-008; Condição 1 — Título acima de 80 caracteres → truncado em 80 |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar no campo de título um texto com 81 caracteres. | O campo contém apenas 80 caracteres e o contador exibe "80/80". |

**Pós-Condições**

- O 81º caractere não é aceito pelo campo.

---

## Caso de Teste 8

| Campo | Valor |
| --- | --- |
| **ID** | 8 |
| **Título** | Deve manter apenas os primeiros 80 caracteres e exibir "80/80" quando um texto de 120 caracteres é colado no título (classe: acima do máximo, entrada por colagem). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-010; Condição 1 — Título acima de 80 caracteres → truncado em 80 |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Colar no campo de título um texto com 120 caracteres. | O campo mantém os primeiros 80 caracteres e o contador exibe "80/80". |

**Pós-Condições**

- Os 40 caracteres excedentes são descartados.

---

## Caso de Teste 9

| Campo | Valor |
| --- | --- |
| **ID** | 9 |
| **Título** | Deve aceitar a descrição e exibir o contador 0/500 quando a descrição informada tem 0 caractere(s) (limite inferior, campo opcional). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição com 0 a 500 caracteres → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de descrição" e digitar uma descrição com 0 caractere(s). | O campo contém 0 caractere(s) e o contador da descrição exibe "0/500". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão não exibe parágrafo de descrição. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 10

| Campo | Valor |
| --- | --- |
| **ID** | 10 |
| **Título** | Deve tratar a descrição como vazia quando ela contém apenas espaços (classe: descrição em branco). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-011; Condição 1 — Descrição só com espaços → tratada como vazia |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Sem descrição" e a descrição com "     " (somente espaços). | Os dados são aceitos no formulário. |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão não exibe parágrafo de descrição. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 11

| Campo | Valor |
| --- | --- |
| **ID** | 11 |
| **Título** | Deve aceitar a descrição e exibir o contador 1/500 quando a descrição informada tem 1 caractere(s) (limite inferior preenchido). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição com 0 a 500 caracteres → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de descrição" e digitar uma descrição com 1 caractere(s). | O campo contém 1 caractere(s) e o contador da descrição exibe "1/500". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão exibe a descrição informada. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 12

| Campo | Valor |
| --- | --- |
| **ID** | 12 |
| **Título** | Deve aceitar a descrição e exibir o contador 250/500 quando a descrição informada tem 250 caractere(s) (representante do interior da faixa válida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição com 0 a 500 caracteres → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de descrição" e digitar uma descrição com 250 caractere(s). | O campo contém 250 caractere(s) e o contador da descrição exibe "250/500". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão exibe a descrição informada. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 13

| Campo | Valor |
| --- | --- |
| **ID** | 13 |
| **Título** | Deve aceitar a descrição e exibir o contador 499/500 quando a descrição informada tem 499 caractere(s) (limite imediatamente abaixo do máximo). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição com 0 a 500 caracteres → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de descrição" e digitar uma descrição com 499 caractere(s). | O campo contém 499 caractere(s) e o contador da descrição exibe "499/500". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão exibe a descrição informada. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 14

| Campo | Valor |
| --- | --- |
| **ID** | 14 |
| **Título** | Deve aceitar a descrição e exibir o contador 500/500 quando a descrição informada tem 500 caractere(s) (limite superior válido). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição com 0 a 500 caracteres → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de descrição" e digitar uma descrição com 500 caractere(s). | O campo contém 500 caractere(s) e o contador da descrição exibe "500/500". |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O lembrete é criado e o cartão exibe a descrição completa. |

**Pós-Condições**

- O lembrete é registrado na lista de Lembretes futuros.

---

## Caso de Teste 15

| Campo | Valor |
| --- | --- |
| **ID** | 15 |
| **Título** | Deve limitar o campo a 500 caracteres e exibir "500/500" quando 501 caracteres são digitados (limite imediatamente acima do máximo). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-009; Condição 1 — Descrição acima de 500 caracteres → truncada em 500 |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Digitar na descrição um texto com 501 caracteres. | O campo contém apenas 500 caracteres e o contador exibe "500/500". |

**Pós-Condições**

- O 501º caractere não é aceito pelo campo.

---

## Caso de Teste 16

| Campo | Valor |
| --- | --- |
| **ID** | 16 |
| **Título** | Deve rejeitar e exibir a mensagem "Informe a data e a hora do lembrete." quando a data e hora informada é vazia (classe inválida: ausência de valor). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-004; Condição 1 — Data vazia → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de data" e informar a data e hora: vazia. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | Exibe "Informe a data e a hora do lembrete."; o campo de data e hora fica marcado como inválido. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 17

| Campo | Valor |
| --- | --- |
| **ID** | 17 |
| **Título** | Deve rejeitar e exibir a mensagem "Escolha uma data e hora no futuro." quando a data e hora informada é 1 dia atrás (classe inválida: passado distante). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-005; Condição 1 — Data no passado → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de data" e informar a data e hora: 1 dia atrás. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | Exibe "Escolha uma data e hora no futuro."; o campo de data e hora fica marcado como inválido. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 18

| Campo | Valor |
| --- | --- |
| **ID** | 18 |
| **Título** | Deve rejeitar e exibir a mensagem "Escolha uma data e hora no futuro." quando a data e hora informada é 1 minuto atrás (limite imediatamente abaixo do minuto atual). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-005; Condição 1 — Data no passado → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de data" e informar a data e hora: 1 minuto atrás. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | Exibe "Escolha uma data e hora no futuro."; o campo de data e hora fica marcado como inválido. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 19

| Campo | Valor |
| --- | --- |
| **ID** | 19 |
| **Título** | Deve rejeitar e exibir a mensagem "Escolha uma data e hora no futuro." quando a data e hora informada é o minuto atual (limite: não é futuro). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-005; Condição 1 — Data que não é futura → erro |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de data" e informar a data e hora: o minuto atual. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | Exibe "Escolha uma data e hora no futuro."; o campo de data e hora fica marcado como inválido. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 20

| Campo | Valor |
| --- | --- |
| **ID** | 20 |
| **Título** | Deve criar o lembrete e exibir o horário informado quando a data e hora é o próximo minuto (limite mínimo aceito). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-006; Condição 1 — Data futura (limite mínimo) → aceita |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste de data futura" e informar a data e hora do próximo minuto. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | O lembrete é criado e o horário exibido no cartão corresponde ao informado. |

**Pós-Condições**

- O lembrete é registrado em Lembretes futuros.

---

## Caso de Teste 21

| Campo | Valor |
| --- | --- |
| **ID** | 21 |
| **Título** | Deve criar o lembrete único quando título e data e hora futura (daqui a 1 hora) são válidos (representante da classe válida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-001; Condição 1 — Campos obrigatórios válidos → lembrete criado |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Pagar boleto do condomínio" e informar uma data e hora daqui a 1 hora. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | O formulário é fechado; aviso "Lembrete criado para" com a data e hora; cartão com o chip "Único"; contador "1 lembrete"; bloco "Próximo lembrete" exibe o título. |

**Pós-Condições**

- O lembrete é persistido no navegador.

---

## Caso de Teste 22

| Campo | Valor |
| --- | --- |
| **ID** | 22 |
| **Título** | Deve exibir as duas mensagens de erro e focar o título quando título e data e hora estão vazios (combinação de classes inválidas). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-007; Condição 1 — Título e data inválidos → dois erros |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Deixar título e data e hora vazios e clicar em "Salvar lembrete". | Exibe "Informe um título para o lembrete." e "Informe a data e a hora do lembrete."; o foco vai para o título. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 23

| Campo | Valor |
| --- | --- |
| **ID** | 23 |
| **Título** | Deve exibir a tag "Recorrente · Diário" quando o lembrete é criado como recorrente com a frequência "Todos os dias" (categoria diário). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-020, CT-021; Condição 2 — Frequência diário → tag Diário |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Lembrete diário" e selecionar "Recorrente". | O campo "Frequência" é exibido com o valor padrão "Todos os dias". |
| 2 | Escolher a frequência "Todos os dias", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe a tag "Recorrente · Diário" e existe apenas 1 cartão para o lembrete. |

**Pós-Condições**

- O lembrete recorrente é persistido com a frequência escolhida.

---

## Caso de Teste 24

| Campo | Valor |
| --- | --- |
| **ID** | 24 |
| **Título** | Deve exibir a tag "Recorrente · Semanal" quando o lembrete é criado como recorrente com a frequência "Toda semana" (categoria semanal). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-020, CT-021; Condição 2 — Frequência semanal → tag Semanal |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Lembrete semanal" e selecionar "Recorrente". | O campo "Frequência" é exibido com o valor padrão "Todos os dias". |
| 2 | Escolher a frequência "Toda semana", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe a tag "Recorrente · Semanal" e existe apenas 1 cartão para o lembrete. |

**Pós-Condições**

- O lembrete recorrente é persistido com a frequência escolhida.

---

## Caso de Teste 25

| Campo | Valor |
| --- | --- |
| **ID** | 25 |
| **Título** | Deve exibir a tag "Recorrente · Mensal" quando o lembrete é criado como recorrente com a frequência "Todo mês" (categoria mensal). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-020, CT-021; Condição 2 — Frequência mensal → tag Mensal |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Lembrete mensal" e selecionar "Recorrente". | O campo "Frequência" é exibido com o valor padrão "Todos os dias". |
| 2 | Escolher a frequência "Todo mês", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe a tag "Recorrente · Mensal" e existe apenas 1 cartão para o lembrete. |

**Pós-Condições**

- O lembrete recorrente é persistido com a frequência escolhida.

---

## Caso de Teste 26

| Campo | Valor |
| --- | --- |
| **ID** | 26 |
| **Título** | Deve exibir "Nenhum lembrete agendado" e deixar o contador vazio quando não existem lembretes futuros (limite inferior: 0 lembretes). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-023; Condição 3 — Estado vazio |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal. | Exibe "Nenhum lembrete agendado" e os botões "Criar primeiro lembrete" e "Carregar exemplos"; o contador está vazio; "Próximo lembrete" e "Concluídos" ficam ocultos. |

**Pós-Condições**

- Nenhum dado é criado.

---

## Caso de Teste 27

| Campo | Valor |
| --- | --- |
| **ID** | 27 |
| **Título** | Deve exibir "1 lembrete" no contador quando existem 1 lembretes futuros (limite inferior, singular). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-030; Condição 3 — Contador singular/plural |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível e com 1 lembrete(s) futuro(s) cadastrado(s). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o contador da lista de Lembretes futuros. | O contador exibe "1 lembrete". |

**Pós-Condições**

- A lista exibe 1 cartão(ões).

---

## Caso de Teste 28

| Campo | Valor |
| --- | --- |
| **ID** | 28 |
| **Título** | Deve exibir "2 lembretes" no contador quando existem 2 lembretes futuros (primeiro valor no plural). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-030; Condição 3 — Contador singular/plural |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível e com 2 lembrete(s) futuro(s) cadastrado(s). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o contador da lista de Lembretes futuros. | O contador exibe "2 lembretes". |

**Pós-Condições**

- A lista exibe 2 cartão(ões).

---

## Caso de Teste 29

| Campo | Valor |
| --- | --- |
| **ID** | 29 |
| **Título** | Deve exibir "10 lembretes" no contador quando existem 10 lembretes futuros (representante do plural com dois dígitos). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-030; Condição 3 — Contador singular/plural |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível e com 10 lembrete(s) futuro(s) cadastrado(s). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o contador da lista de Lembretes futuros. | O contador exibe "10 lembretes". |

**Pós-Condições**

- A lista exibe 10 cartão(ões).

---

## Caso de Teste 30

| Campo | Valor |
| --- | --- |
| **ID** | 30 |
| **Título** | Deve exibir "em menos de 1 min" no card de tempo relativo quando o lembrete está agendado para daqui a 30 segundos (interior da faixa abaixo de 1 minuto). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 30 segundos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em menos de 1 min". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 31

| Campo | Valor |
| --- | --- |
| **ID** | 31 |
| **Título** | Deve exibir "em menos de 1 min" no card de tempo relativo quando o lembrete está agendado para daqui a 1 minuto (limite de 1 minuto). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 1 minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em menos de 1 min". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 32

| Campo | Valor |
| --- | --- |
| **ID** | 32 |
| **Título** | Deve exibir "em 45 min" no card de tempo relativo quando o lembrete está agendado para daqui a 45 minutos (faixa de minutos). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 45 minutos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em 45 min". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 33

| Campo | Valor |
| --- | --- |
| **ID** | 33 |
| **Título** | Deve exibir "em 2 h" no card de tempo relativo quando o lembrete está agendado para daqui a 2 horas (faixa de horas exatas). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 2 horas. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em 2 h". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 34

| Campo | Valor |
| --- | --- |
| **ID** | 34 |
| **Título** | Deve exibir "em 2 h 15 min" no card de tempo relativo quando o lembrete está agendado para daqui a 2 horas e 15 minutos (faixa de horas com minutos). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 2 horas e 15 minutos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em 2 h 15 min". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 35

| Campo | Valor |
| --- | --- |
| **ID** | 35 |
| **Título** | Deve exibir "em 3 d" no card de tempo relativo quando o lembrete está agendado para daqui a 3 dias (faixa de dias exatos). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 3 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em 3 d". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 36

| Campo | Valor |
| --- | --- |
| **ID** | 36 |
| **Título** | Deve exibir "em 1 d 4 h" no card de tempo relativo quando o lembrete está agendado para daqui a 1 dia e 4 horas (faixa de dias com horas). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-031; Condição 3 — Tempo relativo |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 1 dia e 4 horas. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o card de tempo relativo do lembrete. | O card exibe "em 1 d 4 h". |

**Pós-Condições**

- Nenhum alerta "Chegou a hora" é exibido.

---

## Caso de Teste 37

| Campo | Valor |
| --- | --- |
| **ID** | 37 |
| **Título** | Deve rotular o grupo corretamente quando o lembrete está agendado para hoje (categoria hoje). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-027; Condição 3 — Agrupamento por dia |
| **Pré-Condições** | Existe um lembrete único agendado para hoje. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o cabeçalho do grupo de dia. | O grupo tem o rótulo "Hoje" seguido da data por extenso. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 38

| Campo | Valor |
| --- | --- |
| **ID** | 38 |
| **Título** | Deve rotular o grupo corretamente quando o lembrete está agendado para amanhã (categoria amanhã). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-027; Condição 3 — Agrupamento por dia |
| **Pré-Condições** | Existe um lembrete único agendado para amanhã. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o cabeçalho do grupo de dia. | O grupo tem o rótulo "Amanhã" seguido da data por extenso. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 39

| Campo | Valor |
| --- | --- |
| **ID** | 39 |
| **Título** | Deve rotular o grupo corretamente quando o lembrete está agendado para daqui a 5 dias (categoria data distante). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-027; Condição 3 — Agrupamento por dia |
| **Pré-Condições** | Existe um lembrete único agendado para daqui a 5 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o cabeçalho do grupo de dia. | O grupo exibe apenas o dia da semana e a data por extenso, sem rótulo Hoje/Amanhã. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 40

| Campo | Valor |
| --- | --- |
| **ID** | 40 |
| **Título** | Deve agrupar no mesmo grupo de dia quando os lembretes estão agendados às 00:00 e às 23:59 do mesmo dia (limites do dia civil). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-029; Condição 3 — Agrupamento por dia (limites do dia) |
| **Pré-Condições** | Existem dois lembretes para o mesmo dia civil seguinte, às 00:00 e às 23:59. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar os grupos de dia. | Há um único grupo "Amanhã" com os cartões 00:00 e 23:59, nessa ordem. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 41

| Campo | Valor |
| --- | --- |
| **ID** | 41 |
| **Título** | Deve exibir o horário "14:05" no formato 24 horas quando o lembrete está agendado para as 14:05. |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-033; Condição 3 — Horário no formato 24 horas |
| **Pré-Condições** | Existe um lembrete único agendado para amanhã às 14:05. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar o horário do cartão. | O cartão exibe "14:05". |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 42

| Campo | Valor |
| --- | --- |
| **ID** | 42 |
| **Título** | Deve avançar o lembrete diário para 16/12/2026 às 09:00 quando ele é marcado como visto em 15/12/2026 (interior do mês). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência diário (caso comum) |
| **Pré-Condições** | Existe um lembrete diário agendado para 15/12/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 16/12/2026 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 16/12/2026 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 43

| Campo | Valor |
| --- | --- |
| **ID** | 43 |
| **Título** | Deve avançar o lembrete diário para 01/01/2027 às 09:00 quando ele é marcado como visto em 31/12/2026 (limite: último dia do ano). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência diário (virada de ano) |
| **Pré-Condições** | Existe um lembrete diário agendado para 31/12/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 01/01/2027 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 01/01/2027 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 44

| Campo | Valor |
| --- | --- |
| **ID** | 44 |
| **Título** | Deve avançar o lembrete semanal para 22/12/2026 às 09:00 quando ele é marcado como visto em 15/12/2026 (interior do ano). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência semanal (caso comum) |
| **Pré-Condições** | Existe um lembrete semanal agendado para 15/12/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 22/12/2026 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 22/12/2026 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 45

| Campo | Valor |
| --- | --- |
| **ID** | 45 |
| **Título** | Deve avançar o lembrete semanal para 04/01/2027 às 09:00 quando ele é marcado como visto em 28/12/2026 (limite: virada de ano). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência semanal (virada de ano) |
| **Pré-Condições** | Existe um lembrete semanal agendado para 28/12/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 04/01/2027 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 04/01/2027 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 46

| Campo | Valor |
| --- | --- |
| **ID** | 46 |
| **Título** | Deve avançar o lembrete mensal para 15/11/2026 às 09:00 quando ele é marcado como visto em 15/10/2026 (interior do ano). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência mensal (caso comum) |
| **Pré-Condições** | Existe um lembrete mensal agendado para 15/10/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 15/11/2026 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 15/11/2026 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 47

| Campo | Valor |
| --- | --- |
| **ID** | 47 |
| **Título** | Deve avançar o lembrete mensal para 15/01/2027 às 09:00 quando ele é marcado como visto em 15/12/2026 (limite: dezembro para janeiro). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-065; Condição 7 — Avanço de recorrência mensal (virada de ano) |
| **Pré-Condições** | Existe um lembrete mensal agendado para 15/12/2026 às 09:00 e o alerta "Chegou a hora" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Visto. Próxima vez:" com a data 15/01/2027 às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e Concluídos. | O lembrete aparece em Lembretes futuros em 15/01/2027 e não aparece em Concluídos. |

**Pós-Condições**

- A próxima ocorrência é persistida no navegador.

---

## Caso de Teste 48

| Campo | Valor |
| --- | --- |
| **ID** | 48 |
| **Título** | Deve agendar a próxima ocorrência para 28/02/2027 e depois 31/03/2027 quando o lembrete mensal criado no dia 31 é marcado como visto em 31/01/2027 (fevereiro de ano comum). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (fevereiro de ano comum) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 31, agendado para 31/01/2027, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 28/02/2027. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 31: 31/03/2027. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 49

| Campo | Valor |
| --- | --- |
| **ID** | 49 |
| **Título** | Deve agendar a próxima ocorrência para 29/02/2028 e depois 31/03/2028 quando o lembrete mensal criado no dia 31 é marcado como visto em 31/01/2028 (fevereiro de ano bissexto). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (fevereiro de ano bissexto) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 31, agendado para 31/01/2028, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 29/02/2028. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 31: 31/03/2028. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 50

| Campo | Valor |
| --- | --- |
| **ID** | 50 |
| **Título** | Deve agendar a próxima ocorrência para 30/04/2027 e depois 31/05/2027 quando o lembrete mensal criado no dia 31 é marcado como visto em 31/03/2027 (mês seguinte com 30 dias). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (mês seguinte com 30 dias) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 31, agendado para 31/03/2027, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 30/04/2027. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 31: 31/05/2027. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 51

| Campo | Valor |
| --- | --- |
| **ID** | 51 |
| **Título** | Deve agendar a próxima ocorrência para 28/02/2027 e depois 30/03/2027 quando o lembrete mensal criado no dia 30 é marcado como visto em 30/01/2027 (dia 30 em fevereiro). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (dia 30 em fevereiro) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 30, agendado para 30/01/2027, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 28/02/2027. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 30: 30/03/2027. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 52

| Campo | Valor |
| --- | --- |
| **ID** | 52 |
| **Título** | Deve agendar a próxima ocorrência para 28/02/2027 e depois 29/03/2027 quando o lembrete mensal criado no dia 29 é marcado como visto em 29/01/2027 (dia 29 em fevereiro de ano comum). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (dia 29 em fevereiro de ano comum) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 29, agendado para 29/01/2027, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 28/02/2027. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 29: 29/03/2027. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 53

| Campo | Valor |
| --- | --- |
| **ID** | 53 |
| **Título** | Deve agendar a próxima ocorrência para 29/02/2028 e depois 29/03/2028 quando o lembrete mensal criado no dia 29 é marcado como visto em 29/01/2028 (dia 29 em ano bissexto). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-066; Condição 7 — Recorrência mensal em dia inexistente (dia 29 em ano bissexto) |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente no dia 29, agendado para 29/01/2028, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 29/02/2028. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia 29: 29/03/2028. |

**Pós-Condições**

- A recorrência mensal permanece em Lembretes futuros e fora de Concluídos.

---

## Caso de Teste 54

| Campo | Valor |
| --- | --- |
| **ID** | 54 |
| **Título** | Deve exibir a próxima ocorrência no futuro e não reabrir alertas das ocorrências perdidas quando o lembrete diário está atrasado há 5 dias e é marcado como visto. |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-067; Condição 7 — Recorrência muito atrasada |
| **Pré-Condições** | Existe um lembrete diário cujo último horário agendado foi há 5 dias, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida está no futuro e a janela de alerta é fechada. |
| 2 | Aguardar alguns segundos observando a tela. | Nenhum alerta é reaberto para as ocorrências perdidas. |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros.

---

## Caso de Teste 55

| Campo | Valor |
| --- | --- |
| **ID** | 55 |
| **Título** | Deve adiar o lembrete para agora + 10 minutos (segundos zerados) quando a opção rápida "+10 min" é escolhida (categoria de opção rápida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-070, CT-080; Condição 8 — Adiar por opção rápida |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+10 min". | Aviso "Adiado para" seguido de agora + 10 minutos (segundos zerados); a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros. | O lembrete aparece em agora + 10 minutos (segundos zerados) com o chip "Adiado 1x". |

**Pós-Condições**

- O novo horário é persistido no navegador.

---

## Caso de Teste 56

| Campo | Valor |
| --- | --- |
| **ID** | 56 |
| **Título** | Deve adiar o lembrete para agora + 60 minutos (segundos zerados) quando a opção rápida "+1 hora" é escolhida (categoria de opção rápida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-070, CT-080; Condição 8 — Adiar por opção rápida |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+1 hora". | Aviso "Adiado para" seguido de agora + 60 minutos (segundos zerados); a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros. | O lembrete aparece em agora + 60 minutos (segundos zerados) com o chip "Adiado 1x". |

**Pós-Condições**

- O novo horário é persistido no navegador.

---

## Caso de Teste 57

| Campo | Valor |
| --- | --- |
| **ID** | 57 |
| **Título** | Deve adiar o lembrete para amanhã às 09:00 quando a opção rápida "Amanhã às 9h" é escolhida (categoria de opção rápida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-070, CT-080; Condição 8 — Adiar por opção rápida |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Amanhã às 9h". | Aviso "Adiado para" seguido de amanhã às 09:00; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros. | O lembrete aparece em amanhã às 09:00 com o chip "Adiado 1x". |

**Pós-Condições**

- O novo horário é persistido no navegador.

---

## Caso de Teste 58

| Campo | Valor |
| --- | --- |
| **ID** | 58 |
| **Título** | Deve rejeitar e exibir a mensagem "Escolha a nova data e hora." quando o adiamento personalizado é vazio (classe inválida: ausência de valor). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-072; Condição 8 — Adiar sem data → erro |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" o valor: vazio, e clicar em "Adiar". | Exibe "Escolha a nova data e hora.". |

**Pós-Condições**

- O alerta continua aberto e o lembrete não é alterado.

---

## Caso de Teste 59

| Campo | Valor |
| --- | --- |
| **ID** | 59 |
| **Título** | Deve rejeitar e exibir a mensagem "A nova data precisa estar no futuro." quando o adiamento personalizado é 1 dia atrás (classe inválida: passado distante). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-073; Condição 8 — Adiar para o passado → erro |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" o valor: 1 dia atrás, e clicar em "Adiar". | Exibe "A nova data precisa estar no futuro.". |

**Pós-Condições**

- O alerta continua aberto e o lembrete não é alterado.

---

## Caso de Teste 60

| Campo | Valor |
| --- | --- |
| **ID** | 60 |
| **Título** | Deve rejeitar e exibir a mensagem "A nova data precisa estar no futuro." quando o adiamento personalizado é 1 minuto atrás (limite abaixo do minuto atual). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-073; Condição 8 — Adiar para o passado → erro |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" o valor: 1 minuto atrás, e clicar em "Adiar". | Exibe "A nova data precisa estar no futuro.". |

**Pós-Condições**

- O alerta continua aberto e o lembrete não é alterado.

---

## Caso de Teste 61

| Campo | Valor |
| --- | --- |
| **ID** | 61 |
| **Título** | Deve rejeitar e exibir a mensagem "A nova data precisa estar no futuro." quando o adiamento personalizado é o minuto atual (limite: não é futuro). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-073; Condição 8 — Adiar para o minuto atual → erro |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" o valor: o minuto atual, e clicar em "Adiar". | Exibe "A nova data precisa estar no futuro.". |

**Pós-Condições**

- O alerta continua aberto e o lembrete não é alterado.

---

## Caso de Teste 62

| Campo | Valor |
| --- | --- |
| **ID** | 62 |
| **Título** | Deve adiar o lembrete com sucesso quando o adiamento personalizado é o próximo minuto (limite mínimo aceito). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-074; Condição 8 — Adiar para o próximo minuto → aceito |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" o próximo minuto e clicar em "Adiar". | Aviso "Adiado para" com o horário informado. |

**Pós-Condições**

- O lembrete volta a Lembretes futuros no horário informado.

---

## Caso de Teste 63

| Campo | Valor |
| --- | --- |
| **ID** | 63 |
| **Título** | Deve adiar o lembrete para o horário informado quando o adiamento personalizado é daqui a 3 horas (representante da classe válida). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-071; Condição 8 — Adiar para data futura → aceito |
| **Pré-Condições** | O alerta do lembrete "Ligar para o João" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Informar em "Outra data e hora" um horário daqui a 3 horas e clicar em "Adiar". | Aviso "Adiado para" com o horário informado; a janela de alerta é fechada. |

**Pós-Condições**

- O lembrete volta a Lembretes futuros no horário informado.

---

## Caso de Teste 64

| Campo | Valor |
| --- | --- |
| **ID** | 64 |
| **Título** | Deve exibir o chip "Adiado 2x" quando o mesmo lembrete é adiado duas vezes (categoria: adiamentos acumulados). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-077; Condição 8 — Contador de adiamentos |
| **Pré-Condições** | O lembrete "Ligar para o João" já foi adiado 1 vez e seu alerta está aberto novamente. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+10 min". | Aviso "Adiado para" é exibido e a janela de alerta é fechada. |
| 2 | Consultar o cartão do lembrete em Lembretes futuros. | O cartão exibe o chip "Adiado 2x". |

**Pós-Condições**

- O contador de adiamentos é persistido no navegador.

---

## Caso de Teste 65

| Campo | Valor |
| --- | --- |
| **ID** | 65 |
| **Título** | Deve ocultar a seção "Concluídos" quando existem 0 lembretes concluídos (limite inferior). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-081; Condição 9 — Histórico vazio |
| **Pré-Condições** | Existem 0 lembrete(s) único(s) marcado(s) como visto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar a área de histórico. | A seção "Concluídos" não é exibida. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 66

| Campo | Valor |
| --- | --- |
| **ID** | 66 |
| **Título** | Deve exibir "Concluídos (1)" quando existem 1 lembretes concluídos (primeiro valor com histórico). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-087; Condição 9 — Contagem de concluídos |
| **Pré-Condições** | Existem 1 lembrete(s) único(s) marcado(s) como visto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar a área de histórico. | A seção exibe "Concluídos (1)" e o histórico persiste após recarregar a página. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 67

| Campo | Valor |
| --- | --- |
| **ID** | 67 |
| **Título** | Deve exibir "Concluídos (3)" com os itens riscados quando existem 3 lembretes concluídos (representante de vários itens). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-082; Condição 9 — Contagem de concluídos |
| **Pré-Condições** | Existem 3 lembrete(s) único(s) marcado(s) como visto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Abrir a tela principal e observar a área de histórico. | A seção exibe "Concluídos (3)"; ao expandir, os 3 lembretes aparecem com título riscado e data e hora da conclusão. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 68

| Campo | Valor |
| --- | --- |
| **ID** | 68 |
| **Título** | Deve exibir o texto literal sem executar HTML ou script quando o título contém marcação HTML (classe: caracteres especiais). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-013, CT-088; Condição 1 e 9 — Texto com HTML exibido como texto |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "<b>teste</b>", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe exatamente "<b>teste</b>", sem negrito, e nenhuma janela de alerta do navegador é aberta. |

**Pós-Condições**

- Nenhum código HTML ou script é executado.

---

## Caso de Teste 69

| Campo | Valor |
| --- | --- |
| **ID** | 69 |
| **Título** | Deve preservar emoji e acentuação quando o título é "Aniversário da vovó 🎂" (classe: caracteres Unicode). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-014; Condição 1 — Emojis e acentuação preservados |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Aniversário da vovó 🎂", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe "Aniversário da vovó 🎂" corretamente. |

**Pós-Condições**

- O texto é persistido sem alteração.

---

## Caso de Teste 70

| Campo | Valor |
| --- | --- |
| **ID** | 70 |
| **Título** | Deve remover os espaços das extremidades quando o título é "   Ligar para o banco   " (classe: espaços nas pontas). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-012; Condição 1 — Espaços nas extremidades removidos |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "   Ligar para o banco   ", informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe "Ligar para o banco" sem espaços nas pontas. |

**Pós-Condições**

- O título é persistido sem espaços nas extremidades.

---

## Caso de Teste 71

| Campo | Valor |
| --- | --- |
| **ID** | 71 |
| **Título** | Deve preservar as quebras de linha quando a descrição tem três linhas separadas por Enter (classe: texto multilinha). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-015; Condição 1 — Quebras de linha preservadas |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Lista de compras" e a descrição com três linhas separadas por Enter. | O campo aceita as quebras de linha. |
| 2 | Informar uma data e hora futura (ex.: daqui a 1 hora) e clicar em "Salvar lembrete". | O cartão exibe a descrição em três linhas. |

**Pós-Condições**

- A descrição é persistida com as quebras de linha.

---

## Caso de Teste 72

| Campo | Valor |
| --- | --- |
| **ID** | 72 |
| **Título** | Deve exibir o aviso "Não foi possível usar o armazenamento do navegador" e carregar a lista vazia quando o valor salvo é JSON inválido (classe inválida: dado corrompido). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-093; Condição 10 — Dados inválidos no armazenamento |
| **Pré-Condições** | A chave "brasa.lembretes.v1" do localStorage contém o valor "{abc". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | Exibe o aviso "Não foi possível usar o armazenamento do navegador" e a lista carrega vazia. |
| 2 | Criar um novo lembrete válido. | O lembrete é criado normalmente. |

**Pós-Condições**

- A aplicação permanece utilizável.

---

## Caso de Teste 73

| Campo | Valor |
| --- | --- |
| **ID** | 73 |
| **Título** | Deve carregar a lista vazia sem erro na tela quando o valor salvo é um objeto e não uma lista (classe inválida: tipo incorreto). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-094; Condição 10 — Dados inválidos no armazenamento |
| **Pré-Condições** | A chave "brasa.lembretes.v1" do localStorage contém o objeto {"a":1}. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | A aplicação carrega com a lista vazia e não apresenta erro na tela. |

**Pós-Condições**

- A aplicação permanece utilizável.

---

## Caso de Teste 74

| Campo | Valor |
| --- | --- |
| **ID** | 74 |
| **Título** | Deve exibir o aviso de armazenamento indisponível e manter o lembrete apenas na sessão quando o localStorage está bloqueado (classe inválida: armazenamento indisponível). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-095; Condição 10 — Armazenamento indisponível |
| **Pré-Condições** | O navegador bloqueia o acesso ao localStorage (cookies e dados de sites bloqueados). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação e criar um lembrete válido. | Exibe "Não foi possível usar o armazenamento do navegador. Os lembretes funcionam, mas serão perdidos ao fechar a página." e o lembrete aparece na lista. |
| 2 | Recarregar a página. | O lembrete deixa de existir. |

**Pós-Condições**

- Nenhum dado é persistido.

---

## Caso de Teste 75

| Campo | Valor |
| --- | --- |
| **ID** | 75 |
| **Título** | Deve exibir o cartão em uma coluna, o relógio em linha própria e o formulário colado à parte inferior quando o viewport tem 360 px (faixa de telas pequenas). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-103, CT-104; Condição 12 — Layout por largura |
| **Pré-Condições** | Existem ao menos 3 lembretes futuros; viewport de 360 px de largura. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Visualizar a lista e clicar em "+ Novo lembrete". | Sem rolagem horizontal; relógio em linha própria; cartão em uma coluna; formulário colado à parte inferior da tela. |

**Pós-Condições**

- Todos os botões estão visíveis e clicáveis.

---

## Caso de Teste 76

| Campo | Valor |
| --- | --- |
| **ID** | 76 |
| **Título** | Deve exibir o formulário colado à parte inferior da tela quando o viewport tem 560 px (limite superior da faixa de telas pequenas). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-104; Condição 12 — Formulário por largura |
| **Pré-Condições** | Viewport de 560 px de largura. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". | O formulário é exibido colado à parte inferior da tela. |

**Pós-Condições**

- Nenhum dado é criado.

---

## Caso de Teste 77

| Campo | Valor |
| --- | --- |
| **ID** | 77 |
| **Título** | Deve exibir o formulário centralizado e o cartão com horário à esquerda quando o viewport tem 561 px (limite inferior da faixa de telas maiores). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-103, CT-104; Condição 12 — Layout por largura |
| **Pré-Condições** | Existem ao menos 3 lembretes futuros; viewport de 561 px de largura. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Visualizar a lista e clicar em "+ Novo lembrete". | Sem rolagem horizontal; cartão com horário à esquerda e conteúdo à direita; formulário centralizado na tela. |

**Pós-Condições**

- Todos os botões estão visíveis e clicáveis.

---

## Caso de Teste 78

| Campo | Valor |
| --- | --- |
| **ID** | 78 |
| **Título** | Deve centralizar o conteúdo com largura máxima quando o viewport tem 820 px (faixa de telas grandes). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-103; Condição 12 — Layout por largura |
| **Pré-Condições** | Existem ao menos 3 lembretes futuros; viewport de 820 px de largura. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Visualizar a lista de Lembretes futuros. | Sem rolagem horizontal; o conteúdo fica centralizado com largura máxima. |

**Pós-Condições**

- Todos os botões estão visíveis e clicáveis.

---

## Caso de Teste 79

| Campo | Valor |
| --- | --- |
| **ID** | 79 |
| **Título** | Deve rejeitar o cadastro e exibir as duas mensagens de erro quando o título está vazio e a data e hora informada é 1 dia atrás (TD-1, R6: título inválido + data no passado). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-003, CT-005; Condição 1; TD-1, regra R6 |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Deixar o título vazio e informar a data e hora de 1 dia atrás. | Os dados são aceitos no formulário. |
| 2 | Clicar em "Salvar lembrete". | Exibe "Informe um título para o lembrete." e "Escolha uma data e hora no futuro." (resultado combinado inferido de CT-003 e CT-005; confirmar na especificação); o foco vai para o título. |

**Pós-Condições**

- Nenhum lembrete é criado.

---

## Caso de Teste 80

| Campo | Valor |
| --- | --- |
| **ID** | 80 |
| **Título** | Deve rejeitar a edição e exibir a mensagem "Informe um título para o lembrete." quando o título é alterado para vazio (TD-1, R7: edição com título inválido). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-039; Condição 4; TD-1, regra R7 |
| **Pré-Condições** | Existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". Alterar o título para: vazio. | Os dados são aceitos no formulário de edição. |
| 2 | Clicar em "Salvar alterações". | Exibe "Informe um título para o lembrete.". |

**Pós-Condições**

- O lembrete "Dentista" permanece com os dados anteriores.

---

## Caso de Teste 81

| Campo | Valor |
| --- | --- |
| **ID** | 81 |
| **Título** | Deve rejeitar a edição e exibir a mensagem "Informe a data e a hora do lembrete." quando a data e hora é alterado para vazia (TD-1, R8: edição com data vazia). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-039; Condição 4; TD-1, regra R8 |
| **Pré-Condições** | Existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". Alterar a data e hora para: vazia. | Os dados são aceitos no formulário de edição. |
| 2 | Clicar em "Salvar alterações". | Exibe "Informe a data e a hora do lembrete.". |

**Pós-Condições**

- O lembrete "Dentista" permanece com os dados anteriores.

---

## Caso de Teste 82

| Campo | Valor |
| --- | --- |
| **ID** | 82 |
| **Título** | Deve rejeitar a edição e exibir a mensagem "Escolha uma data e hora no futuro." quando a data e hora é alterado para 1 hora atrás (TD-1, R9: edição com data no passado). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-039; Condição 4; TD-1, regra R9 |
| **Pré-Condições** | Existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". Alterar a data e hora para: 1 hora atrás. | Os dados são aceitos no formulário de edição. |
| 2 | Clicar em "Salvar alterações". | Exibe "Escolha uma data e hora no futuro.". |

**Pós-Condições**

- O lembrete "Dentista" permanece com os dados anteriores.

---

## Caso de Teste 83

| Campo | Valor |
| --- | --- |
| **ID** | 83 |
| **Título** | Deve manter o chip "Único" e atualizar o título quando um lembrete único é editado sem mudar o tipo (TD-2, R1: Único → Único). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-035; Condição 4; TD-2, regra R1 |
| **Pré-Condições** | Existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". Alterar o título para "Dentista - retorno" e clicar em "Salvar alterações". | Aviso "Lembrete atualizado"; o cartão exibe "Dentista - retorno" com o chip "Único"; continua existindo apenas 1 cartão. |

**Pós-Condições**

- A alteração é persistida no navegador.

---

## Caso de Teste 84

| Campo | Valor |
| --- | --- |
| **ID** | 84 |
| **Título** | Deve exibir o chip "Recorrente · Semanal" quando um lembrete único é convertido em recorrente com a frequência "Toda semana" (TD-2, R2: Único → Recorrente). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-037; Condição 4; TD-2, regra R2 |
| **Pré-Condições** | Existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". Selecionar "Recorrente", escolher a frequência "Toda semana" e clicar em "Salvar alterações". | O cartão exibe o chip "Recorrente · Semanal". |

**Pós-Condições**

- O lembrete passa a ser recorrente semanal.

---

## Caso de Teste 85

| Campo | Valor |
| --- | --- |
| **ID** | 85 |
| **Título** | Deve exibir o chip "Único" quando um lembrete recorrente mensal é convertido em único (TD-2, R3: Recorrente → Único). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-038; Condição 4; TD-2, regra R3 |
| **Pré-Condições** | Existe o lembrete "Dentista" recorrente mensal (convertido a partir de único). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Editar" no cartão "Dentista". | O formulário abre com "Recorrente" selecionado e a frequência "Todo mês". |
| 2 | Selecionar "Único" e clicar em "Salvar alterações". | O cartão exibe o chip "Único". |

**Pós-Condições**

- O lembrete deixa de ser recorrente.

---

## Caso de Teste 86

| Campo | Valor |
| --- | --- |
| **ID** | 86 |
| **Título** | Deve exibir o alerta exibe a descrição "Após o almoço" e o chip "Único" quando o lembrete único com a descrição "Após o almoço" atinge o horário (TD-3, R1: descrição sim + tipo único). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-051, CT-052, CT-053; Condição 6; TD-3, regra R1 |
| **Pré-Condições** | Existe o lembrete único "Tomar remédio" com a descrição "Após o almoço" agendado para o próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o relógio atingir o horário agendado. | A janela "Chegou a hora" é exibida em até 1 segundo, com o título "Tomar remédio", "Agendado para" com data e hora, exibe a descrição "Após o almoço" e o chip "Único". |

**Pós-Condições**

- O lembrete deixa de aparecer em Lembretes futuros.

---

## Caso de Teste 87

| Campo | Valor |
| --- | --- |
| **ID** | 87 |
| **Título** | Deve exibir o alerta não exibe o parágrafo de descrição e o chip "Único" quando o lembrete único sem descrição atinge o horário (TD-3, R2: descrição não + tipo único). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-051, CT-052, CT-053; Condição 6; TD-3, regra R2 |
| **Pré-Condições** | Existe o lembrete único "Tomar remédio" sem descrição agendado para o próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o relógio atingir o horário agendado. | A janela "Chegou a hora" é exibida em até 1 segundo, com o título "Tomar remédio", "Agendado para" com data e hora, não exibe o parágrafo de descrição e o chip "Único". |

**Pós-Condições**

- O lembrete deixa de aparecer em Lembretes futuros.

---

## Caso de Teste 88

| Campo | Valor |
| --- | --- |
| **ID** | 88 |
| **Título** | Deve exibir o alerta exibe a descrição "Após o almoço" e o chip "Recorrente · Semanal" quando o lembrete semanal com a descrição "Após o almoço" atinge o horário (TD-3, R3: descrição sim + tipo semanal). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-051, CT-052, CT-053; Condição 6; TD-3, regra R3 |
| **Pré-Condições** | Existe o lembrete semanal "Tomar remédio" com a descrição "Após o almoço" agendado para o próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o relógio atingir o horário agendado. | A janela "Chegou a hora" é exibida em até 1 segundo, com o título "Tomar remédio", "Agendado para" com data e hora, exibe a descrição "Após o almoço" e o chip "Recorrente · Semanal". |

**Pós-Condições**

- O lembrete deixa de aparecer em Lembretes futuros.

---

## Caso de Teste 89

| Campo | Valor |
| --- | --- |
| **ID** | 89 |
| **Título** | Deve exibir o alerta não exibe o parágrafo de descrição e o chip "Recorrente · Semanal" quando o lembrete semanal sem descrição atinge o horário (TD-3, R4: descrição não + tipo semanal). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-051, CT-052, CT-053; Condição 6; TD-3, regra R4 |
| **Pré-Condições** | Existe o lembrete semanal "Tomar remédio" sem descrição agendado para o próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o relógio atingir o horário agendado. | A janela "Chegou a hora" é exibida em até 1 segundo, com o título "Tomar remédio", "Agendado para" com data e hora, não exibe o parágrafo de descrição e o chip "Recorrente · Semanal". |

**Pós-Condições**

- O lembrete deixa de aparecer em Lembretes futuros.

---

## Caso de Teste 90

| Campo | Valor |
| --- | --- |
| **ID** | 90 |
| **Título** | Deve mover o lembrete único para "Concluídos (1)" quando ele é marcado como visto (TD-4, R1: tipo único). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-064; Condição 7; TD-4, regra R1 |
| **Pré-Condições** | O alerta do lembrete único "Tomar remédio" está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | Aviso "Lembrete marcado como visto"; a janela de alerta é fechada. |
| 2 | Consultar Lembretes futuros e a seção "Concluídos". | "Tomar remédio" não aparece em Lembretes futuros; a seção "Concluídos (1)" passa a existir e lista o lembrete com data e hora da conclusão. |

**Pós-Condições**

- O lembrete é persistido no histórico de concluídos.

---

## Caso de Teste 91

| Campo | Valor |
| --- | --- |
| **ID** | 91 |
| **Título** | Deve exibir o segundo alerta imediatamente e ocultar o indicador da fila quando o primeiro é marcado como visto (TD-5, R1: marcar como visto + há outro na fila). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-056; Condição 6; TD-5, regra R1 |
| **Pré-Condições** | Existem 2 lembretes vencidos, com 2 alertas na fila. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto" no primeiro alerta. | O segundo alerta é exibido imediatamente e o indicador da fila deixa de ser exibido. |

**Pós-Condições**

- O primeiro lembrete é tratado conforme o seu tipo.

---

## Caso de Teste 92

| Campo | Valor |
| --- | --- |
| **ID** | 92 |
| **Título** | Deve fechar a janela e restaurar o título da aba "Brasa Lembretes" quando o último alerta é marcado como visto (TD-5, R2: marcar como visto + sem outro na fila). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-056; Condição 6; TD-5, regra R2 |
| **Pré-Condições** | Existe 1 lembrete vencido, com 1 alerta aberto e nenhum outro na fila. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A janela de alerta é fechada e o título da aba volta a ser "Brasa Lembretes". |

**Pós-Condições**

- Nenhum alerta permanece aberto.

---

## Caso de Teste 93

| Campo | Valor |
| --- | --- |
| **ID** | 93 |
| **Título** | Deve exibir o segundo alerta e devolver o primeiro lembrete a Lembretes futuros quando o primeiro é adiado com "+10 min" (TD-5, R3: adiar + há outro na fila). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-079; Condição 8; TD-5, regra R3 |
| **Pré-Condições** | Existem 2 lembretes vencidos, com 2 alertas na fila. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+10 min" no primeiro alerta. | O segundo alerta é exibido. |
| 2 | Consultar Lembretes futuros. | O primeiro lembrete aparece em Lembretes futuros com o horário adiado. |

**Pós-Condições**

- O novo horário do primeiro lembrete é persistido.

---

## Caso de Teste 94

| Campo | Valor |
| --- | --- |
| **ID** | 94 |
| **Título** | Deve fechar a janela e devolver o lembrete a Lembretes futuros quando o último alerta é adiado com "+10 min" (TD-5, R4: adiar + sem outro na fila). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-070; Condição 8; TD-5, regra R4 |
| **Pré-Condições** | Existe 1 lembrete vencido, com 1 alerta aberto e nenhum outro na fila. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+10 min". | A janela de alerta é fechada e nenhum outro alerta é exibido. |
| 2 | Consultar Lembretes futuros. | O lembrete aparece em agora + 10 minutos com o chip "Adiado 1x". |

**Pós-Condições**

- O novo horário é persistido.

---

## Caso de Teste 95

| Campo | Valor |
| --- | --- |
| **ID** | 95 |
| **Título** | Deve agendar a próxima ocorrência para a segunda-feira seguinte às 09:00 quando um lembrete semanal adiado com "+1 hora" é marcado como visto (TD-6, R2: adiar + recorrente). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-078; Condição 8; TD-6, regra R2 |
| **Pré-Condições** | O alerta de um lembrete semanal agendado originalmente para segunda-feira às 09:00 está aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+1 hora". | A janela é fechada e o lembrete volta a Lembretes futuros em agora + 60 minutos. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto". | A próxima ocorrência é a segunda-feira seguinte às 09:00, e não uma semana a partir do horário adiado. |

**Pós-Condições**

- A recorrência semanal é mantida em Lembretes futuros.

---

## Caso de Teste 96

| Campo | Valor |
| --- | --- |
| **ID** | 96 |
| **Título** | Deve excluir "Dentista" e manter "Mercado" quando a exclusão é confirmada (TD-7, R1: confirmar + único + não é o último). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-044; Condição 5; TD-7, regra R1 |
| **Pré-Condições** | Existem os lembretes futuros "Dentista" e "Mercado". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Excluir" no cartão "Dentista". | O cartão exibe "Excluir este lembrete?" com os botões "Excluir" e "Cancelar". |
| 2 | Clicar em "Excluir" na confirmação. | Aviso "Lembrete excluído"; "Dentista" não aparece mais; "Mercado" continua na lista. |

**Pós-Condições**

- A remoção é persistida no navegador.

---

## Caso de Teste 97

| Campo | Valor |
| --- | --- |
| **ID** | 97 |
| **Título** | Deve manter "Dentista" e restaurar os botões "Editar" e "Excluir" quando a exclusão é cancelada (TD-7, R2: cancelar). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-045; Condição 5; TD-7, regra R2 |
| **Pré-Condições** | Existem os lembretes futuros "Dentista" e "Mercado". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Excluir" no cartão "Dentista" e depois em "Cancelar" na confirmação. | O cartão volta a exibir "Editar" e "Excluir" e "Dentista" continua na lista. |

**Pós-Condições**

- Nenhum lembrete é removido.

---

## Caso de Teste 98

| Campo | Valor |
| --- | --- |
| **ID** | 98 |
| **Título** | Deve remover o lembrete diário e não exibir alerta no horário original quando a exclusão é confirmada (TD-7, R3: confirmar + recorrente). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-049; Condição 5; TD-7, regra R3 |
| **Pré-Condições** | Existe o lembrete diário "Beber água". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Excluir "Beber água" confirmando. | "Beber água" não aparece na lista. |
| 2 | Aguardar o horário original do lembrete. | Nenhum alerta é exibido. |

**Pós-Condições**

- Todas as ocorrências futuras são removidas.

---

## Caso de Teste 99

| Campo | Valor |
| --- | --- |
| **ID** | 99 |
| **Título** | Deve exibir o estado vazio quando o último lembrete é excluído com confirmação (TD-7, R4: confirmar + é o último). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-047; Condição 5; TD-7, regra R4 |
| **Pré-Condições** | Existe apenas o lembrete futuro "Dentista". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Excluir "Dentista" confirmando. | Exibe "Nenhum lembrete agendado" e o bloco "Próximo lembrete" fica oculto. |

**Pós-Condições**

- Nenhum lembrete permanece cadastrado.

---

## Caso de Teste 100

| Campo | Valor |
| --- | --- |
| **ID** | 100 |
| **Título** | Deve manter "Concluídos (1)" quando um lembrete futuro é excluído com confirmação (TD-7, R5: confirmar + existe histórico). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-050; Condição 5; TD-7, regra R5 |
| **Pré-Condições** | Existe 1 lembrete concluído no histórico e os lembretes futuros "Dentista" e "Mercado". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Excluir "Dentista" confirmando. | O histórico continua exibindo "Concluídos (1)". |

**Pós-Condições**

- O histórico permanece inalterado.

---

## Caso de Teste 101

| Campo | Valor |
| --- | --- |
| **ID** | 101 |
| **Título** | Deve exibir a confirmação apenas no cartão "Mercado" quando "Excluir" é acionado em dois cartões em sequência (TD-7, R6: confirmação já aberta em outro cartão). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-046; Condição 5; TD-7, regra R6 |
| **Pré-Condições** | Existem os lembretes futuros "Dentista" e "Mercado". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Excluir" no cartão "Dentista" e depois em "Excluir" no cartão "Mercado". | Apenas "Mercado" exibe a pergunta de confirmação; "Dentista" volta ao estado normal. |

**Pós-Condições**

- Nenhum lembrete é removido.

---

## Caso de Teste 102

| Campo | Valor |
| --- | --- |
| **ID** | 102 |
| **Título** | Deve exibir o alerta e emitir dois bipes quando houve interação prévia com a página (TD-8, R1: interação prévia: sim). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-061; Condição 6; TD-8, regra R1 |
| **Pré-Condições** | Existe um lembrete agendado para o próximo minuto e já houve clique ou toque na página. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o horário do lembrete. | A janela "Chegou a hora" é exibida e é emitido um sinal sonoro de dois bipes. |

**Pós-Condições**

- O alerta permanece aberto.

---

## Caso de Teste 103

| Campo | Valor |
| --- | --- |
| **ID** | 103 |
| **Título** | Deve exibir o alerta sem som e sem erro quando não houve interação prévia com a página (TD-8, R2: interação prévia: não). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-062; Condição 6; TD-8, regra R2 |
| **Pré-Condições** | Existe um lembrete agendado para o próximo minuto e a página foi apenas aberta, sem clique ou toque. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o horário do lembrete sem interagir. | A janela "Chegou a hora" aparece normalmente, sem som e sem mensagem de erro. |

**Pós-Condições**

- O alerta permanece aberto.

---

## Caso de Teste 104

| Campo | Valor |
| --- | --- |
| **ID** | 104 |
| **Título** | Deve carregar os lembretes "A" e "B" sem aviso quando o armazenamento contém uma lista válida (TD-9, R1: lista válida). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-089; Condição 10; TD-9, regra R1 |
| **Pré-Condições** | A chave "brasa.lembretes.v1" do localStorage contém uma lista válida com os lembretes "A" e "B". |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | "A" e "B" aparecem na lista com os mesmos dados e nenhum aviso de armazenamento é exibido. |

**Pós-Condições**

- Nenhum dado é alterado.

---

## Caso de Teste 105

| Campo | Valor |
| --- | --- |
| **ID** | 105 |
| **Título** | Deve fechar o formulário, descartar o rascunho e exibir o alerta quando outro lembrete vence com o formulário aberto (TD-10, R1: formulário aberto: sim). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-059; Condição 6; TD-10, regra R1 |
| **Pré-Condições** | O formulário de novo lembrete está aberto com dados preenchidos e outro lembrete vence no próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o horário do outro lembrete. | O formulário é fechado, o alerta é exibido e os dados digitados são perdidos (comportamento a validar quanto à usabilidade, conforme observação do CT-059). |

**Pós-Condições**

- Nenhum lembrete novo é criado.

---

## Caso de Teste 106

| Campo | Valor |
| --- | --- |
| **ID** | 106 |
| **Título** | Deve exibir o alerta, atualizar o título da aba e focar "Marcar como visto" quando o lembrete vence sem formulário aberto (TD-10, R2: formulário aberto: não). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-051; Condição 6; TD-10, regra R2 |
| **Pré-Condições** | Existe o lembrete "Tomar remédio" com descrição "Após o almoço" agendado para o próximo minuto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o relógio atingir o horário agendado. | A janela "Chegou a hora" é exibida em até 1 segundo; o título da aba passa a ser "(1) Lembrete agora · Brasa Lembretes" e o foco fica no botão "Marcar como visto". |

**Pós-Condições**

- O lembrete sai de Lembretes futuros.

---

## Caso de Teste 107

| Campo | Valor |
| --- | --- |
| **ID** | 107 |
| **Título** | Deve exibir o alerta sem travar a interface e sem duplicidade quando o lembrete das 02:30 está agendado no dia da transição do horário de verão (classe: transição de DST). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-115; Condição 13 — Transição de horário de verão |
| **Pré-Condições** | Aplicação em uma zona com horário de verão; existe um lembrete único agendado para as 02:30 no dia em que o relógio adianta 1 hora à meia-noite. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Aguardar o horário do sistema atingir o momento correspondente ao lembrete. | A janela "Chegou a hora" é exibida sem travar a interface. |
| 2 | Observar a tela por alguns segundos após o alerta. | Nenhum alerta duplicado é exibido. |

**Pós-Condições**

- O lembrete é tratado uma única vez.

---

## Caso de Teste 108

| Campo | Valor |
| --- | --- |
| **ID** | 108 |
| **Título** | Deve exibir 14:00 no cartão e acionar o alerta coerentemente com o relógio atualizado quando o fuso do dispositivo muda de UTC-3 para UTC-4 após criar um lembrete para 15:00 (classe: alteração de fuso). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-116; Condição 13 — Alteração de fuso horário |
| **Pré-Condições** | Dispositivo no fuso UTC-3; existe um lembrete único criado para 15:00. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Alterar o fuso horário do sistema para UTC-4 e recarregar a página. | O horário exibido no cartão reflete a hora correspondente no novo fuso (14:00). |
| 2 | Aguardar o horário agendado conforme o relógio atualizado do dispositivo. | O alerta "Chegou a hora" é acionado de forma coerente com o horário exibido. |

**Pós-Condições**

- O horário do lembrete permanece consistente com o relógio do dispositivo.

---

## Caso de Teste 109

| Campo | Valor |
| --- | --- |
| **ID** | 109 |
| **Título** | Deve exibir imediatamente o alerta do lembrete vencido e sincronizar o relógio do topo quando o dispositivo acorda de 30 minutos de suspensão com lembrete agendado para 10 minutos (classe: vencimento durante suspensão ou hibernação). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-119; Condição 13 — Retomada após suspensão/hibernação |
| **Pré-Condições** | Existe o lembrete único "Tomar remédio" agendado para daqui a 10 minutos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Colocar o dispositivo em suspensão ou hibernação por 30 minutos. | O dispositivo entra em suspensão. |
| 2 | Acordar o dispositivo e voltar à aba da aplicação. | O alerta do lembrete vencido é exibido imediatamente e o relógio do topo sincroniza com a hora real do sistema operacional. |

**Pós-Condições**

- O lembrete sai de Lembretes futuros e fica em alerta.

---

## Caso de Teste 110

| Campo | Valor |
| --- | --- |
| **ID** | 110 |
| **Título** | Deve exibir o alerta sem recarregar a página quando o relógio do sistema é adiantado para 1 minuto depois do horário do lembrete (limite imediatamente acima do horário agendado). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-120, CT-051; Condição 13 — Ajuste manual do relógio (caso derivado do limite do horário) |
| **Pré-Condições** | Existe o lembrete único "Tomar remédio" agendado para daqui a 10 minutos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Adiantar o relógio do sistema para 1 minuto depois do horário agendado. | A janela "Chegou a hora" é exibida para "Tomar remédio" sem recarregar a página. |

**Pós-Condições**

- O lembrete sai de Lembretes futuros.

---

## Caso de Teste 111

| Campo | Valor |
| --- | --- |
| **ID** | 111 |
| **Título** | Deve manter o lembrete em Lembretes futuros, sem alerta, com "em menos de 1 min" quando o relógio do sistema é adiantado para 1 minuto antes do horário do lembrete (limite imediatamente abaixo do horário agendado). |
| **Técnica** | Análise de Valor Limite |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-120, CT-031; Condição 13 — Ajuste manual do relógio (caso derivado do limite do horário) |
| **Pré-Condições** | Existe o lembrete único "Tomar remédio" agendado para daqui a 10 minutos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Adiantar o relógio do sistema para 1 minuto antes do horário agendado. | Nenhum alerta é exibido e o card de tempo relativo exibe "em menos de 1 min". |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros.

---

## Caso de Teste 112

| Campo | Valor |
| --- | --- |
| **ID** | 112 |
| **Título** | Deve recalcular o chip de tempo relativo para "em 2 h" e não disparar alerta prematuro quando o relógio do sistema é alterado de 13:50 para 12:00 com lembrete agendado para as 14:00 (TD-11, R3: retrocesso do relógio + lembrete pendente). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-120; Condição 13; TD-11, regra R3 |
| **Pré-Condições** | Existe um lembrete único agendado para as 14:00 e o relógio do sistema marca 13:50. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Alterar manualmente o relógio do sistema para 12:00. | O chip de tempo relativo do cartão é recalculado para "em 2 h" e nenhum alerta é disparado prematuramente. |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros às 14:00.

---

## Caso de Teste 113

| Campo | Valor |
| --- | --- |
| **ID** | 113 |
| **Título** | Deve exibir o aviso de armazenamento cheio e preservar os lembretes existentes quando a gravação falha por cota esgotada ao salvar um lembrete (classe inválida: localStorage cheio). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-117; Condição 14 — Estouro de cota do localStorage |
| **Pré-Condições** | O armazenamento do navegador atingiu o limite de capacidade e já existe o lembrete "A" salvo. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete", preencher o formulário com dados válidos e clicar em "Salvar lembrete". | Exibe o aviso "Não foi possível salvar: armazenamento local cheio. Exclua lembretes antigos ou limpe o histórico de concluídos."; a tela não apresenta erro não tratado. |
| 2 | Recarregar a página. | Os lembretes salvos anteriormente (ex.: "A") permanecem intactos. |

**Pós-Condições**

- Os dados existentes permanecem íntegros.

---

## Caso de Teste 114

| Campo | Valor |
| --- | --- |
| **ID** | 114 |
| **Título** | Deve renderizar a lista sem congelar a interface e manter a rolagem fluida quando existem 300 lembretes futuros e 200 concluídos (representante de carga alta). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-118; Condição 14 — Responsividade com grande volume |
| **Pré-Condições** | Existem 300 lembretes futuros e 200 concluídos salvos no navegador. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | A lista é renderizada sem congelar a interface; o contador exibe "300 lembretes" e a seção exibe "Concluídos (200)". |
| 2 | Rolar a página pela lista. | A rolagem permanece fluida. |

**Pós-Condições**

- Os dados permanecem íntegros.

---

## Caso de Teste 115

| Campo | Valor |
| --- | --- |
| **ID** | 115 |
| **Título** | Deve exibir 29/02/2028 às 10:00 como próxima ocorrência, e não 01/03, quando o lembrete diário de 28/02/2028 é marcado como visto (ano bissexto) (TD-12, R1: diário + ano bissexto, 28/02 → 29/02). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-122; Condição 15; TD-12, regra R1 |
| **Pré-Condições** | Existe um lembrete diário agendado para 28/02/2028 às 10:00 com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é "29/02/2028" às 10:00 e não 01/03. |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros em 29/02/2028.

---

## Caso de Teste 116

| Campo | Valor |
| --- | --- |
| **ID** | 116 |
| **Título** | Deve agendar o lembrete diário para 01/03/2028 às 10:00 quando ele é marcado como visto em 29/02/2028 (ano bissexto; caso derivado do limite do dia 29/02) (TD-12, R2: diário + ano bissexto, 29/02 → 01/03). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-122; Condição 15 (caso derivado); TD-12, regra R2 |
| **Pré-Condições** | Existe um lembrete diário agendado para 29/02/2028 às 10:00 com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 01/03/2028 às 10:00. |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros em 01/03/2028.

---

## Caso de Teste 117

| Campo | Valor |
| --- | --- |
| **ID** | 117 |
| **Título** | Deve agendar o lembrete diário para 01/03/2029 às 10:00 quando ele é marcado como visto em 28/02/2029 (ano comum; caso derivado do limite de fevereiro) (TD-12, R3: diário + ano comum, 28/02 → 01/03). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-122; Condição 15 (caso derivado); TD-12, regra R3 |
| **Pré-Condições** | Existe um lembrete diário agendado para 28/02/2029 às 10:00 com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência exibida é 01/03/2029 às 10:00 (não existe 29/02/2029). |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros em 01/03/2029.

---

## Caso de Teste 118

| Campo | Valor |
| --- | --- |
| **ID** | 118 |
| **Título** | Deve agendar a próxima ocorrência para 29 de março quando o lembrete mensal criado em 29/02/2028 é marcado como visto (ano bissexto) (TD-12, R4: mensal + ano bissexto, criado em 29/02). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-123; Condição 15; TD-12, regra R4 |
| **Pré-Condições** | Existe um lembrete mensal criado em 29/02/2028 (ano bissexto), com o alerta de 29/02 aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A próxima ocorrência cai em 29/03/2028. |

**Pós-Condições**

- O lembrete permanece em Lembretes futuros em 29/03/2028.

---

## Caso de Teste 119

| Campo | Valor |
| --- | --- |
| **ID** | 119 |
| **Título** | Deve cair em 28 de fevereiro a ocorrência de fevereiro do ano comum subsequente quando o lembrete mensal criado em 29/02 avança, preservando o dia base 29 em março (TD-12, R5: mensal + ano comum subsequente, dia base 29 preservado). |
| **Técnica** | Tabela de Decisão |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-123; Condição 15; TD-12, regra R5 |
| **Pré-Condições** | Existe um lembrete mensal criado originalmente em 29/02/2028, agendado para 29/01/2029, com o alerta aberto. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "Marcar como visto". | A ocorrência de fevereiro cai em 28/02/2029. |
| 2 | Quando o novo alerta for exibido, clicar em "Marcar como visto" novamente. | A ocorrência seguinte volta ao dia base 29: 29/03/2029 (verificação derivada da preservação do dia base). |

**Pós-Condições**

- O lembrete mensal permanece em Lembretes futuros.

---

## Caso de Teste 120

| Campo | Valor |
| --- | --- |
| **ID** | 120 |
| **Título** | Deve normalizar o item com valores padrão e exibir a lista sem travar o carregamento dos demais lembretes quando um lembrete salvo não possui a propriedade "type" (classe inválida: propriedade obrigatória ausente). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-121; Condição 16 — Resiliência de schema |
| **Pré-Condições** | A chave do localStorage contém um lembrete sem a propriedade "type" e outro lembrete válido ("A"). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | O item sem "type" é normalizado com valores padrão, a lista é exibida e o lembrete válido "A" é carregado normalmente, sem travar o carregamento. |

**Pós-Condições**

- A aplicação permanece utilizável.

---

## Caso de Teste 121

| Campo | Valor |
| --- | --- |
| **ID** | 121 |
| **Título** | Deve normalizar o item com valores padrão e exibir a lista sem travar o carregamento dos demais lembretes quando um lembrete salvo não possui a propriedade "createdAt" (classe inválida: propriedade obrigatória ausente). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-121; Condição 16 — Resiliência de schema |
| **Pré-Condições** | A chave do localStorage contém um lembrete sem a propriedade "createdAt" e outro lembrete válido ("A"). |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Acessar a aplicação. | O item sem "createdAt" é normalizado com valores padrão, a lista é exibida e o lembrete válido "A" é carregado normalmente, sem travar o carregamento. |

**Pós-Condições**

- A aplicação permanece utilizável.

---

## Caso de Teste 122

| Campo | Valor |
| --- | --- |
| **ID** | 122 |
| **Título** | Deve exibir o texto literal no cartão e na janela de alerta, sem executar JavaScript, quando a descrição é "<img src=x onerror=alert('xss')>" (classe: injeção XSS na descrição). |
| **Técnica** | Partição de Equivalência |
| **Prioridade** | Alta |
| **Rastreabilidade** | CT-124; Condição 16 — Sanitização contra XSS |
| **Pré-Condições** | Aplicação Brasa Lembretes acessível no navegador e sem lembretes salvos. |

**Passos**

| Passo | Ação | Resultado Esperado |
| :---: | --- | --- |
| 1 | Clicar em "+ Novo lembrete". Preencher o título com "Teste XSS" e a descrição com "<img src=x onerror=alert('xss')>", informar a data e hora do próximo minuto e clicar em "Salvar lembrete". | O cartão exibe o texto literal da descrição, sem renderizar imagem, e nenhuma janela de alerta do navegador é aberta. |
| 2 | Aguardar o horário agendado. | A janela "Chegou a hora" exibe o texto literal da descrição; nenhum código JavaScript é executado e nenhuma janela de alerta indevida é disparada. |

**Pós-Condições**

- Nenhum script é executado e o texto é persistido sem alteração.
