# Casos de Teste em Gherkin — Brasa Lembretes

## 1 - Cadastro de lembrete

```gherkin
# language: pt
Funcionalidade: Cadastro de lembrete
  Como um usuário do Brasa Lembretes
  Desejo cadastrar lembretes com título, descrição e data/hora
  Para ser avisado na hora certa   
```
### CT-001
```gherkin
  @CT-001
  Cenário: Criar lembrete único apenas com os campos obrigatórios
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Pagar boleto do condomínio"
    E informo uma data e hora daqui a 1 hora
    E clico em "Salvar lembrete"
    Então o formulário é fechado
    E vejo o aviso "Lembrete criado para" seguido da data e hora informadas
    E o lembrete aparece em "Lembretes futuros" com o card "Único"
    E o contador exibe "1 lembrete"
    E o bloco "Próximo lembrete" exibe "Pagar boleto do condomínio"

```
### CT-002
```gherkin
  @CT-002
  Cenário: Criar lembrete único com descrição
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Reunião com cliente"
    E preencho a descrição com "Levar a proposta impressa"
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão do lembrete exibe o título "Reunião com cliente"
    E exibe a descrição "Levar a proposta impressa"

```
### CT-003
```gherkin
  @CT-003
  Cenário: Rejeitar título vazio ou composto apenas por espaços
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com vazio ou com espaços
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então vejo a mensagem de erro "Informe um título para o lembrete."
    E o campo de título fica marcado como inválido
    E o foco é levado ao campo de título
    E nenhum lembrete é criado


```
### CT-004
```gherkin
  @CT-004 
  Cenário: Rejeitar lembrete sem data e hora
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Sem data"
    E deixo o campo de data e hora vazio
    E clico em "Salvar lembrete"
    Então vejo a mensagem de erro "Informe a data e a hora do lembrete."
    E o campo de data e hora fica marcado como inválido
    E nenhum lembrete é criado

```
### CT-005
```gherkin
  @CT-005
  Cenário: Rejeitar data e hora que não estão no futuro
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Teste de data"
    E informo a data e hora "<data_hora>"
    E clico em "Salvar lembrete"
    Então vejo a mensagem de erro "Escolha uma data e hora no futuro."
    E nenhum lembrete é criado
    

```
### CT-006
```gherkin
  @CT-006 
  Cenário: Aceitar data e hora futuras, incluindo o limite mínimo
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Teste de data futura"
    E informo a data e hora "<data_hora>"
    E clico em "Salvar lembrete"
    Então o lembrete é criado com sucesso
    E o horário exibido no cartão corresponde ao informado
   

```
### CT-007
```gherkin
  @CT-007
  Cenário: Exibir os dois erros ao mesmo tempo quando título e data estão inválidos
    Dado que acesso a aplicação Brasa Lembretes
    Quando clico em "+ Novo lembrete"
    E deixo o título e a data e hora vazios
    E clico em "Salvar lembrete"
    Então vejo a mensagem "Informe um título para o lembrete."
    E vejo a mensagem "Informe a data e a hora do lembrete."
    E o foco é levado ao primeiro campo inválido, o título

```
### CT-008
```gherkin
  @CT-008 
  Cenário: Limite de caracteres do título (máximo 80)
    Dado que acesso a aplicação Brasa Lembretes 
    Quando clico em "+ Novo lembrete"
    E digito um título com <digitados> caracteres
    Então o contador do título exibe "<contador>/80"
    E o campo contém <aceitos> caracteres


```
### CT-009
```gherkin
  @CT-009 
 Cenário: Limite de caracteres da descrição (máximo 500)
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E digito uma descrição com <digitados> caracteres
    Então o contador da descrição exibe "<contador>/500"
    E o campo contém <aceitos> caracteres


```
### CT-010
```gherkin
  @CT-010 
  Cenário: Colar texto maior que o limite no título
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E colo no campo de título um texto com 120 caracteres
    Então o campo de título mantém apenas os primeiros 80 caracteres
    E o contador exibe "80/80"

```
### CT-011
```gherkin
  @CT-011 
  Cenário: Descrição composta apenas por espaços é tratada como vazia
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Sem descrição"
    E preencho a descrição com "     "
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão do lembrete não exibe parágrafo de descrição

```
### CT-012
```gherkin
  @CT-012 
  Cenário: Espaços nas extremidades do título são removidos
    Dado que acesso a aplicação Brasa Lembretes        
    Quando clico em "+ Novo lembrete"
    E preencho o título com "   Ligar para o banco   "
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe o título "Ligar para o banco" sem espaços nas pontas

```
### CT-013
```gherkin
  @CT-013
  Esquema do Cenário: Caracteres especiais e HTML são exibidos como texto
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "<titulo>"
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe exatamente o texto "<titulo>"
    E nenhum código HTML ou script é executado
    E nenhuma janela de alerta do navegador é aberta
 
```
### CT-014
```gherkin
  @CT-014
  Cenário: Emojis e acentuação são preservados
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Aniversário da vovó 🎂"
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe "Aniversário da vovó 🎂" corretamente

```
### CT-015
```gherkin
  @CT-015
  Cenário: Quebras de linha da descrição são preservadas
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Lista de compras"
    E preencho a descrição com três linhas separadas por Enter
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe a descrição em três linhas

```
### CT-016
```gherkin
  @CT-016
  Cenário: Título longo sem espaços não quebra o layout
    Dado que acesso a aplicação Brasa Lembretes    
    Quando crio um lembrete com título de 80 letras "A" sem espaços
    Então o texto quebra dentro do cartão
    E a página não apresenta rolagem horizontal

```
### CT-017
```gherkin
  @CT-017
  Cenário: Fechar o formulário sem salvar
    Dado que abri o formulário de novo lembrete
    E preenchi o título com "Rascunho"
    Quando Fechar o formulário sem salvar
    Então o formulário é fechado
    E nenhum lembrete é criado

```
### CT-018
```gherkin
  @CT-018 
  Cenário: Formulário reaberto não mantém dados nem erros anteriores
    Dado que tentei salvar um lembrete com título vazio e vi a mensagem de erro
    E fechei o formulário
    Quando clico em "+ Novo lembrete" novamente
    Então todos os campos estão vazios
    E nenhuma mensagem de erro é exibida
    E os contadores exibem "0/80" e "0/500"

```
### CT-019
```gherkin
  @CT-019 
  Cenário: Salvar o formulário pressionando Enter no campo de título     
    Dado que abri o formulário de novo lembrete
    E preenchi título e data e hora futura
    Quando pressiono Enter com o foco no campo de título
    Então o lembrete é criado
```

---

## 2 - Lembretes recorrentes

