# 3. Modelagem do processo de negócio

## 3.1 Análise da situação atual

No cenário considerado pelo projeto, informações utilizadas em decisões de marketing estão distribuídas entre diferentes partes da operação.

Uma solicitação do gestor pode envolver dados de plataformas de mídia, informações do CRM, contexto do cliente, histórico temporal e metodologias especializadas.

O problema não é apenas a existência dessas fontes. A dificuldade está em determinar quais delas são relevantes para uma solicitação específica e em qual ordem devem ser consultadas.

Uma investigação pode começar com uma consulta simples e, a partir do resultado, exigir novas consultas.

Dessa forma, o processo possui natureza dinâmica:

```text
Solicitação
    ↓
Interpretação
    ↓
Consulta
    ↓
Resultado
    ↓
Nova decisão
    ↓
Nova consulta
    ↓
Cruzamento de evidências
    ↓
Resposta
```

A arquitetura do Harness deve apoiar esse comportamento sem permitir que a autonomia do agente elimine os controles necessários para a execução.

## 3.2 Descrição geral da proposta

A proposta consiste em utilizar um Harness como runtime responsável por coordenar a investigação realizada pelo agente.

O agente recebe uma solicitação e decide quais informações ou capacidades podem ser necessárias. O Harness recebe as ações propostas, verifica as regras aplicáveis e executa as ferramentas autorizadas.

Os resultados retornam ao agente, que pode utilizá-los para decidir os próximos passos.

O processo pode continuar por múltiplos ciclos até que:

- o objetivo seja atingido;
- não existam mais informações necessárias;
- um limite seja atingido;
- ocorra uma falha sem alternativa;
- seja necessária intervenção humana;
- a execução seja explicitamente encerrada.

A proposta, portanto, separa a responsabilidade de **decidir** da responsabilidade de **executar de forma controlada**.

## 3.3 Modelagem dos processos

### 3.3.1 Processo Principal – Investigação e Ciclo de Vida da Solicitação

Este fluxo mapeia a jornada ponta a ponta do agente de IA desde a entrada da requisição pelo gestor até a entrega da recomendação final. Ele engloba a recuperação inicial de contexto, a interpretação de intenção, a tomada de decisão em malha fechada e o encerramento do processo.

![alt text](/docs/img/ModelagemProcessos.png)

### 3.3.2 Subprocesso de Governança – Execução de Ferramentas, Segurança e Falhas

Este subprocesso descreve o comportamento do Harness (Orquestrador) na intermediação de chamadas a APIs, sistemas de CRM, dados históricos e apps especializados. Ele unifica as políticas de autorização, os mecanismos de aprovação humana e o tratamento resiliente de falhas.

![alt text](/docs/img/Subprocesso.png)

