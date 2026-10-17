## Relatório de Sessão 1
Inspirado no artigo de John Bach sobre Session-Based Test Management (2001)

| Data e Hora do Início | Nome do Testador | Módulo |
| :---- | :---- | :---- |
| **17/10/2026 \- 19:00PM** | Isabella Henriques | Criação de lembrete \- Campo data |

**Test Charter:**  
*Explore* a funcionalidade de criar e editar um novo lembrete  
*Com* o uso da Heurística de teste MAMID   
**M**aior que xpto  
**A**no Bissexto  
**M**enor que xpto  
**I**gual a xpto  
**D**ata inválida  
*Para descobrir* se o campo data lida bem com edição no campo data

**Tamanho da Sessão:**  
30 minutos

**Notas\*:**

**M**aior que a data de hoje
(I) Consegui criar um lembrete maior que a data de hoje

**A**no Bissexto  
(I) Consegui criar um lembrete para ano bissexto

**M**enor que xpto  
(I) O Sistema não criou o lembrete para a data menor que hoje

**I**gual a atual  
(I) O Sistema não criou o lembrete para a data e hora igual a atual

**D**ata inválida  
(I) O Sistema não criou o lembrete para a data inválida ‘29/02/2027’ porém a mensagem de erro não informa o motivo do erro. 

*(\*) Podem ser (I)nformações ou (R)iscos.*

**Defeitos:**

1. O sistema mostra a mensagem de erro ‘Precisa ser uma data e hora futura’ ‘Informe a data e a hora do lembrete’ ao colocar a data inválida 29/02/2027 fazendo com que o usuário fique perdido ao saber exatamente qual é o erro.

**Perguntas:**

1. Quais tratativas de erro temos no sistema?

---
**Relatório de Sessão 2**  