```gherkin
# language: pt
Funcionalidade: Lembretes recorrentes
  Como um usuário
  Desejo criar lembretes que se repetem
  Para não precisar recadastrar atividades periódicas
   

```
### CT-020
```gherkin
  @CT-020
  Cenário: Alternar entre Único e Recorrente exibe e oculta a frequência
    Dado que acesso a aplicação Brasa Lembretes
    E que não existem lembretes salvos no navegador
    Quando clico em "+ Novo lembrete"
    Então o campo "Frequência" está oculto
    E a opção "Único" está selecionada
    Quando seleciono "Recorrente"
    Então o campo "Frequência" é exibido com o valor "Todos os dias"
    Quando seleciono "Único"
    Então o campo "Frequência" volta a ficar oculto

```
### CT-021
```gherkin
  @CT-021
  Esquema do Cenário: Criar lembrete recorrente em cada frequência
    Dado que acesso a aplicação Brasa Lembretes
    E que não existem lembretes salvos no navegador
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Lembrete <frequencia>"
    E seleciono "Recorrente"
    E escolho a frequência "<opcao>"
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe a tag "Recorrente · Frequencia"

    Exemplos:
      | frequencia | opcao         | tag     |
      | diário     | Todos os dias | Diário  |
      | semanal    | Toda semana   | Semanal |
      | mensal     | Todo mês      | Mensal  |

```
### CT-022
```gherkin
  @CT-022
  Cenário: Lembrete recorrente aparece uma única vez na lista de futuros
    Dado que criei um lembrete diário para amanhã às 08:00
    Então a lista exibe apenas 1 cartão para ele
    E o contador exibe "1 lembrete"
```

---

## 3 - Listagem de lembretes futuros

```gherkin
# language: pt
Funcionalidade: Listagem de lembretes futuros
  Como um usuário
  Desejo ver meus lembretes ordenados e agrupados por dia
  Para saber o que vem pela frente    

```
### CT-023
```gherkin
  @CT-023 
  Cenário: Estado vazio na primeira visita
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Então vejo a mensagem "Nenhum lembrete agendado"
    E vejo os botões "Criar primeiro lembrete" e "Carregar exemplos"
    E o bloco "Próximo lembrete" está oculto
    E o contador de lembretes está vazio
    E a seção "Concluídos" está oculta

```
### CT-024
```gherkin
  @CT-024
  Cenário: Botão "Criar primeiro lembrete" abre o formulário
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Quando clico em "Criar primeiro lembrete"
    Então o formulário "Novo lembrete" é exibido

```
### CT-025
```gherkin
  @CT-025
  Cenário: Carregar exemplos
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Quando clico em "Carregar exemplos"
    Então vejo o aviso "3 lembretes de exemplo adicionados"
    E vejo os lembretes "(exemplo) Tomar água", "(exemplo) Reunião semanal do time" e "(exemplo) Pagar aluguel"
    E o estado vazio deixa de ser exibido
    E "(exemplo) Tomar água" é único, "(exemplo) Reunião semanal do time" é semanal e "(exemplo) Pagar aluguel" é mensal

```
### CT-026
```gherkin
  @CT-026 
  Cenário: Ordenação do mais próximo para o mais distante
    Dado que cadastrei os lembretes nesta ordem:
      | título | quando         |
      | C      | daqui a 3 dias |
      | A      | daqui a 1 hora |
      | B      | daqui a 2 dias |
    Então a lista exibe os lembretes na ordem A, B, C
    E o bloco "Próximo lembrete" exibe "A"

```
### CT-027
```gherkin
  @CT-027 
  Cenário: Agrupamento por dia com rótulos "Hoje" e "Amanhã"
    Dado que existem lembretes para hoje, amanhã e daqui a 5 dias
    Então vejo três grupos de dia
    E o primeiro grupo tem o rótulo "Hoje" seguido da data por extenso
    E o segundo grupo tem o rótulo "Amanhã" seguido da data por extenso
    E o terceiro grupo exibe apenas o dia da semana e a data por extenso

```
### CT-028
```gherkin
  @CT-028
  Cenário: Lembretes no mesmo dia ficam no mesmo grupo, ordenados por horário
    Dado que existem lembretes amanhã às 15:00, 09:00 e 12:30
    Então há um único grupo "Amanhã"
    E os cartões aparecem na ordem 09:00, 12:30, 15:00

```
### CT-029
```gherkin
  @CT-029 
  enário: Lembretes em lados opostos da meia-noite ficam em grupos diferentes
    Dado que existem lembretes às <horario_1> e às <horario_2> do mesmo dia civil seguinte
    Então eles pertencem ao mesmo grupo

    Exemplos:
      | horario_1 | horario_2 |
      | 00:00     | 23:59     |

```
### CT-030
```gherkin
  @CT-030
  Cenário: Contador no singular e no plural
    Dado que existem <quantidade> lembretes futuros
    Então o contador exibe "<texto>"

    Exemplos:
      | quantidade | texto         |
      | 1          | 1 lembrete    |
      | 2          | 2 lembretes   |
      | 10         | 10 lembretes  |

```
### CT-031
```gherkin
  @CT-031 
  Cenário: Texto de tempo relativo no cartão
    Dado que existe um lembrete agendado para <distancia>
    Então o card de tempo relativo exibe "<texto>"

    Exemplos:
      | distancia                | texto               |
      | daqui a 30 segundos      | em menos de 1 min   |
      | daqui a 1 minuto         | em menos de 1 min   |
      | daqui a 45 minutos       | em 45 min           |
      | daqui a 2 horas          | em 2 h              |
      | daqui a 2 horas e 15 min | em 2 h 15 min       |
      | daqui a 3 dias           | em 3 d              |
      | daqui a 1 dia e 4 horas  | em 1 d 4 h          |

```
### CT-032
```gherkin
  @CT-032
  Cenário: Lembrete futuro não exibe alerta
    Dado que existe um lembrete agendado para daqui a 1 hora
    Então nenhum alerta "Chegou a hora" é exibido

```
### CT-033
```gherkin
  @CT-033 
  Cenário: Cartão exibe o horário no formato 24 horas
    Dado que existe um lembrete agendado para amanhã às 14:05
    Então o cartão exibe o horário "14:05"
```

---

## 4 - Edição de lembrete

