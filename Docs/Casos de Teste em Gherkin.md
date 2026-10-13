# Casos de Teste em Gherkin — Brasa Lembretes

## 1 - Técnicas aplicadas:
- 

---

## 2 - Cadastro de lembrete

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
    E o lembrete aparece em "Lembretes futuros" com o chip "Único"
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
