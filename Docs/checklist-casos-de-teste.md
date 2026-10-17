# Checklist de casos de teste — Brasa Lembretes

Este documento consolida os 124 casos de teste formalizados no arquivo [Casos de Teste em Gherkin.md](./Casos%20de%20Teste%20em%20Gherkin.md).

| ID | Situação | Observação |
| --- | --- | --- |
| CT-001 | [ ] | Cadastro de lembrete único obrigatório |
| CT-002 | [ ] | Cadastro de lembrete único com descrição |
| CT-003 | [ ] | Rejeitar título vazio ou composto apenas por espaços |
| CT-004 | [ ] | Rejeitar lembrete sem data e hora |
| CT-005 | [ ] | Rejeitar data e hora no passado |
| CT-006 | [ ] | Aceitar data e hora futuras, incluindo o limite mínimo |
| CT-007 | [ ] | Exibir erros simultâneos de título e data |
| CT-008 | [ ] | Limite de caracteres do título |
| CT-009 | [ ] | Limite de caracteres da descrição |
| CT-010 | [ ] | Colar texto maior que o limite no título |
| CT-011 | [ ] | Descrição composta apenas por espaços |
| CT-012 | [ ] | Remoção de espaços nas extremidades do título |
| CT-013 | [ ] | Caracteres especiais e HTML exibidos como texto |
| CT-014 | [ ] | Emojis e acentuação preservados |
| CT-015 | [ ] | Quebras de linha da descrição preservadas |
| CT-016 | [ ] | Título longo sem espaços e layout estável |
| CT-017 | [ ] | Fechar formulário sem salvar |
| CT-018 | [ ] | Reabertura do formulário sem dados anteriores |
| CT-019 | [ ] | Salvar pressionando Enter no campo de título |
| CT-020 | [ ] | Alternar entre único e recorrente |
| CT-021 | [ ] | Criar lembrete recorrente em cada frequência |
| CT-022 | [ ] | Lembrete recorrente aparece uma única vez na lista |
| CT-023 | [ ] | Estado vazio na primeira visita |
| CT-024 | [ ] | Botão “Criar primeiro lembrete” abre o formulário |
| CT-025 | [ ] | Carregar exemplos |
| CT-026 | [ ] | Ordenação do mais próximo para o mais distante |
| CT-027 | [ ] | Agrupamento por dia com rótulos Hoje/Amanhã |
| CT-028 | [ ] | Mesmos dias agrupados por horário |
| CT-029 | [ ] | Lembretes em lados opostos da meia-noite ficam no mesmo grupo |
| CT-030 | [ ] | Contador no singular e no plural |
| CT-031 | [ ] | Texto de tempo relativo no cartão |
| CT-032 | [ ] | Lembrete futuro não exibe alerta |
| CT-033 | [ ] | Cartão exibe horário em formato 24 horas |
| CT-034 | [ ] | Abrir edição com dados preenchidos |
| CT-035 | [ ] | Alterar título do lembrete |
| CT-036 | [ ] | Alterar data e hora reordena a lista |
| CT-037 | [ ] | Converter lembrete único em recorrente |
| CT-038 | [ ] | Converter lembrete recorrente em único |
| CT-039 | [ ] | Cancelar edição sem salvar alterações |
| CT-040 | [ ] | Verificação de exclusão com confirmação |
| CT-041 | [ ] | Exclusão de lembrete único |
| CT-042 | [ ] | Exclusão de lembrete recorrente |
| CT-043 | [ ] | Cancelar exclusão sem excluir |
| CT-044 | [ ] | Alerta dispara na hora correta |
| CT-045 | [ ] | Alerta exibe mensagem e ações |
| CT-046 | [ ] | Marcar como visto no alerta |
| CT-047 | [ ] | Adiar alerta em 5 minutos |
| CT-048 | [ ] | Adiar alerta em 15 minutos |
| CT-049 | [ ] | Repetição de alerta durante a mesma janela |
| CT-050 | [ ] | Alerta não reaparece após confirmação |
| CT-051 | [ ] | Som é acionado após interação inicial |
| CT-052 | [ ] | Som não é disparado antes da interação |
| CT-053 | [ ] | Alerta fecha corretamente após ação |
| CT-054 | [ ] | Lembrete concluído entra no histórico |
| CT-055 | [ ] | Histórico exibe itens concluidos em ordem |
| CT-056 | [ ] | Histórico mantém distinção de lembretes cancelados |
| CT-057 | [ ] | Excluir lembrete concluído do histórico |
| CT-058 | [ ] | Histórico de itens concluídos permanece acessível |
| CT-059 | [ ] | Contador de concluídos exibe valor correto |
| CT-060 | [ ] | Lembrete de exemplo preserva tipo e recorrência |
| CT-061 | [ ] | Estado vazio após remoção dos últimos lembretes |
| CT-062 | [ ] | Lembrar estado persistido em refresh |
| CT-063 | [ ] | Persistência localStorage ao criar lembrete |
| CT-064 | [ ] | Persistência localStorage ao editar lembrete |
| CT-065 | [ ] | Persistência localStorage ao excluir lembrete |
| CT-066 | [ ] | Recuperação de dados armazenados após reload |
| CT-067 | [ ] | Dados corrompidos não quebram a aplicação |
| CT-068 | [ ] | Estrutura de schema diferente é normalizada |
| CT-069 | [ ] | Campos ausentes em lembretes antigos são preenchidos |
| CT-070 | [ ] | Ordenação após reload preserva cronologia |
| CT-071 | [ ] | Carregamento de dados com lembretes em ordem |
| CT-072 | [ ] | Proteção contra payload inválido no localStorage |
| CT-073 | [ ] | Tratamento de storage indisponível |
| CT-074 | [ ] | Tempo relativo atualiza sem recarregar a página |
| CT-075 | [ ] | Atualização das tags de recorrência em tempo real |
| CT-076 | [ ] | Fechamento do modal não perde estado |
| CT-077 | [ ] | Foco em campo inválido ao salvar |
| CT-078 | [ ] | Validação de título com espaços e HTML |
| CT-079 | [ ] | Validação de descrição com script malicioso |
| CT-080 | [ ] | Ordenação por prioridade de proximidade |
| CT-081 | [ ] | Regras de borda de data e hora em fim de mês |
| CT-082 | [ ] | Lembrete diário avança corretamente em dia útil |
| CT-083 | [ ] | Lembrete semanal respeita dias da semana |
| CT-084 | [ ] | Lembrete mensal respeita calendário |
| CT-085 | [ ] | Lembrete diário em ano bissexto |
| CT-086 | [ ] | Recorrência mensal em 29 de fevereiro |
| CT-087 | [ ] | Atualização de recorrência após avanço manual |
| CT-088 | [ ] | Recalcular próxima ocorrência após marcar como visto |
| CT-089 | [ ] | Conservar histórico de recorrência sem duplicar |
| CT-090 | [ ] | Montagem da lista com grande volume de dados |
| CT-091 | [ ] | Performance com 300 lembretes futuros |
| CT-092 | [ ] | Responsividade da interface em alta carga |
| CT-093 | [ ] | Fuso horário local não distorce o agendamento |
| CT-094 | [ ] | Alteração de fuso horário do dispositivo |
| CT-095 | [ ] | Tratamento de hora de verão |
| CT-096 | [ ] | Ajuste manual do relógio para o passado |
| CT-097 | [ ] | Retomada após suspensão ou hibernação |
| CT-098 | [ ] | Cota do navegador esgotada em localStorage |
| CT-099 | [ ] | Compatibilidade com navegador restritivo |
| CT-100 | [ ] | Carregamento de dados do storage com propriedades ausentes |
| CT-101 | [ ] | Sanitização de script em campo de descrição |
| CT-102 | [ ] | Prevenção de XSS em caso de entrada maliciosa |
| CT-103 | [ ] | Estado visual estável com muitos itens |
| CT-104 | [ ] | Acesso por teclado no formulário |
| CT-105 | [ ] | Célula de texto exibe overflow correto |
| CT-106 | [ ] | Regressão em alteração de recorrência |
| CT-107 | [ ] | Reiterar comportamento de alertas após reload |
| CT-108 | [ ] | Ordenação do bloco “Próximo lembrete” |
| CT-109 | [ ] | Campos vazios não disparam a aplicação |
| CT-110 | [ ] | Lembrete futuro não entra em status concluído |
| CT-111 | [ ] | Lembrete concluído não reaparece na lista |
| CT-112 | [ ] | Reuse da seção de histórico após exclusão |
| CT-113 | [ ] | Persistência de conclusão no histórico |
| CT-114 | [ ] | Campo de data e hora aceita limite mínimo |
| CT-115 | [ ] | Conformidade com transição de horário de verão |
| CT-116 | [ ] | Mudança de fuso horário com lembretes pendentes |
| CT-117 | [ ] | Tratamento de cota esgotada no navegador |
| CT-118 | [ ] | Responsividade da interface com grande volume |
| CT-119 | [ ] | Retomada após suspensão ou hibernação |
| CT-120 | [ ] | Ajuste de relógio para o passado |
| CT-121 | [ ] | Carregamento de dados salvos com propriedades obrigatórias ausentes |
| CT-122 | [ ] | Avanço de lembrete diário em ano bissexto |
| CT-123 | [ ] | Recorrência mensal em 29 de fevereiro |
| CT-124 | [ ] | Sanitização de script (XSS) no campo de descrição |


