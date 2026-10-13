# Casos de Teste em Gherkin — Brasa Lembretes

## 1 - Cadastro de lembrete

```gherkin
# language: pt
Funcionalidade: Cadastro de lembrete
  Como um usuário do Brasa Lembretes
  Desejo cadastrar lembretes com título, descrição e data/hora
  Para ser avisado na hora certa   

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

  @CT-005
  Cenário: Rejeitar data e hora que não estão no futuro
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Teste de data"
    E informo a data e hora "<data_hora>"
    E clico em "Salvar lembrete"
    Então vejo a mensagem de erro "Escolha uma data e hora no futuro."
    E nenhum lembrete é criado
    

  @CT-006 
  Cenário: Aceitar data e hora futuras, incluindo o limite mínimo
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Teste de data futura"
    E informo a data e hora "<data_hora>"
    E clico em "Salvar lembrete"
    Então o lembrete é criado com sucesso
    E o horário exibido no cartão corresponde ao informado
   

  @CT-007
  Cenário: Exibir os dois erros ao mesmo tempo quando título e data estão inválidos
    Dado que acesso a aplicação Brasa Lembretes
    Quando clico em "+ Novo lembrete"
    E deixo o título e a data e hora vazios
    E clico em "Salvar lembrete"
    Então vejo a mensagem "Informe um título para o lembrete."
    E vejo a mensagem "Informe a data e a hora do lembrete."
    E o foco é levado ao primeiro campo inválido, o título

  @CT-008 
  Cenário: Limite de caracteres do título (máximo 80)
    Dado que acesso a aplicação Brasa Lembretes 
    Quando clico em "+ Novo lembrete"
    E digito um título com <digitados> caracteres
    Então o contador do título exibe "<contador>/80"
    E o campo contém <aceitos> caracteres


  @CT-009 
 Cenário: Limite de caracteres da descrição (máximo 500)
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E digito uma descrição com <digitados> caracteres
    Então o contador da descrição exibe "<contador>/500"
    E o campo contém <aceitos> caracteres


  @CT-010 
  Cenário: Colar texto maior que o limite no título
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E colo no campo de título um texto com 120 caracteres
    Então o campo de título mantém apenas os primeiros 80 caracteres
    E o contador exibe "80/80"

  @CT-011 
  Cenário: Descrição composta apenas por espaços é tratada como vazia
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Sem descrição"
    E preencho a descrição com "     "
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão do lembrete não exibe parágrafo de descrição

  @CT-012 
  Cenário: Espaços nas extremidades do título são removidos
     Dado que acesso a aplicação Brasa Lembretes        
    Quando clico em "+ Novo lembrete"
    E preencho o título com "   Ligar para o banco   "
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe o título "Ligar para o banco" sem espaços nas pontas

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
 
  @CT-014
  Cenário: Emojis e acentuação são preservados
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Aniversário da vovó 🎂"
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe "Aniversário da vovó 🎂" corretamente

  @CT-015
  Cenário: Quebras de linha da descrição são preservadas
    Dado que acesso a aplicação Brasa Lembretes    
    Quando clico em "+ Novo lembrete"
    E preencho o título com "Lista de compras"
    E preencho a descrição com três linhas separadas por Enter
    E informo uma data e hora futura
    E clico em "Salvar lembrete"
    Então o cartão exibe a descrição em três linhas

  @CT-016
  Cenário: Título longo sem espaços não quebra o layout
    Dado que acesso a aplicação Brasa Lembretes    
    Quando crio um lembrete com título de 80 letras "A" sem espaços
    Então o texto quebra dentro do cartão
    E a página não apresenta rolagem horizontal

  @CT-017
  Cenário: Fechar o formulário sem salvar
    Dado que abri o formulário de novo lembrete
    E preenchi o título com "Rascunho"
    Quando Fechar o formulário sem salvar
    Então o formulário é fechado
    E nenhum lembrete é criado

  @CT-018 
  Cenário: Formulário reaberto não mantém dados nem erros anteriores
    Dado que tentei salvar um lembrete com título vazio e vi a mensagem de erro
    E fechei o formulário
    Quando clico em "+ Novo lembrete" novamente
    Então todos os campos estão vazios
    E nenhuma mensagem de erro é exibida
    E os contadores exibem "0/80" e "0/500"

  @CT-019 
  Cenário: Salvar o formulário pressionando Enter no campo de título     
    Dado que abri o formulário de novo lembrete
    E preenchi título e data e hora futura
    Quando pressiono Enter com o foco no campo de título
    Então o lembrete é criado
```