```gherkin
# language: pt
Funcionalidade: Edição de lembrete
  Como um usuário
  Desejo alterar um lembrete já cadastrado
  Para corrigir ou atualizar informações

```
### CT-034
```gherkin
  @CT-034
  Cenário: Abrir a edição com os dados preenchidos
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    Quando clico em "Editar" no cartão "Dentista"
    Então o formulário abre com o título "Editar lembrete"
    E o botão de salvar exibe "Salvar alterações"
    E o campo título contém "Dentista"
    E o campo descrição contém "Levar exames"
    E a opção "Único" está selecionada
    E a data e hora contêm o valor agendado
    E os contadores refletem o tamanho dos textos

```
### CT-035
```gherkin
  @CT-035
  Cenário: Alterar o título de um lembrete
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    Quando clico em "Editar" no cartão "Dentista"
    E altero o título para "Dentista - retorno"
    E clico em "Salvar alterações"
    Então vejo o aviso "Lembrete atualizado"
    E o cartão exibe "Dentista - retorno"
    E continua existindo apenas 1 cartão

```
### CT-036
```gherkin
  @CT-036
  Cenário: Alterar data e hora reordena a lista
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    E que existe também o lembrete "Mercado" agendado para daqui a 1 dia
    Quando edito "Dentista" para daqui a 12 horas
    Então "Dentista" passa a aparecer antes de "Mercado"
    E o bloco "Próximo lembrete" exibe "Dentista"

```
### CT-037
```gherkin
  @CT-037
  Cenário: Converter lembrete único em recorrente
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    Quando clico em "Editar" no cartão "Dentista"
    E seleciono "Recorrente"
    E escolho a frequência "Toda semana"
    E clico em "Salvar alterações"
    Então o cartão exibe o chip "Recorrente · Semanal"

```
### CT-038
```gherkin
  @CT-038
  Cenário: Converter lembrete recorrente em único
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    E que "Dentista" foi convertido em recorrente mensal
    Quando clico em "Editar" no cartão "Dentista"
    Então a opção "Recorrente" está selecionada e a frequência é "Todo mês"
    Quando seleciono "Único"
    E clico em "Salvar alterações"
    Então o cartão exibe o chip "Único"

```
### CT-039
```gherkin
  @CT-039
  Cenário: Validações também valem na edição
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    Quando clico em "Editar" no cartão "Dentista"
    E altero <campo> para <valor>
    E clico em "Salvar alterações"
    Então vejo a mensagem "<mensagem>"
    E o lembrete permanece com os dados anteriores

    Exemplos:
      | campo          | valor          | mensagem                              |
      | o título       | vazio          | Informe um título para o lembrete.    |
      | a data e hora  | vazia          | Informe a data e a hora do lembrete.  |
      | a data e hora  | 1 hora atrás   | Escolha uma data e hora no futuro.    |

```
### CT-040
```gherkin
  @CT-040
  Cenário: Cancelar a edição descarta as alterações
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    Quando clico em "Editar" no cartão "Dentista"
    E altero o título para "Outro título"
    E clico em "Cancelar"
    Então o cartão continua exibindo "Dentista"

```
### CT-041
```gherkin
  @CT-041
  Cenário: Abrir "Novo lembrete" depois de cancelar uma edição não traz dados do lembrete editado
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    E que abri a edição de "Dentista" e cancelei
    Quando clico em "+ Novo lembrete"
    Então o título do formulário é "Novo lembrete"
    E todos os campos estão vazios
    E, ao salvar, é criado um novo lembrete e "Dentista" não é alterado

```
### CT-042
```gherkin
  @CT-042
  Cenário: Editar um lembrete que já foi adiado
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete único "Dentista" com descrição "Levar exames" agendado para daqui a 2 dias
    E que "Dentista" foi adiado uma vez e exibe o chip "Adiado 1x"
    Quando edito o título e salvo
    Então o cartão mantém ou zera o contador de adiamentos de forma coerente
    # Observação: o código não zera "snoozes" na edição. Avaliar se o comportamento é o desejado.

```
### CT-043
```gherkin
  @CT-043
  Cenário: Editar a data de um lembrete mensal criado no dia 31
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete mensal agendado para o dia 31
    Quando edito a data para o dia 15 do mês seguinte
    E o lembrete é marcado como visto na data
    Então a próxima ocorrência cai no dia 15 do mês seguinte
```

---

## 5 - Exclusão de lembrete

```gherkin
# language: pt
Funcionalidade: Exclusão de lembrete
  Como um usuário
  Desejo excluir lembretes que não preciso mais
  Para manter minha lista organizada

```
### CT-044
```gherkin
  @CT-044
  Cenário: Excluir lembrete com confirmação
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes futuros "Dentista" e "Mercado"
    Quando clico em "Excluir" no cartão "Dentista"
    Então o cartão exibe "Excluir este lembrete?" com os botões "Excluir" e "Cancelar"
    Quando clico em "Excluir" na confirmação
    Então vejo o aviso "Lembrete excluído"
    E "Dentista" não aparece mais na lista
    E "Mercado" continua na lista

```
### CT-045
```gherkin
  @CT-045
  Cenário: Cancelar a exclusão
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes futuros "Dentista" e "Mercado"
    Quando clico em "Excluir" no cartão "Dentista"
    E clico em "Cancelar" na confirmação
    Então o cartão volta a exibir os botões "Editar" e "Excluir"
    E "Dentista" continua na lista

```
### CT-046
```gherkin
  @CT-046
  Cenário: Apenas uma confirmação de exclusão fica aberta por vez
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes futuros "Dentista" e "Mercado"
    Quando clico em "Excluir" no cartão "Dentista"
    E clico em "Excluir" no cartão "Mercado"
    Então apenas o cartão "Mercado" exibe a pergunta de confirmação
    E o cartão "Dentista" volta ao estado normal

```
### CT-047
```gherkin
  @CT-047
  Cenário: Excluir o último lembrete exibe o estado vazio
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes futuros "Dentista" e "Mercado"
    E que "Mercado" já foi excluído
    Quando excluo "Dentista" confirmando
    Então vejo "Nenhum lembrete agendado"
    E o bloco "Próximo lembrete" fica oculto

```
### CT-048
```gherkin
  @CT-048
  Cenário: A exclusão persiste após recarregar a página
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes futuros "Dentista" e "Mercado"
    Quando excluo "Dentista" confirmando
    E recarrego a página
    Então "Dentista" não aparece na lista

```
### CT-049
```gherkin
  @CT-049
  Cenário: Excluir lembrete recorrente remove todas as ocorrências futuras
    Dado que acesso a aplicação Brasa Lembretes
    E que existe o lembrete diário "Beber água"
    Quando excluo "Beber água" confirmando
    Então "Beber água" não aparece na lista
    E não é exibido alerta no horário original

```
### CT-050
```gherkin
  @CT-050
  Cenário: Excluir um lembrete não altera o histórico de concluídos
    Dado que acesso a aplicação Brasa Lembretes
    E que existe 1 lembrete concluído no histórico
    E que existem os lembretes futuros "Dentista" e "Mercado"
    Quando excluo "Dentista" confirmando
    Então o histórico continua exibindo "Concluídos (1)"
```

