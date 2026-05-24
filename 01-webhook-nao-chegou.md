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

1. **Falha na entrega automática do webhook**
   - Pensei nisso porque o reenvio manual funcionou, então talvez o problema tenha sido no fluxo automático de envio.
   - Confirmaria olhando os logs de envio e as tentativas de retry.

2. **Problema parcial ou intermitente**
   - Como outras cobranças chegam normalmente, não parece ser uma falha geral.
   - Confirmaria verificando se outros clientes ou cobranças tiveram atraso parecido no mesmo período.

3. **Configuração do webhook**
   - Eu também validaria se o webhook cadastrado está correto, mesmo sendo menos provável, porque o cliente informou que recebe outras cobranças.
   - Confirmaria comparando a URL configurada e os eventos habilitados.

## 4. Mensagem para o cliente

Boa tarde, tudo bem?

Vou verificar os IDs que você me encaminhou, junto com as cobranças para entender melhor se houve algum atraso ou falha no envio do webhook, vou verificar também se teve mais casos parecidos.

Assim que eu conseguir mais informações eu lhe retorno.

## 5. Acompanhamento interno

Se eu identificasse falha no envio automático do webhook, abriria um chamado interno para o time responsável verificar o problema.

Caso percebesse que aconteceu com outros clientes também, trataria como possível incidente interno para investigar o impacto.
