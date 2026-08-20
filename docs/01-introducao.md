# 1. Introdução

## 1.1 Contextualização

O avanço de sistemas baseados em agentes de inteligência artificial permite que aplicações deixem de apenas responder perguntas e passem a executar investigações orientadas a objetivos. No contexto de marketing, essa capacidade pode ser utilizada para apoiar gestores na análise de campanhas, clientes e resultados da operação.

Um gestor de marketing pode precisar tomar uma decisão utilizando informações distribuídas entre diferentes partes da operação. Essas informações podem estar presentes na memória da operação, no contexto do cliente, no histórico temporal, nos dados de campanhas, nas plataformas de mídia, no CRM, em conversas e em metodologias ou aplicações especializadas.

Nesse cenário, o principal desafio não é simplesmente disponibilizar essas fontes ao agente. É necessário coordenar a utilização dessas capacidades durante uma investigação, permitindo que os resultados obtidos em uma etapa influenciem as próximas decisões.

Este projeto investiga, portanto, a definição de um Harness capaz de atuar como runtime de coordenação entre o chat agêntico e as capacidades disponíveis.

## 1.2 Problema

Um gestor de marketing precisa obter respostas e tomar decisões utilizando informações distribuídas entre diferentes partes da operação.

Essas informações podem estar presentes na memória da operação, no contexto do cliente, no histórico temporal, nos dados de campanha, nas plataformas de mídia, no CRM, em conversas, em metodologias especializadas, em ferramentas e em aplicações de análise.

O agente precisa ser capaz de determinar quais informações são relevantes para uma determinada solicitação, consultar as fontes necessárias, observar os resultados obtidos, cruzar informações e decidir quais passos adicionais serão necessários antes de produzir uma resposta.

Por exemplo, uma solicitação como:

> "Por que a campanha do cliente X apresentou uma queda de desempenho na última semana?"

pode exigir a consulta aos dados da plataforma de mídia, ao CRM, ao contexto da operação e, dependendo dos resultados encontrados, a uma metodologia especializada de análise.

Assim, o problema central deste projeto é definir um runtime capaz de coordenar contextos, ferramentas, estados e limites de execução para transformar uma solicitação de um gestor de marketing em uma investigação orientada a objetivos e, posteriormente, em uma resposta útil e fundamentada.

## 1.3 Objetivo geral

Definir e prototipar um Harness para agentes de marketing capaz de coordenar uma investigação orientada a objetivos, permitindo que o agente utilize diferentes fontes de contexto e ferramentas de maneira controlada para produzir respostas fundamentadas.

### 1.3.1 Objetivos específicos

I - Identificar as fontes de contexto e capacidades necessárias para uma investigação de marketing;

II - Permitir que o agente determine quais ferramentas e fontes são relevantes para uma solicitação;

III - Permitir a execução de ferramentas e a observação de seus resultados;

IV - Permitir que os resultados obtidos influenciem os próximos passos da investigação;

V - Manter o estado necessário durante a execução;

VI - Controlar permissões e limites de execução;

VII - Permitir intervenção humana quando necessário;

VIII - Registrar informações relevantes da execução para observabilidade e análise;

IX - Tratar falhas de ferramentas e situações em que os dados disponíveis sejam insuficientes;

X - Produzir uma resposta fundamentada a partir das evidências obtidas;

XI - Avaliar diferentes abordagens arquiteturais para a implementação do Harness;

XII - Validar a abordagem escolhida por meio de um protótipo utilizando dados simulados.

## 1.4 Justificativas

Uma solicitação de negócio pode depender de informações provenientes de diferentes sistemas e metodologias. Conectar essas fontes a um agente, isoladamente, não garante que o agente saiba quando utilizá-las, como combinar seus resultados ou quando interromper uma investigação.

A existência de um runtime responsável por coordenar a execução permite separar a capacidade de decisão do agente das responsabilidades de controle da execução.

Essa separação pode proporcionar mecanismos explícitos para gerenciamento de estado, permissões, limites, observabilidade, tratamento de falhas e intervenção humana.

O projeto é relevante, portanto, por investigar como um Harness pode transformar um agente com acesso a múltiplas capacidades em um sistema de investigação controlada, em vez de simplesmente disponibilizar um conjunto de ferramentas ao modelo.

Além disso, o desafio não exige a construção da infraestrutura real da operação. Dessa forma, o projeto pode utilizar dados e integrações simulados para concentrar a investigação na arquitetura e no comportamento do runtime.