---

## 6 - Alerta no horário marcado

```gherkin
# language: pt
Funcionalidade: Alerta no horário marcado
  Como um usuário
  Desejo ser avisado quando chegar a hora do lembrete
  Para não esquecer a atividade

```
### CT-051
```gherkin
  @CT-051
  Cenário: Alerta é exibido na data e hora marcadas
    Dado que acesso a aplicação Brasa Lembretes
    E que criei o lembrete "Tomar remédio" com descrição "Após o almoço" para o próximo minuto
    Quando o relógio atinge o horário agendado
    Então uma janela "Chegou a hora" é exibida em até 1 segundo
    E exibe o título "Tomar remédio"
    E exibe a descrição "Após o almoço"
    E exibe "Agendado para" seguido da data e hora do lembrete
    E exibe o chip "Único"
    E o título da aba do navegador passa a ser "(1) Lembrete agora · Brasa Lembretes"
    E o foco é posicionado no botão "Marcar como visto"

```
### CT-052
```gherkin
  @CT-052
  Cenário: Alerta sem descrição não exibe o parágrafo de descrição
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete sem descrição cujo horário chegou
    Então o alerta é exibido sem o campo de descrição

```
### CT-053
```gherkin
  @CT-053
  Cenário: Alerta de lembrete recorrente exibe o chip da frequência
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete semanal cujo horário chegou
    Então o alerta exibe o chip "Recorrente · Semanal"

```
### CT-054
```gherkin
  @CT-054
  Cenário: Lembrete em alerta sai da lista de futuros
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes "A" (vencido) e "B" (futuro)
    Quando o alerta de "A" é exibido
    Então a lista de futuros mostra apenas "B"
    E o contador exibe "1 lembrete"

```
### CT-055
```gherkin
  @CT-055
  Cenário: Vários lembretes vencidos entram em fila, do mais antigo ao mais recente
    Dado que acesso a aplicação Brasa Lembretes
    E que existem 3 lembretes vencidos com horários 10:00, 10:01 e 10:02
    Quando o alerta é exibido
    Então o primeiro alerta é o de 10:00
    E o indicador da fila exibe "1 de 3"
    E o título da aba exibe "(3) Lembrete agora · Brasa Lembretes"

```
### CT-056
```gherkin
  @CT-056
  Cenário: Ao tratar um alerta da fila o próximo é exibido em seguida
    Dado que acesso a aplicação Brasa Lembretes
    E que há 2 alertas na fila
    Quando clico em "Marcar como visto" no primeiro
    Então o segundo alerta é exibido imediatamente
    E o indicador da fila deixa de ser exibido
    Quando clico em "Marcar como visto" no segundo
    Então a janela de alerta é fechada
    E o título da aba volta a ser "Brasa Lembretes"

```
### CT-057
```gherkin
  @CT-057
  Cenário: Lembrete vencido enquanto a página estava fechada
    Dado que acesso a aplicação Brasa Lembretes
    E que criei um lembrete para daqui a 2 minutos
    E fechei a aba do navegador
    Quando reabro a aplicação depois do horário agendado
    Então o alerta do lembrete é exibido assim que a página carrega

```
### CT-058
```gherkin
  @CT-058
  Cenário: O alerta não é fechado pela tecla Esc nem pelo clique fora
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta está aberto
    Quando pressiono Esc
    E clico na área escura fora da janela
    Então o alerta continua aberto

```
### CT-059
```gherkin
  @CT-059
  Cenário: Alerta dispara com o formulário aberto
    Dado que acesso a aplicação Brasa Lembretes
    E que o formulário de novo lembrete está aberto com dados preenchidos
    Quando chega a hora de outro lembrete
    Então o formulário é fechado e o alerta é exibido
    E os dados digitados no formulário são perdidos
    # Observação: avaliar se perder o rascunho é aceitável do ponto de vista do usuário.

```
### CT-060
```gherkin
  @CT-060
  Cenário: Alerta com título e descrição longos permanece legível no celular
    Dado que acesso a aplicação Brasa Lembretes
    E que o viewport tem 375 px de largura
    E existe um lembrete vencido com título de 80 caracteres e descrição de 500 caracteres
    Então o alerta aparece como janela inferior (bottom sheet)
    E o conteúdo rola dentro da janela sem cortar os botões de ação

```
### CT-061
```gherkin
  @CT-061
  Cenário: Som do alerta após interação do usuário
    Dado que acesso a aplicação Brasa Lembretes
    E que já cliquei ou toquei em algum ponto da página
    Quando um alerta é exibido
    Então é emitido um sinal sonoro de dois bipes

```
### CT-062
```gherkin
  @CT-062
  Cenário: Sem interação prévia o alerta funciona sem som
    Dado que acesso a aplicação Brasa Lembretes
    E que apenas abri a página, sem clicar ou tocar em nada
    Quando um alerta é exibido
    Então a janela de alerta aparece normalmente
    E nenhum erro é exibido ao usuário

```
### CT-063
```gherkin
  @CT-063
  Cenário: Alerta aparece mesmo com a aba em segundo plano
    Dado que acesso a aplicação Brasa Lembretes
    E que criei um lembrete para o próximo minuto
    E mudei para outra aba do navegador
    Quando o horário chega e volto à aba do Brasa Lembretes
    Então o alerta está visível
```

---

## 7 - Marcar como visto

