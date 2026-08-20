# AdzHub Harness

Protótipo de **Harness Agêntico** desenvolvido para o desafio da AdzHub.

O projeto investiga como um runtime pode **coordenar um agente de IA** durante investigações que dependem de múltiplas fontes de contexto e ferramentas.

## Problema

Um gestor de marketing pode precisar cruzar informações distribuídas entre diferentes partes da operação, como:

- contexto e memória da operação;
- dados de campanhas;
- plataformas de mídia;
- CRM;
- metodologias e ferramentas especializadas.

O desafio é permitir que o agente determine o que precisa consultar, utilize as ferramentas necessárias, observe os resultados e decida os próximos passos antes de produzir uma resposta fundamentada.

## Objetivo

Construir um protótipo de Harness capaz de:

- coordenar o ciclo de investigação;
- manter o estado da execução;
- controlar ferramentas e permissões;
- aplicar limites de execução;
- registrar o processo;
- permitir intervenção quando necessário;
- produzir uma resposta fundamentada.

## Arquitetura

A solução utiliza uma **arquitetura de orquestração baseada em grafo de estados**, com controle explícito do ciclo de execução.

```text
                         ┌─────────────┐
                         │   Gestor    │
                         └──────┬──────┘
                                │
                                ▼
                         ┌─────────────┐
                         │    Chat     │
                         └──────┬──────┘
                                │
                                ▼
                  ┌─────────────────────────┐
                  │         Harness         │
                  │                         │
                  │ Estado · Permissões     │
                  │ Limites · Execução      │
                  │ Observabilidade         │
                  └────────────┬────────────┘
                               │
                               ▼
                         ┌─────────────┐
                         │  Agente IA  │
                         └──────┬──────┘
                                │
                 ┌──────────────┼──────────────┐
                 ▼              ▼              ▼
          ┌────────────┐  ┌──────────┐   ┌──────────┐
          │Supercérebro│  │   Apps   │   │   APIs   │
          └────────────┘  └──────────┘   └──────────┘
```

O **Harness** é responsável pela governança da execução, enquanto o **agente** interpreta a solicitação, analisa resultados e decide os próximos passos.

## Caso de uso principal

> **Realizar uma investigação orientada a objetivo.**

Exemplo:

> "Por que o desempenho de uma campanha caiu nos últimos 7 dias?"

O agente deve ser capaz de consultar diferentes fontes, analisar os resultados, decidir se precisa de novas informações e produzir um diagnóstico fundamentado.

## Documentação

A documentação detalhada está disponível em [`docs/`](./docs/).

Principais documentos:

- [Problema](./docs/01-problema.md)
- [Contexto e objetivos](./docs/02-contexto-e-objetivos.md)
- [Modelagem do processo](./docs/03-modelagem-do-processo.md)
- [Projeto da solução](./docs/04-projeto-da-solucao.md)
- [Modelos de caso de uso](./docs/05-modelos-de-caso-de-uso.md)

## Status

**Em desenvolvimento.**

A etapa de descoberta, modelagem e definição da arquitetura já foi realizada. O próximo passo é transformar o caso de uso principal em um cenário executável e iniciar a implementação do protótipo.
