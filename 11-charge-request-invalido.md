## Ticket #11 — /chargeretorna sucesso mas o split não foi aplicado como esperado

## 1. Compreensão do problema

O cliente está criando uma cobrança pela API usando o endpoint `/charge` e informando um split no corpo da requisição.

A requisição retorna sucesso, com status 200, porém os dados de split retornados na resposta são diferentes do que ele enviou.

Ele enviou um split com `value: 510`, mas na resposta o valor retornou como `value: 50`.

Além disso, apareceu um `SPLIT_PARTNER` na resposta, mesmo o cliente não tendo enviado esse split na requisição.

O cliente quer entender por que o split enviado foi alterado e por que apareceu um split adicional na cobrança.

## 2. Plano de investigação


## 3. Hipóteses 


## 4. Mensagem para o cliente


## 5. Acompanhamento interno