```gherkin
# language: pt
Funcionalidade: Marcar lembrete como visto
  Como um usuário
  Desejo marcar o alerta como visto
  Para concluir o lembrete ou avançar para a próxima ocorrência

```
### CT-064
```gherkin
  @CT-064
  Cenário: Marcar lembrete único como visto
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete único "Tomar remédio" está aberto
    Quando clico em "Marcar como visto"
    Então vejo o aviso "Lembrete marcado como visto"
    E a janela de alerta é fechada
    E "Tomar remédio" não aparece em "Lembretes futuros"
    E a seção "Concluídos (1)" passa a existir
    E "Tomar remédio" aparece na lista de concluídos com a data e hora da conclusão

```
### CT-065
```gherkin
  @CT-065
  Cenário: Lembrete recorrente avança para a próxima ocorrência
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta de um lembrete <frequencia> agendado para <data_atual> às 09:00 está aberto
    Quando clico em "Marcar como visto"
    Então vejo o aviso "Visto. Próxima vez:" com a data <proxima_data> às 09:00
    E o lembrete continua em "Lembretes futuros" na data <proxima_data>
    E o lembrete não aparece em "Concluídos"

    Exemplos:
      | frequencia | data_atual | proxima_data | observacao             |
      | diário     | 15/12/2026 | 16/12/2026   | caso comum             |
      | diário     | 31/12/2026 | 01/01/2027   | virada de ano          |
      | semanal    | 15/12/2026 | 22/12/2026   | caso comum             |
      | semanal    | 28/12/2026 | 04/01/2027   | virada de ano          |
      | mensal     | 15/10/2026 | 15/11/2026   | caso comum             |
      | mensal     | 15/12/2026 | 15/01/2027   | virada de ano          |

```
### CT-066
```gherkin
  @CT-066
  Cenário: Lembrete mensal criado em dia que não existe no mês seguinte
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta de um lembrete mensal criado originalmente no dia <dia_origem> e agendado para <data_atual> está aberto
    Quando clico em "Marcar como visto"
    Então a próxima ocorrência é <proxima_data>
    Quando o novo alerta é tratado em seguida
    Então a ocorrência seguinte volta ao dia <dia_origem> quando o mês permitir, ou seja, <seguinte>

    Exemplos:
      | dia_origem | data_atual | proxima_data | seguinte   | observacao                       |
      | 31         | 31/01/2027 | 28/02/2027   | 31/03/2027 | fevereiro de ano comum           |
      | 31         | 31/01/2028 | 29/02/2028   | 31/03/2028 | fevereiro de ano bissexto        |
      | 31         | 31/03/2027 | 30/04/2027   | 31/05/2027 | mês seguinte com 30 dias         |
      | 30         | 30/01/2027 | 28/02/2027   | 30/03/2027 | dia 30 em fevereiro              |
      | 29         | 29/01/2027 | 28/02/2027   | 29/03/2027 | dia 29 em fevereiro de ano comum |
      | 29         | 29/01/2028 | 29/02/2028   | 29/03/2028 | dia 29 em ano bissexto           |

```
### CT-067
```gherkin
  @CT-067
  Cenário: Lembrete recorrente muito atrasado pula direto para a próxima data futura
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete diário cujo último horário agendado foi há 5 dias
    E o alerta está aberto
    Quando clico em "Marcar como visto"
    Então a próxima ocorrência exibida está no futuro
    E nenhum alerta é reaberto para as ocorrências perdidas

```
### CT-068
```gherkin
  @CT-068
  Cenário: Marcar como visto não gera novo alerta imediato para recorrente
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta de um lembrete diário está aberto
    Quando clico em "Marcar como visto"
    Então a janela de alerta é fechada
    E nenhum novo alerta é exibido nos próximos segundos

```
### CT-069
```gherkin
  @CT-069
  Cenário: Recorrente continua gerando alertas nas ocorrências seguintes
    Dado que acesso a aplicação Brasa Lembretes
    E que um lembrete recorrente foi marcado como visto e avançou para daqui a 1 minuto (ajustado via localStorage)
    Quando o novo horário chega
    Então um novo alerta é exibido para o mesmo lembrete
```

---

## 8 - Adiar lembrete

```gherkin
# language: pt
Funcionalidade: Adiar lembrete
  Como um usuário
  Desejo adiar um alerta
  Para ser lembrado novamente em outro momento

```
### CT-070
```gherkin
  @CT-070
  Cenário: Adiar usando as opções rápidas
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete "Ligar para o João" está aberto
    Quando clico em "<opcao>"
    Então vejo o aviso "Adiado para" seguido de <novo_horario>
    E a janela de alerta é fechada
    E o lembrete volta para "Lembretes futuros" em <novo_horario>
    E o cartão exibe o chip "Adiado 1x"

    Exemplos:
      | opcao          | novo_horario                        |
      | +10 min        | agora + 10 minutos (segundos zerados) |
      | +1 hora        | agora + 60 minutos (segundos zerados) |
      | Amanhã às 9h   | amanhã às 09:00                     |

```
### CT-071
```gherkin
  @CT-071
  Cenário: Adiar para data e hora personalizadas
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete "Ligar para o João" está aberto
    Quando informo em "Outra data e hora" um horário daqui a 3 horas
    E clico em "Adiar"
    Então vejo o aviso "Adiado para" com o horário informado
    E o lembrete volta à lista nesse horário

```
### CT-072
```gherkin
  @CT-072
  Cenário: Adiar sem informar data e hora
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete "Ligar para o João" está aberto
    Quando deixo "Outra data e hora" vazio
    E clico em "Adiar"
    Então vejo a mensagem "Escolha a nova data e hora."
    E o alerta continua aberto

```
### CT-073
```gherkin
  @CT-073
  Cenário: Adiar para uma data que não está no futuro
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete "Ligar para o João" está aberto
    Quando informo em "Outra data e hora" o valor <valor>
    E clico em "Adiar"
    Então vejo a mensagem "A nova data precisa estar no futuro."
    E o alerta continua aberto

    Exemplos:
      | valor                    |
      | 1 dia atrás              |
      | 1 minuto atrás           |
      | o minuto atual           |

```
### CT-074
```gherkin
  @CT-074
  Cenário: Adiar para o próximo minuto é aceito
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta do lembrete "Ligar para o João" está aberto
    Quando informo em "Outra data e hora" o próximo minuto
    E clico em "Adiar"
    Então o lembrete é adiado com sucesso

```
### CT-075
```gherkin
  @CT-075
  Cenário: A mensagem de erro do adiamento é limpa no alerta seguinte
    Dado que acesso a aplicação Brasa Lembretes
    E que tentei adiar sem data e vi a mensagem de erro
    Quando adio o lembrete com "+10 min"
    E existe outro alerta na fila
    Então o novo alerta não exibe mensagem de erro

```
### CT-076
```gherkin
  @CT-076
  Cenário: O alerta volta a ser exibido quando o novo horário chega
    Dado que acesso a aplicação Brasa Lembretes
    E que adiei o lembrete para daqui a 1 minuto (ou ajustei o horário via localStorage)
    Quando o novo horário chega
    Então o alerta "Chegou a hora" é exibido novamente para "Ligar para o João"

```
### CT-077
```gherkin
  @CT-077
  Cenário: O contador de adiamentos acumula
    Dado que acesso a aplicação Brasa Lembretes
    E que o lembrete foi adiado 2 vezes
    Então o cartão exibe o chip "Adiado 2x"

```
### CT-078
```gherkin
  @CT-078
  Cenário: Adiar um lembrete recorrente mantém a recorrência
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta é de um lembrete semanal agendado originalmente para segunda às 09:00
    Quando clico em "+1 hora"
    E o novo alerta é exibido e clico em "Marcar como visto"
    Então a próxima ocorrência é a segunda-feira seguinte às 09:00
    E não uma semana a partir do horário adiado

```
### CT-079
```gherkin
  @CT-079
  Cenário: Adiar um alerta da fila exibe o próximo
    Dado que acesso a aplicação Brasa Lembretes
    E que há 2 alertas na fila
    Quando adio o primeiro com "+10 min"
    Então o segundo alerta é exibido
    E o primeiro aparece em "Lembretes futuros"

```
### CT-080
```gherkin
  @CT-080
  Cenário: Adiar para "Amanhã às 9h" mostra o rótulo "Amanhã" no agrupamento
    Dado que acesso a aplicação Brasa Lembretes
    Quando clico em "Amanhã às 9h"
    Então o lembrete aparece no grupo "Amanhã" às 09:00
```

