# Experimento com IA - Desafio em grupo 3

A título de fazer um experimento, solicitamos ao Claude Code que, com base no documento de casos de testes anexado (no formato ISO 29119-3), e sendo um analista de testes que não  possui muito tempo disponível para realização dos testes e precisa garantir a qualidade, dentro dos 124 casos de testes criados listasse os 50 mais críticos e importantes de serem validados.

O resultado foi trazido separado por módulos, e a justificativa apresentada de forma coerente. Abaixo, seguem o prompt, a justificativa e a lista definida.

### Prompt utilizado:

“Você é um analista de testes sênior e está com pouco tempo para fazer a validação desses cenários que criou. Analise esses cenários de testes, e separe os 50 testes mais importantes e críticos para serem validados, liste os títulos.”

### Justificativa:

“Selecionei os 50 casos por risco. Entram os fluxos que, se falharem, o lembrete não cumpre sua função: criar, avisar na hora certa, concluir, adiar, recorrência e não perder dados. Também entram as validações de entrada, as brechas de segurança e os limites de data.

Ficaram de fora os casos mais redundantes: os limites repetidos de contador, a descrição e os textos de tempo relativo, as tags de frequência restantes, os demais meses de recorrência e as combinações do alerta (86 a 89). Também ficaram de fora o layout em outras larguras, a carga alta (114), a perda de rascunho (105) e as variações de edição e exclusão.

Se sobrar tempo, o primeiro a incluir é o 114, de carga alta. Os casos 49 e 53 (recorrência mensal em ano bissexto) e o 15 (descrição com 501 caracteres) vêm em seguida.”

### Lista com os 50 testes, separados por módulos:

- Cadastro e validação (11 casos de testes)

1: Deve rejeitar e exibir a mensagem “Informe um título para o lembrete.” quando o título tem 0 caracteres.
2: Deve rejeitar e exibir a mensagem “Informe um título para o lembrete.” quando o título contém apenas espaços.
6: Deve aceitar o título e exibir o contador 80/80 quando o título informado tem 80 caracteres. 
7: Deve limitar o campo a 80 caracteres e exibir o contador “80/80” quando 81 caracteres são digitados. 
16: Deve rejeitar e exibir a mensagem “Informe a data e a hora do lembrete.” quando a data e hora informada é vazia. 
17: Deve rejeitar e exibir a mensagem “Escolha uma data e hora no futuro.” quando a data e hora informada é 1 dia atrás.
19: Deve rejeitar e exibir a mensagem “Escolha uma data e hora no futuro.” quando a data e hora informada é o minuto atual.
20: Deve criar o lembrete e exibir o horário informado quando a data e hora é o próximo minuto.
21: Deve criar o lembrete único quando título e data e hora futura (daqui a 1 hora) são válidos.
22: Deve exibir as duas mensagens de erro e focar o título quando título e data e hora estão vazios.
23: Deve exibir a tag “Recorrente · Diário” quando o lembrete é criado como recorrente com a frequência “Todos os dias”.

- Edição, exclusão e listagem (7 casos de testes)

26: Deve exibir “Nenhum lembrete agendado” e deixar o contador vazio quando não existem lembretes futuros.
80: Deve rejeitar a edição e exibir a mensagem “Informe um título para o lembrete.” quando o título é alterado para vazio.
82: Deve rejeitar a edição e exibir a mensagem “Escolha uma data e hora no futuro.” quando a data e hora é alterada para 1 hora atrás.
84: Deve exibir o chip “Recorrente · Semanal” quando um lembrete único é convertido em recorrente com a frequência “Toda semana”.
96: Deve excluir “Dentista” e manter “Mercado” quando a exclusão é confirmada.
98: Deve remover o lembrete diário e não exibir alerta no horário original quando a exclusão é confirmada.
99: Deve exibir o estado vazio quando o último lembrete é excluído com confirmação.

- Alerta no horário (5 casos de testes)

91: Deve exibir o segundo alerta imediatamente e ocultar o indicador da fila quando o primeiro é marcado como visto.
103: Deve exibir o alerta sem som e sem erro quando não houve interação prévia com a página.
106: Deve exibir o alerta, atualizar o título da aba e focar “Marcar como visto” quando o lembrete vence sem formulário aberto.
109: Deve exibir imediatamente o alerta do lembrete vencido e sincronizar o relógio do topo quando o dispositivo acorda de 30 minutos de suspensão.
110: Deve exibir o alerta sem recarregar a página quando o relógio do sistema é adiantado para 1 minuto depois do horário do lembrete.

