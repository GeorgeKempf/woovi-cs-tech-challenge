# Ticket #01 — Webhook não chegou após pagamento confirmado

## 1. Compreensão do problema
O pagamento das cobranças foi concluído (`COMPLETED`), porém o cliente não recebeu o webhook `OPENPIX:TRANSACTION_RECEIVED`. Mesmo esperando mais de 40 minutos.

O problema não parece estar no pagamento, mas sim em alguma falha na comunicação entre a Woovi e o sistema do cliente. Como eles dependem do webhook para liberar saldo ao usuário final, podendo gerando reclamações de “pagou e não caiu”.

## 2. Plano de investigação

Primeiro eu verificaria se o webhook está configurado corretamente.

Em seguida eu verificaria se as três cobranças realmente estão como `COMPLETED` e se o evento `OPENPIX:TRANSACTION_RECEIVED` foi gerado, pois pela documentação esse evento deve ser enviado quando uma transação é recebida.

Depois eu analisaria os logs do webhook para saber se houve tentativa de envio, erro HTTP, timeout ou alguma falha no endpoint. Como a documentação informa que a Woovi faz retentativas em caso de falha, eu também verificaria se essas retentativas aconteceram.

Por fim, eu verificaria se o problema aconteceu apenas com esse cliente ou se existia algum atraso/incidente afetando outros webhooks no mesmo período.

## 3. Hipóteses 

1. Delay na fila do webhooks
2. Falha na entrega do webhook
3. Validar o Webhook cadastrado

## 4. Mensagem para o cliente

**Primeira mensagem ao cliente**

Boa tarde tudo bem?
Vou verificar a situação e ja lhe retorno.

**Explicando a situação**







## 5. Acompanhamento interno