---

## 9 - Histórico de concluídos

```gherkin
# language: pt
Funcionalidade: Histórico de concluídos
  Como um usuário
  Desejo consultar e limpar os lembretes concluídos
  Para acompanhar o que já foi visto

```
### CT-081
```gherkin
  @CT-081
  Cenário: Seção de concluídos fica oculta quando não há concluídos
    Dado que acesso a aplicação Brasa Lembretes
    E que não há lembretes concluídos
    Então a seção "Concluídos" não é exibida

```
### CT-082
```gherkin
  @CT-082
  Cenário: Seção de concluídos exibe a quantidade
    Dado que acesso a aplicação Brasa Lembretes
    E que 3 lembretes únicos foram marcados como vistos
    Então a seção exibe "Concluídos (3)"
    Quando expando a seção
    Então vejo os 3 lembretes com o título riscado e a data e hora da conclusão

```
### CT-083
```gherkin
  @CT-083
  Cenário: Concluídos ordenados do mais recente para o mais antigo
    Dado que acesso a aplicação Brasa Lembretes
    E que marquei "A" como visto às 10:00 e "B" às 10:05
    Quando expando "Concluídos"
    Então "B" aparece antes de "A"

```
### CT-084
```gherkin
  @CT-084
  Cenário: Lembrete recorrente visto não vai para o histórico
    Dado que acesso a aplicação Brasa Lembretes
    E que marquei como visto um lembrete diário
    Então "Concluídos" não contabiliza esse lembrete

```
### CT-085
```gherkin
  @CT-085
  Cenário: Limpar concluídos
    Dado que acesso a aplicação Brasa Lembretes
    E que existem 2 lembretes concluídos e 1 lembrete futuro
    Quando clico em "Limpar concluídos"
    Então vejo o aviso "Concluídos removidos"
    E a seção "Concluídos" desaparece
    E o lembrete futuro permanece na lista

```
### CT-086
```gherkin
  @CT-086
  Cenário: Limpar concluídos não pede confirmação
    Dado que acesso a aplicação Brasa Lembretes
    E que existem lembretes concluídos
    Quando clico em "Limpar concluídos"
    Então os lembretes são removidos imediatamente
    # Observação: diferente da exclusão individual, não há confirmação. Avaliar impacto na usabilidade.

```
### CT-087
```gherkin
  @CT-087
  Cenário: Histórico persiste após recarregar a página
    Dado que acesso a aplicação Brasa Lembretes
    E que existe 1 lembrete concluído
    Quando recarrego a página
    Então a seção exibe "Concluídos (1)"

```
### CT-088
```gherkin
  @CT-088
  Cenário: Título com HTML no histórico é exibido como texto
    Dado que acesso a aplicação Brasa Lembretes
    E que concluí um lembrete com título "<b>teste</b>"
    Quando expando "Concluídos"
    Então vejo o texto literal "<b>teste</b>" sem formatação
```

---

## 10 - Persistência e armazenamento

```gherkin
# language: pt
Funcionalidade: Persistência dos dados no navegador
  Como um usuário
  Desejo que meus lembretes sejam mantidos
  Para encontrá-los quando voltar à aplicação

```
### CT-089
```gherkin
  @CT-089
  Cenário: Lembretes persistem após recarregar a página
    Dado que acesso a aplicação Brasa Lembretes
    E que criei os lembretes "A" e "B"
    Quando recarrego a página
    Então "A" e "B" continuam na lista com os mesmos dados

```
### CT-090
```gherkin
  @CT-090
  Cenário: Lembretes persistem após fechar e reabrir o navegador
    Dado que acesso a aplicação Brasa Lembretes
    E que criei o lembrete "A" para daqui a 1 dia
    Quando fecho o navegador e o abro novamente
    E acesso a aplicação
    Então "A" continua na lista

```
### CT-091
```gherkin
  @CT-091
  Cenário: Edição, exclusão e conclusão são persistidas
    Dado que acesso a aplicação Brasa Lembretes
    E que editei "A", excluí "B" e concluí "C"
    Quando recarrego a página
    Então "A" exibe os dados editados
    E "B" não existe
    E "C" está em "Concluídos"

```
### CT-092
```gherkin
  @CT-092
  Cenário: Dados são isolados por navegador
    Dado que acesso a aplicação Brasa Lembretes
    E que criei o lembrete "A" no navegador 1
    Quando acesso a aplicação no navegador 2
    Então "A" não aparece

```
### CT-093
```gherkin
  @CT-093
  Cenário: Dados corrompidos no armazenamento
    Dado que acesso a aplicação Brasa Lembretes
    E que o valor da chave "brasa.lembretes.v1" no localStorage é um JSON inválido (ex.: "{abc")
    Quando acesso a aplicação
    Então vejo o aviso "Não foi possível usar o armazenamento do navegador"
    E a aplicação carrega com a lista vazia
    E é possível criar novos lembretes

```
### CT-094
```gherkin
  @CT-094
  Cenário: Valor salvo que não é uma lista
    Dado que acesso a aplicação Brasa Lembretes
    E que o valor da chave "brasa.lembretes.v1" é o objeto {"a":1}
    Quando acesso a aplicação
    Então a aplicação carrega com a lista vazia
    E não apresenta erro na tela

```
### CT-095
```gherkin
  @CT-095
  Cenário: Armazenamento do navegador indisponível ou bloqueado
    Dado que acesso a aplicação Brasa Lembretes
    E que o navegador bloqueia o acesso ao localStorage (ex.: cookies e dados de sites bloqueados)
    Quando acesso a aplicação e crio um lembrete
    Então vejo o aviso "Não foi possível usar o armazenamento do navegador. Os lembretes funcionam, mas serão perdidos ao fechar a página."
    E o lembrete aparece na lista durante a sessão
    Quando recarrego a página
    Então o lembrete deixa de existir

```
### CT-096
```gherkin
  @CT-096
  Cenário: Sincronização entre abas abertas
    Dado que acesso a aplicação Brasa Lembretes
    E que a aplicação está aberta em duas abas do mesmo navegador
    Quando crio o lembrete "A" na aba 1
    Então "A" aparece na aba 2 sem recarregar

```
### CT-097
```gherkin
  @CT-097
  Cenário: Alerta ao tratar o mesmo lembrete em duas abas
    Dado que acesso a aplicação Brasa Lembretes
    E que a aplicação está aberta em duas abas
    E existe um lembrete que vence no próximo minuto
    Quando o horário chega e marco como visto na aba 1
    Então a aba 2 não exibe um alerta duplicado e permanece consistente
    # Observação: as duas abas disparam o alerta; verificar o estado final após tratar em ambas.

```
### CT-098
```gherkin
  @CT-098
  Cenário: Modo de navegação anônima
    Dado que acesso a aplicação Brasa Lembretes em uma janela anônima
    Quando crio um lembrete e recarrego a página
    Então a aplicação funciona
    E o lembrete se comporta conforme a política de armazenamento do navegador
```

