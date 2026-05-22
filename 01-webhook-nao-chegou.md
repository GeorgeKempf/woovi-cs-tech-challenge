# Ticket #01 — Webhook não chegou após pagamento confirmado

## 1. Compreensão do problema
O pagamento das cobranças foi concluído (`COMPLETED`), porém o cliente não recebeu o webhook `OPENPIX:TRANSACTION_RECEIVED`. Mesmo esperando mais de 40 minutos.

O problema não parece estar no pagamento, mas sim em alguma falha na comunicação entre a Woovi e o sistema do cliente. Como eles dependem do webhook para liberar saldo ao usuário final, podendo gerando reclamações de “pagou e não caiu”.

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