---

## 2. Lembretes recorrentes
```gherkin
# language: pt
Funcionalidade: Lembretes recorrentes
  Como um usuário
  Desejo criar lembretes que se repetem
  Para não precisar recadastrar atividades periódicas
   

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

  @CT-022
  Cenário: Lembrete recorrente aparece uma única vez na lista de futuros
    Dado que criei um lembrete diário para amanhã às 08:00
    Então a lista exibe apenas 1 cartão para ele
    E o contador exibe "1 lembrete"
```

---

## 3. Listagem de lembretes futuros

```gherkin
# language: pt
Funcionalidade: Listagem de lembretes futuros
  Como um usuário
  Desejo ver meus lembretes ordenados e agrupados por dia
  Para saber o que vem pela frente    

  @CT-024 
  Cenário: Estado vazio na primeira visita
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Então vejo a mensagem "Nenhum lembrete agendado"
    E vejo os botões "Criar primeiro lembrete" e "Carregar exemplos"
    E o bloco "Próximo lembrete" está oculto
    E o contador de lembretes está vazio
    E a seção "Concluídos" está oculta

  @CT-025
  Cenário: Botão "Criar primeiro lembrete" abre o formulário
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Quando clico em "Criar primeiro lembrete"
    Então o formulário "Novo lembrete" é exibido

  @CT-026
  Cenário: Carregar exemplos
    Dado que acesso a aplicação Brasa Lembretes
    E não existem lembretes salvos
    Quando clico em "Carregar exemplos"
    Então vejo o aviso "3 lembretes de exemplo adicionados"
    E vejo os lembretes "(exemplo) Tomar água", "(exemplo) Reunião semanal do time" e "(exemplo) Pagar aluguel"
    E o estado vazio deixa de ser exibido
    E "(exemplo) Tomar água" é único, "(exemplo) Reunião semanal do time" é semanal e "(exemplo) Pagar aluguel" é mensal

  @CT-027 
  Cenário: Ordenação do mais próximo para o mais distante
    Dado que cadastrei os lembretes nesta ordem:
      | título | quando         |
      | C      | daqui a 3 dias |
      | A      | daqui a 1 hora |
      | B      | daqui a 2 dias |
    Então a lista exibe os lembretes na ordem A, B, C
    E o bloco "Próximo lembrete" exibe "A"

  @CT-028 
  Cenário: Agrupamento por dia com rótulos "Hoje" e "Amanhã"
    Dado que existem lembretes para hoje, amanhã e daqui a 5 dias
    Então vejo três grupos de dia
    E o primeiro grupo tem o rótulo "Hoje" seguido da data por extenso
    E o segundo grupo tem o rótulo "Amanhã" seguido da data por extenso
    E o terceiro grupo exibe apenas o dia da semana e a data por extenso

  @CT-029
  Cenário: Lembretes no mesmo dia ficam no mesmo grupo, ordenados por horário
    Dado que existem lembretes amanhã às 15:00, 09:00 e 12:30
    Então há um único grupo "Amanhã"
    E os cartões aparecem na ordem 09:00, 12:30, 15:00

  @CT-030 
  enário: Lembretes em lados opostos da meia-noite ficam em grupos diferentes
    Dado que existem lembretes às <horario_1> e às <horario_2> do mesmo dia civil seguinte
    Então eles pertencem ao mesmo grupo

    Exemplos:
      | horario_1 | horario_2 |
      | 00:00     | 23:59     |

  @CT-031
  Cenário: Contador no singular e no plural
    Dado que existem <quantidade> lembretes futuros
    Então o contador exibe "<texto>"

    Exemplos:
      | quantidade | texto         |
      | 1          | 1 lembrete    |
      | 2          | 2 lembretes   |
      | 10         | 10 lembretes  |

  @CT-032 
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

  @CT-033
  Cenário: Lembrete futuro não exibe alerta
    Dado que existe um lembrete agendado para daqui a 1 hora
    Então nenhum alerta "Chegou a hora" é exibido

  @CT-034 
  Cenário: Cartão exibe o horário no formato 24 horas
    Dado que existe um lembrete agendado para amanhã às 14:05
    Então o cartão exibe o horário "14:05"
```

---

## 4. Edição de lembrete