---

## 11 - Relógio e atualização automática da tela

```gherkin
# language: pt
Funcionalidade: Relógio e atualização automática
  Como um usuário
  Desejo ver a hora atual e informações sempre atualizadas
  Para confiar no que a tela mostra

```
### CT-099
```gherkin
  @CT-099
  Cenário: Relógio do topo atualiza a cada segundo
    Dado que acesso a aplicação Brasa Lembretes
    Então a barra superior exibe dia da semana, dia, mês e hora no formato "HH:MM:SS"
    E os segundos avançam a cada segundo

```
### CT-100
```gherkin
  @CT-100
  Cenário: O tempo relativo dos cartões é atualizado sem recarregar
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete agendado para daqui a 5 minutos
    Quando aguardo 2 minutos
    Então o chip de tempo relativo exibe aproximadamente "em 3 min"

```
### CT-101
```gherkin
  @CT-101
  Cenário: A passagem do horário gera alerta sem recarregar
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete agendado para o próximo minuto
    Quando aguardo o horário chegar sem interagir com a página
    Então o alerta é exibido automaticamente

```
### CT-102
```gherkin
  @CT-102
  Cenário: O bloco "Próximo lembrete" muda após o primeiro vencer
    Dado que acesso a aplicação Brasa Lembretes
    E que existem os lembretes "A" (daqui a 1 minuto) e "B" (daqui a 1 hora)
    Quando "A" vence e é marcado como visto
    Então o bloco "Próximo lembrete" passa a exibir "B"
```

---

## 12 - Layout, responsividade e acessibilidade

```gherkin
# language: pt
Funcionalidade: Layout, responsividade e acessibilidade
  Como um usuário em computador ou celular
  Desejo usar a aplicação com conforto
  Para gerenciar meus lembretes em qualquer dispositivo

```
### CT-103
```gherkin
  @CT-103
  Cenário: Layout nos principais tamanhos de tela
    Dado que acesso a aplicação Brasa Lembretes
    E que o viewport tem <largura> px de largura
    Quando visualizo a lista com ao menos 3 lembretes
    Então não há rolagem horizontal
    E todos os botões são visíveis e clicáveis
    E <comportamento>

    Exemplos:
      | largura | comportamento                                                       |
      | 360     | o relógio ocupa uma linha própria e o cartão tem uma coluna         |
      | 561     | o cartão exibe horário à esquerda e conteúdo à direita              |
      | 820     | o conteúdo fica centralizado com largura máxima                     |
      | 1920    | o conteúdo fica centralizado com largura máxima                     |

```
### CT-104
```gherkin
  @CT-104
  Cenário: Formulário como janela central ou janela inferior
    Dado que acesso a aplicação Brasa Lembretes
    E que o viewport tem <largura> px de largura
    Quando clico em "+ Novo lembrete"
    Então o formulário é exibido <posicao>

    Exemplos:
      | largura | posicao                         |
      | 560     | colado à parte inferior da tela |
      | 561     | centralizado na tela            |

```
### CT-105
```gherkin
  @CT-105
  Cenário: Formulário longo é rolável em tela pequena
    Dado que acesso a aplicação Brasa Lembretes
    E que o viewport tem 360 x 560 px
    Quando abro o formulário com frequência visível
    Então consigo rolar o formulário até o botão "Salvar lembrete"

```
### CT-106
```gherkin
  @CT-106
  Cenário: Teclado do celular não impede o preenchimento
    Dado que acesso a aplicação Brasa Lembretes
    E que estou em um celular
    Quando toco no campo de data e hora
    Então o seletor nativo de data e hora é exibido
    E consigo escolher e confirmar o valor

```
### CT-107
```gherkin
  @CT-107
  Cenário: Navegação completa por teclado
    Dado que acesso a aplicação Brasa Lembretes
    Quando uso apenas Tab, Shift+Tab, Enter, Espaço e Esc
    Então consigo abrir o formulário, preencher os campos, escolher Único/Recorrente, salvar, editar, excluir com confirmação e tratar um alerta
    E o foco é sempre visível

```
### CT-108
```gherkin
  @CT-108
  Cenário: Campos inválidos são indicados de forma acessível
    Dado que acesso a aplicação Brasa Lembretes
    Quando tento salvar o formulário vazio
    Então os campos com erro recebem aria-invalid="true"
    E as mensagens de erro são exibidas junto aos campos

```
### CT-109
```gherkin
  @CT-109
  Cenário: Janelas anunciam sua função para leitores de tela
    Dado que acesso a aplicação Brasa Lembretes
    Então o formulário possui role="dialog" com rótulo "Novo lembrete"
    E o alerta possui role="alertdialog" com título e descrição associados

```
### CT-110
```gherkin
  @CT-110
  Cenário: Tamanho mínimo de alvo de toque
    Dado que acesso a aplicação Brasa Lembretes
    E que estou em um celular
    Então os botões principais têm altura mínima de 44 px

```
### CT-111
```gherkin
  @CT-111
  Cenário: Preferência por movimento reduzido
    Dado que acesso a aplicação Brasa Lembretes
    E que o sistema operacional está configurado para reduzir animações
    Quando abro o formulário e um alerta
    Então não há animações de entrada nem de pulsação

```
### CT-112
```gherkin
  @CT-112
  Cenário: Aviso rápido (toast) some sozinho
    Dado que acesso a aplicação Brasa Lembretes
    Quando crio um lembrete
    Então o aviso é exibido na parte inferior da tela
    E desaparece após cerca de 3 segundos

```
### CT-113
```gherkin
  @CT-113
  Cenário: Compatibilidade entre navegadores
    Dado que acesso a aplicação Brasa Lembretes no <navegador>
    Quando crio um lembrete, recebo o alerta e marco como visto
    Então o fluxo funciona sem erros visuais ou funcionais

    Exemplos:
      | navegador                     |
      | Google Chrome (computador)    |
      | Mozilla Firefox (computador)  |
      | Microsoft Edge (computador)   |
      | Safari (macOS)                |
      | Chrome (Android)              |
      | Safari (iOS)                  |

```
### CT-114
```gherkin
  @CT-114
  Cenário: Fontes externas indisponíveis
    Dado que acesso a aplicação Brasa Lembretes
    E que o acesso ao Google Fonts está bloqueado
    Quando acesso a aplicação
    Então o texto é exibido com as fontes alternativas do sistema
    E todas as funcionalidades continuam disponíveis
```