- Marcar como visto e recorrência (8 casos de testes)

42: Deve avançar o lembrete diário para 16/12/2026 às 09:00 quando ele é marcado como visto em 15/12/2026.
43: Deve avançar o lembrete diário para 01/01/2027 às 09:00 quando ele é marcado como visto em 31/12/2026.
46: Deve avançar o lembrete mensal para 15/11/2026 às 09:00 quando ele é marcado como visto em 15/10/2026.
48: Deve agendar a próxima ocorrência para 28/02/2027 e depois 31/03/2027 quando o lembrete mensal criado no dia 31 é marcado como visto em 31/01/2027.
54: Deve exibir a próxima ocorrência no futuro e não reabrir alertas das ocorrências perdidas quando o lembrete diário está atrasado há 5 dias e é marcado como visto.
90: Deve mover o lembrete único para “Concluídos (1)” quando ele é marcado como visto.
115: Deve exibir 29/02/2028 às 10:00 como próxima ocorrência, e não 01/03, quando o lembrete diário de 28/02/2028 é marcado como visto.
119: Deve cair em 28 de fevereiro a ocorrência de fevereiro do ano comum subsequente quando o lembrete mensal criado em 29/02 avança, preservando o dia base 29 em março.

- Adiamento (6 casos de testes)

55: Deve adiar o lembrete para agora + 10 minutos (segundos zerados) quando a opção rápida “+10 min” é escolhida.
57: Deve adiar o lembrete para amanhã às 09:00 quando a opção rápida “Amanhã às 9h” é escolhida.
58: Deve rejeitar e exibir a mensagem “Escolha a nova data e hora.” quando o adiamento personalizado é vazio.
61: Deve rejeitar e exibir a mensagem “A nova data precisa estar no futuro.” quando o adiamento personalizado é o minuto atual.
93: Deve exibir o segundo alerta e devolver o primeiro lembrete a Lembretes futuros quando o primeiro é adiado com “+10 min”.
95: Deve agendar a próxima ocorrência para a segunda-feira seguinte às 09:00 quando um lembrete semanal adiado com “+1 hora” é marcado como visto.

- Histórico (1 caso de teste)

66: Deve exibir “Concluídos (1)” quando existem 1 lembretes concluídos.

- Persistência e dados (6 casos de testes)

72: Deve exibir o aviso “Não foi possível usar o armazenamento do navegador” e carregar a lista vazia quando o valor salvo é JSON inválido.
73: Deve carregar a lista vazia sem erro na tela quando o valor salvo é um objeto e não uma lista.
74: Deve exibir o aviso de armazenamento indisponível e manter o lembrete apenas na sessão quando o localStorage está bloqueado.
104: Deve carregar os lembretes “A” e “B” sem aviso quando o armazenamento contém uma lista válida.
113: Deve exibir o aviso de armazenamento cheio e preservar os lembretes existentes quando a gravação falha por cota esgotada ao salvar um lembrete.
120: Deve normalizar o item com valores padrão e exibir a lista sem travar o carregamento dos demais lembretes quando um lembrete salvo não possui a propriedade “type”.

- Segurança (2 casos de testes)

68: Deve exibir o texto literal sem executar HTML ou script quando o título contém marcação HTML.
122: Deve exibir o texto literal no cartão e na janela de alerta, sem executar JavaScript, quando a descrição é <img src=x onerror=alert('xss')>.

- Tempo e dispositivo (3 casos de testes)

107: Deve exibir o alerta sem travar a interface e sem duplicidade quando o lembrete das 02:30 está agendado no dia da transição do horário de verão.
108: Deve exibir 14:00 no cartão e acionar o alerta coerentemente com o relógio atualizado quando o fuso do dispositivo muda de UTC-3 para UTC-4 após criar um lembrete para 15:00.
112: Deve recalcular o chip de tempo relativo para “em 2 h” e não disparar alerta prematuro quando o relógio do sistema é alterado de 13:50 para 12:00 com lembrete agendado para as 14:00.

- Layout (1 caso de teste)

75: Deve exibir o cartão em uma coluna, o relógio em linha própria e o formulário colado à parte inferior quando o viewport tem 360 px.
