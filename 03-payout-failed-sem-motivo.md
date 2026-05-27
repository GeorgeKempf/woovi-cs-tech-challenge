## Ticket #03 — Pagamento FAILED com error.codee providerRejectedReasonvazios 

## 1. Compreensão do problema

O cliente realizou pagamentos pela API utilizando o endpoint `/api/v1/payment` e inicialmente os pagamentos retornaram com status `APPROVED`.

Porém alguns minutos depois foi recebido um webhook `OPENPIX:MOVEMENT_FAILED`, alterando o status dos pagamentos para `FAILED`.

O problema é que as informações de erro vieram vazias, sem `error.code`, `providerRejectedReason` ou qualquer descrição do motivo da falha.

Por conta disso o cliente não consegue identificar o que realmente aconteceu nem explicar o motivo da falha para os clientes finais.

## 2. Plano de investigação


## 3. Hipóteses 


## 4. Mensagem para o cliente


## 5. Acompanhamento interno