---

## 13 - Comportamento temporal, fuso e suspensão

```gherkin
# language: pt
Funcionalidade: Comportamento sob alterações de tempo e energia
  Como um usuário da aplicação
  Desejo que meus lembretes disparem no momento correto mesmo sob variações de relógio ou energia
  Para manter a confiabilidade dos avisos

```
### CT-115
```gherkin
  @CT-115
  Cenário: Lembrete agendado através da transição do horário de verão
    Dado que a aplicação está configurada em uma zona com horário de verão
    E que agendei um lembrete para as 02:30 no dia em que o relógio adianta em 1 hora à meia-noite
    Quando o horário do sistema atinge o momento correspondente
    Então o alerta dispara sem travar a interface
    E nenhum alerta duplicado é exibido

```
### CT-116
```gherkin
  @CT-116
  Cenário: Mudança de fuso horário do dispositivo com lembretes futuros pendentes
    Dado que acesso a aplicação Brasa Lembretes
    E que criei um lembrete para "15:00" em um dispositivo no fuso UTC-3
    Quando o fuso horário do sistema é alterado para UTC-4
    E recarrego a página
    Então o horário exibido no cartão reflete a hora correspondente no novo fuso
    E o alerta é acionado coerentemente com o relógio atualizado do dispositivo

```
### CT-119
```gherkin
  @CT-119
  Cenário: Retomada após suspensão ou hibernação do dispositivo
    Dado que acesso a aplicação Brasa Lembretes
    E que criei um lembrete agendado para daqui a 10 minutos
    E o dispositivo entra em modo de suspensão ou hibernação por 30 minutos
    Quando o dispositivo acorda e a aba volta a ficar ativa
    Então o alerta do lembrete vencido é exibido imediatamente
    E o relógio do topo sincroniza com a hora real do sistema operacional

```
### CT-120
```gherkin
  @CT-120
  Cenário: Ajuste manual do relógio do sistema para o passado
    Dado que acesso a aplicação Brasa Lembretes
    E que existe um lembrete agendado para as 14:00
    E o relógio do sistema marcava 13:50
    Quando o usuário altera manualmente o relógio do sistema para 12:00
    Então o chip de tempo relativo do cartão é recalculado para "em 2 h"
    E nenhum alerta indevido é disparado prematuramente

# language: pt
Funcionalidade: Limites de armazenamento e carga
  Como um usuário com grande volume de lembretes
  Desejo que a aplicação lide de forma graciosa com o esgotamento de espaço
  Para não perder meus dados cadastrados nem travar a tela

```
### CT-117
```gherkin
  @CT-117
  Cenário: Tratamento de cota do navegador esgotada (localStorage cheio)
    Dado que acesso a aplicação Brasa Lembretes
    E que o armazenamento do navegador atingiu o limite de capacidade
    Quando preencho o formulário e clico em "Salvar lembrete"
    Então vejo o aviso "Não foi possível salvar: armazenamento local cheio. Exclua lembretes antigos ou limpe o histórico de concluídos."
    E a tela não apresenta erro não tratado
    E os lembretes salvos anteriormente permanecem intactos

```
### CT-118
```gherkin
  @CT-118
  Cenário: Responsividade da interface com grande volume de lembretes
    Dado que existem 300 lembretes futuros e 200 concluídos salvos no navegador
    Quando acesso a aplicação Brasa Lembretes
    Então a lista é renderizada sem congelar a interface
    E a rolagem da página permanece fluida

# language: pt
Funcionalidade: Regras de borda para anos bissextos em recorrências
  Como um usuário
  Desejo precisão no agendamento de recorrências em datas variáveis de calendário
  Para não perder compromissos agendados no final de fevereiro

```
### CT-122
```gherkin
  @CT-122
  Cenário: Avanço de lembrete diário em ano bissexto
    Dado que acesso a aplicação Brasa Lembretes
    E que o alerta de um lembrete diário agendado para 28 de fevereiro de 2028 (ano bissexto) às 10:00 está aberto
    Quando clico em "Marcar como visto"
    Então a próxima ocorrência exibida é "29/02/2028" às 10:00
    E não o dia primeiro de março

```
### CT-123
```gherkin
  @CT-123
  Cenário: Recorrência mensal cadastrada originalmente em 29 de fevereiro
    Dado que acesso a aplicação Brasa Lembretes
    E que criei um lembrete mensal em 29 de fevereiro de um ano bissexto
    Quando o alerta de 29/02 é marcado como visto
    Então a próxima ocorrência cai em 29 de março
    Quando o lembrete avança para o ano comum subsequente
    Então a ocorrência de fevereiro cai em 28 de fevereiro

# language: pt
Funcionalidade: Resiliência de schema e segurança de entrada
  Como um usuário
  Desejo ter meus dados protegidos contra falhas de versão e códigos maliciosos
  Para usar a ferramenta com segurança e estabilidade

```
### CT-121
```gherkin
  @CT-121
  Cenário: Carregamento de dados salvos com propriedades obrigatórias ausentes
    Dado que acesso a aplicação Brasa Lembretes
    E que a chave no localStorage contém um lembrete sem as propriedades "type" ou "createdAt"
    Quando a aplicação é carregada
    Então o item é normalizado com valores padrão
    E a lista é exibida sem travar o carregamento dos demais lembretes

```
### CT-124
```gherkin
  @CT-124
  Cenário: Sanitização de script (XSS) no campo de descrição
    Dado que acesso a aplicação Brasa Lembretes
    Quando crio um lembrete com a descrição "<img src=x onerror=alert('xss')>"
    Então o cartão e a janela de alerta exibem o texto literal
    E nenhum código JavaScript é executado
    E nenhuma janela de alerta indevida é disparada
```

---
