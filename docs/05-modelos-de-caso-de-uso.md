# 5. Modelos de Caso de Uso

## 5.1 Objetivo

Os casos de uso descrevem as principais interações entre o gestor de marketing e o Harness durante uma investigação orientada a objetivo.

O foco deste modelo é representar os comportamentos necessários para demonstrar o funcionamento do Harness, sem detalhar as implementações internas de cada componente.

## 5.2 Atores

### Gestor de Marketing

Responsável por iniciar uma investigação por meio de uma solicitação e receber a resposta produzida pelo agente.

### Agente de IA

Responsável por interpretar a solicitação, analisar os resultados obtidos e decidir quais passos devem ser realizados durante a investigação.

### Harness

Responsável por controlar a execução da investigação, manter o estado, validar permissões e limites, executar ferramentas e registrar os resultados.

### Fontes de capacidade

Representam as capacidades disponíveis para a investigação:

- **Supercérebro:** contexto, memória e informações da operação.
- **Apps:** metodologias e capacidades especializadas.
- **APIs:** dados provenientes de plataformas e sistemas externos.

## 5.3 Diagrama de Casos de Uso

[![](https://mermaid.ink/img/pako:eNp1VNuO2jAQ_RXL0kogAUsuXJqHSojdtkittFpKH5rw4E1mwSqxI9up6CI-pupD1Q_oF_BjHceBhd00D87M8ZmLxzPe0VRmQCO6UqxYk883iSD4XV2RiZEKNLlTXKS8YFy7nfegcaMVu_-y7dDJCoSB2SR2AsmAzCbLRLzwdj3n2kDONJlDWors8FNxqUnrnUQjfT0pNjxlh9-Hv6Brx_OyAJWCggclY6cc_lTaso5cFDq2y1G_m6GOS60717dbEzuJwNaAEkyfZ_eR59xmLUmdIGl9YEqAPqahywdXoBom8ZFYA3U0-y2mXqu1mHb7HrkHtuFPTBEuvmO9-Moe7pdst8_ZvmP7ZCqFLjcG6alNdWteEANHDMjtFqtneY-gFMux4uySGTpmSL5g_AyJYC0aYg8ccUBmGFApmWOB_0seOvIQj2Vk_srrMxUreg8blnIpquzwirn1L1BAVQFBYco0rtgoCy0vike63be2LE1g0ASGTeCgCRw6EER2dvnV0euuwxbQx85PZU5ODXHe_LUz77L1K7TuhjPvthAn3-R8PKoAdVMicMMw9mlAXvnuXoxCw7adgSYYR6EBPo0F7eDo84xGRpXQoTmonFmV7qxVQs0ackhohCI20reEJmKPNgUTX6XMj2ZKlqs1jR7ZRqNWFhkzcMMZzswzBasOaipLYWjk9f1R5YRGO7pFfez1Rm-CIBgHXj8cB-G4Q3_QaBT0-gNviLt93_fDYLzv0KcqrNdDyPL8_igcBaPBoEMh43g7n9x7Vj1r-39V94L0?type=png)](https://mermaid.ai/live/edit#pako:eNp1VNuO2jAQ_RXL0kogAUsuXJqHSojdtkittFpKH5rw4E1mwSqxI9up6CI-pupD1Q_oF_BjHceBhd00D87M8ZmLxzPe0VRmQCO6UqxYk883iSD4XV2RiZEKNLlTXKS8YFy7nfegcaMVu_-y7dDJCoSB2SR2AsmAzCbLRLzwdj3n2kDONJlDWors8FNxqUnrnUQjfT0pNjxlh9-Hv6Brx_OyAJWCggclY6cc_lTaso5cFDq2y1G_m6GOS60717dbEzuJwNaAEkyfZ_eR59xmLUmdIGl9YEqAPqahywdXoBom8ZFYA3U0-y2mXqu1mHb7HrkHtuFPTBEuvmO9-Moe7pdst8_ZvmP7ZCqFLjcG6alNdWteEANHDMjtFqtneY-gFMux4uySGTpmSL5g_AyJYC0aYg8ccUBmGFApmWOB_0seOvIQj2Vk_srrMxUreg8blnIpquzwirn1L1BAVQFBYco0rtgoCy0vike63be2LE1g0ASGTeCgCRw6EER2dvnV0euuwxbQx85PZU5ODXHe_LUz77L1K7TuhjPvthAn3-R8PKoAdVMicMMw9mlAXvnuXoxCw7adgSYYR6EBPo0F7eDo84xGRpXQoTmonFmV7qxVQs0ackhohCI20reEJmKPNgUTX6XMj2ZKlqs1jR7ZRqNWFhkzcMMZzswzBasOaipLYWjk9f1R5YRGO7pFfez1Rm-CIBgHXj8cB-G4Q3_QaBT0-gNviLt93_fDYLzv0KcqrNdDyPL8_igcBaPBoEMh43g7n9x7Vj1r-39V94L0)


## 5.4 UC-01 — Realizar investigação

**Objetivo:** obter uma resposta fundamentada para uma solicitação do gestor.

**Fluxo principal:**

1. Gestor envia uma solicitação.
2. Harness inicia a execução.
3. Agente interpreta o objetivo.
4. Agente solicita informações ou ferramentas.
5. Harness valida e executa as ações.
6. Agente observa os resultados e decide os próximos passos.
7. O processo se repete enquanto forem necessárias novas informações.
8. Agente produz a resposta.
9. Harness encerra a execução.

## 5.5 UC-02 — Executar ferramenta

**Objetivo:** permitir que o agente consulte uma fonte ou execute uma capacidade.

1. Agente solicita uma ferramenta.
2. Harness verifica permissões e limites.
3. Harness executa a ferramenta.
4. Resultado é retornado ao agente.

Caso a execução não seja permitida, o Harness bloqueia a operação.

## 5.6 UC-03 — Interromper e retomar execução

**Objetivo:** permitir controle humano ou automático sobre uma investigação em andamento.

1. Harness interrompe ou recebe uma solicitação de interrupção.
2. Estado da execução é preservado.
3. Execução pode ser retomada posteriormente.
4. Agente continua a investigação a partir do estado preservado.

## 5.7 Relação entre os casos de uso

O caso de uso principal é **Realizar investigação**. Os demais representam comportamentos necessários durante sua execução.

```text
                 Realizar investigação
                         │
              ┌──────────┴──────────┐
              ↓                     ↓
      Executar ferramenta    Interromper/retomar
