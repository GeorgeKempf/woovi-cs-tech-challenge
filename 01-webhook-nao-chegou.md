# Ticket #01 — Webhook não chegou após pagamento confirmado

## 1. Compreensão do problema
O cliente Acme Gateway informa que três cobranças aparecem com status `COMPLETED`, porém o webhook `OPENPIX:TRANSACTION_RECEIVED` não foi recebido mesmo aguardando 40 minutos.

O problema não aparenta estar no pagamento em si, pois as cobranças já foram concluídas com sucesso. O problema está na comunicação automática entre a Woovi e o sistema do cliente, que depende do webhook para creditar saldo ao usuário final.

O impacto do problema é alto, pois enquanto o webhook não chega, o cliente final entende que “pagou e não caiu”, gerando reclamações e potencial escalabilidade do incidente caso mais transações sejam afetadas.

## 2. Plano de investigação

Verificar confirguração do webhook, se o mesmo esta configurado corretamente.

Validar as charges/transaction internamente
   - Confirmar se as três cobranças realmente estão com status `COMPLETED`;
   - Verificar a data e hora do webhook (se foi enviado)

Confirmar geração do evento
   - Verificar se o evento `OPENPIX:TRANSACTION_RECEIVED` foi criado corretamente.

Analisar entrega do webhook
   - Validar logs de envio;
   - Conferir possíveis falhas na entrega.
   - Verificar erros no recebimentos do webhook

 Investigar possível incidente
   - Verificar se outros clientes foram afetados no mesmo período;
   - Analisar filas de webhook e possíveis atrasos operacionais.

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