# 4. Projeto da Solução

## 4.1 Arquitetura escolhida

A arquitetura escolhida para o Harness é baseada em um grafo de estados com execução orientada por ferramentas e controle explícito do ciclo de execução.

A escolha está relacionada ao comportamento identificado no processo de negócio: uma solicitação do gestor pode exigir múltiplas consultas, e o resultado de uma etapa pode determinar quais ações deverão ser realizadas posteriormente.

O Harness precisa manter o estado da investigação, controlar a execução das ferramentas, aplicar permissões e limites e permitir que o fluxo avance ou seja interrompido conforme os resultados obtidos.

## 4.2 Por que essa arquitetura foi escolhida

A arquitetura foi escolhida principalmente pelos seguintes fatores:

- **Controle do estado:** permite representar explicitamente em qual etapa da investigação o agente se encontra.
- **Fluxo dinâmico:** permite que o resultado de uma ferramenta influencie a decisão sobre o próximo passo.
- **Governança:** facilita a aplicação de permissões, limites e pontos de intervenção.
- **Observabilidade:** facilita registrar as etapas executadas e seus resultados.
- **Tratamento de falhas:** permite representar caminhos alternativos para erros.
- **Intervenção humana:** permite interromper e retomar a execução em pontos definidos.

A principal característica que diferencia essa abordagem para o problema deste projeto é a possibilidade de representar a investigação como um fluxo controlado, sem depender exclusivamente do comportamento implícito do modelo.

## 4.3 Comparação com as alternativas consideradas

| Abordagem | Por que poderia ser utilizada | Por que não foi escolhida |
|---|---|---|
| **ReAct** | Alterna entre raciocínio, ação e observação de ferramentas. | Sozinha, não oferece estrutura suficiente para representar explicitamente estados, permissões, limites e intervenção. |
| **Skills / Permissions** | Organiza capacidades e controla ações disponíveis ao agente. | Resolve principalmente capacidades e autorização, mas não define o ciclo completo de investigação e gerenciamento de estado. |
| **CodeAct** | Permite gerar e executar código para tarefas flexíveis. | Adiciona uma superfície de execução maior e não é necessária para o problema principal do protótipo. |
| **RLM** | Pode ser útil para exploração iterativa de grandes contextos. | Não é necessária para demonstrar o problema central do Harness e adicionaria complexidade à solução. |

Essas abordagens não são necessariamente incompatíveis com a arquitetura escolhida. Algumas podem ser utilizadas como mecanismos complementares.

## 4.4 Papel do Harness

A arquitetura separa a responsabilidade de decisão da responsabilidade de execução controlada.

![alt text](/docs/img/Harness.png)


O agente interpreta a solicitação, analisa os resultados e decide os próximos passos. O Harness garante que essas ações sejam executadas dentro das regras definidas.

## 4.5 Trade-offs

A principal vantagem da abordagem é o maior controle sobre a execução.

Como contrapartida, a utilização de estados explícitos aumenta a complexidade de implementação em comparação com uma abordagem em que o modelo recebe ferramentas e decide livremente como utilizá-las.

Esse trade-off é considerado adequado ao problema porque o objetivo do projeto não é apenas permitir que o agente execute ações, mas investigar como controlar e coordenar essa execução.

## 4.6 Limitações

A arquitetura será validada inicialmente em um protótipo com dados e ferramentas simulados.

O projeto não pretende demonstrar integração completa com a infraestrutura real, desempenho em escala de produção ou custos reais de execução.

A avaliação será concentrada na capacidade do Harness de coordenar uma investigação, controlar ferramentas, manter estado e produzir uma execução observável e controlada.
