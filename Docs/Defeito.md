**Defeito**  
Baseado na ISO-29119-3 e em ferramentas de gestão de defeitos. 

## Defeito 01

| ID | 01 |
| :---- | :---- |
| **Título** | O sistema mostra a mensagem de erro ‘Precisa ser uma data e hora futura’ ‘Informe a data e a hora do lembrete’ ao colocar a data inválida 29/02/2027 |
| **Testador** | Isabella Henriques |
| **Data e Hora** | 17/10/2026 \- 19:20 |
| **Resultado Esperado** | Mensagem de erro informando que a data é inválida |
| **Resultado Atual** | O sistema mostra a mensagem de erro ‘Precisa ser uma data e hora futura’ ‘Informe a data e a hora do lembrete’ ao colocar a data inválida 29/02/2027 |
| **Evidências** | [Visualizar imagem da evidência](./img/Brasa-Lembretes-10-17-2026_07_23_PM.png) |
| **Prioridade** | Baixa |
| **Severidade** | Baixa |
| **Informações sobre  o Software** | file:///C:/Projetos%20GitHub/brasa-lembretes/index.html |
| **Rastreabilidade** | [Relatório de Sessão 1](./Relatorio_de_Sessao.md#relat%C3%B3rio-de-sess%C3%A3o-1) |
| **Status** | To Do |

![Evidência do defeito 01](./img/Brasa-Lembretes-10-17-2026_07_23_PM.png)

## Defeito 02

| ID | 02 |
| :---- | :---- |
| **Título** | O indicador da fila não é exibido no primeiro alerta (esperado “1 de 3”) e, após marcar como visto, a contagem é reiniciada para “1 de 2” ao invés de “2 de 3” |
| **Testador** | Yara Rodrigues |
| **Data e Hora** | 19/10/2026 \- 11:11 |
| **Resultado Esperado** | Ao exibir 3 lembretes vencidos de horarios diferentes (11:07, 11:08 e 11:09), o primeiro alerta é o de 11:07 e o indicador da fila exibe “1 de 3”. O título da aba exibe “(3) Lembrete agora · Brasa Lembretes”. Ao marcar o primeiro como visto, o próximo alerta exibe “2 de 3” |
| **Resultado Atual** | O primeiro alerta (“Teste de Fila de Lembretes 1”) é exibido sem nenhum indicador de fila. Ao marcar como visto, o segundo alerta exibe “1 de 2” (a fila é recontada com os lembretes restantes). O terceiro alerta também é exibido sem indicador. A ordem dos alertas (11:07, 11:08, 11:09) está correta |
| **Evidências** | [Visualizar vídeo da evidência](./videos/EvidenciaBUGFila.mp4) |
| **Prioridade** | Média |
| **Severidade** | Baixa |
| **Informações sobre  o Software** | https://brasa-lembretes.vercel.app/ |
| **Rastreabilidade** | [CT-055](./Casos%20de%20Teste%20em%20Gherkin.md#ct-055) |
| **Status** | To Do |

**Passos para reproduzir**

1. Acessar a aplicação Brasa Lembretes.
2. Criar 3 lembretes únicos com horários diferentes (ex.: 11:07, 11:08 e 11:09).
3. Aguardar o vencimento dos 3 lembretes e o alerta ser exibido.
4. Observar o primeiro alerta: o indicador da fila não aparece.
5. Clicar em “Marcar como visto” e observar o segundo alerta: o indicador mostra “1 de 2”.

[Assistir à evidência do defeito 02](./videos/EvidenciaBUGFila.mp4)

---
