# Desafio em Grupo #3

## 1. Técnicas de teste utilizadas

- Partição de equivalência: aplicada aos campos do formulário de novo lembrete.
- Análise de valor limite: aplicada às validações de data, hora e campos obrigatórios.
- Teste exploratório baseado em sessão: realizado com foco em cenários CRUD e heurísticas de validação funcional.


## 2. Artefatos utilizados

- [Casos de teste baseados na ISO 29119-3](./Casos_de_Teste_ISO_29119-3.md)
- [Casos de teste em formato Gherkin](./Casos%20de%20Teste%20em%20Gherkin.md)
- [Checklist de casos de teste](./checklist-casos-de-teste.md)
- [Condições de teste](./Condicoes%20de%20Teste.md)
- [Relatório de sessão](./Relatorio_de_Sessao.md)
- [Registro do defeito conforme a ISO 29119-3](Defeito.md)


## 3. Execução dos testes

| Métrica | Quantidade |
| --- | ---: |
| Casos planejados | 124 |
| Casos executados | 94 |
| Passaram | 89 |
| Falharam | 1 |
| Bloqueados / não executados | 34 |
| Defeitos encontrados | 2 |


## 4. Relato de defeitos

### DEF-01 — Mensagem inadequada para data inválida

- **Descrição:** ao informar a data inválida `29/02/2027`, o sistema exibe as mensagens “Precisa ser uma data e hora futura” e “Informe a data e a hora do lembrete”, sem indicar que a data informada não existe.
- **Impacto:** as mensagens não explicam o motivo da rejeição e podem confundir o usuário.
- **Prioridade / severidade:** baixa.
- **Rastreabilidade:** identificado durante o [Relatório de Sessão 1](./Relatorio_de_Sessao.md#relat%C3%B3rio-de-sess%C3%A3o-1).
- **Registro completo e evidência:** [Defeito 01](./Defeito.md#defeito-01).

### DEF-02 — Indicador da fila do alerta não acompanha a sequência correta

- **Descrição:** ao disparar três alertas simultâneos, o primeiro alerta não exibe o indicador da fila (esperado “1 de 3”), e ao marcar como visto o primeiro item a contagem reinicia para “1 de 2” em vez de “2 de 3”.
- **Impacto:** a navegação entre alertas fica inconsistente e a fila não reflete corretamente o estado real dos lembretes pendentes.
- **Prioridade / severidade:** média / baixa.
- **Rastreabilidade:** identificado no caso de teste [CT-055](./checklist-casos-de-teste.md#ct-055)
- **Registro completo e evidência:** [Defeito 02](./Defeito.md#defeito-02).


## 5. Aprendizados

1. Foi possível planejar e executar testes com base na experiência prévia em aplicações semelhantes.
2. A criação de casos de teste em Gherkin e no formato ISO demanda tempo e organização, sendo muito moroso
3. Estratégias exploratórias, combinadas com heurísticas e critérios de verificação, se mostraram muito úteis em entregas com regras de negócio ainda pouco definidas.
4. todo
5. todo

**Integrantes:** Dennys, Isabella Henriques, Patrick Aguiar, Taís Santos e Yara Rodrigues