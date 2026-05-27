## Ticket #05 — Boleto pago via Pix QR não dá baixa no DDA do banco

## 1. Compreensão do problema

Os boletos foram pagos normalmente via Pix QR Code e no painel da Woovi aparecem como `COMPLETED`.

Já no banco dos clientes os boletos continuam aparecendo como “em aberto”, mesmo após o pagamento. Isso acabou gerando um pagamento duplicado, pois um cliente achou que o primeiro pagamento não tinha sido reconhecido e pagou novamente.

Então o cliente quer entender porque o boleto continua em aberto no banco mesmo já tendo sido pago via Pix, e como evitar esse problema.

## 2. Plano de investigação

Primeiro eu confirmaria se os boletos realmente estão `COMPLETED` no painel e validaria os comprovantes enviados pelo cliente.

E depois confirmaria se esse problema aconteceu apenas com esses casos ou com outros clientes, se existir mais casos pode ter algum atraso ou falha na baixa do boleto do banco especifico.

## 3. Hipóteses 

1. **Atraso ou falha na baixa do DDA do banco**
   - O pagamento foi reconhecido pela Woovi como `COMPLETED`, mas o banco pode não ter atualizado ou pode ter ocorrido algum atraso na baixa do boleto.
   - Isso explicaria o boleto continuar aparecendo como “em aberto”.

2. **Problema específico de alguns bancos**
   - Como o cliente citou apenas alguns casos, verificaria se isso aconteceu somente com esses boletos ou com clientes do mesmo banco.
   - Isso ajudaria a entender se é um comportamento isolado ou algo recorrente.

## 4. Mensagem para o cliente

Boa tarde tudo bem?

Entendi a situação e vou verificar melhor o que pode ter acontecido. Vou confirmar os comprovantes que você me enviou e validar se houve mais casos parecidos nesse período.

Vou confirmar isso o mais rapido possivel, assim que eu tiver mais informações sobre o que aconteceu, retorno para você por aqui.

## 5. Acompanhamento interno

Se eu descobrisse que é atraso do DDA do banco, explicaria a situação para o cliente e pediria para avisar os clientes dele sobre esse possível atraso, para evitar novos pagamentos duplicados.

Se eu percebesse que isso aconteceu com outros clientes também, eu abriria um chamado interno e deixaria registrado para investigarem melhor o que pode estar acontecendo.