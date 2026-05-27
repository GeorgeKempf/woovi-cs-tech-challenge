## Ticket #08 — correlationIDé ignorado em /subaccount/{id}/credite/debit

## 1. Compreensão do problema

O cliente está implementando idempotência e auditoria nas movimentações de subconta (`credit_subaccount`, `debit_subaccount` e transferências internas).

O problema é que o `correlationID` enviado por eles no payload aparentemente não está sendo retornado nos endpoints consultados posteriormente.

Eles já investigaram diversos endpoints da API e perceberam que alguns retornam vazio, outros não possuem `correlationID` e alguns endpoints nem existem ou retornam erro.

Com isso, o cliente ficou sem uma forma clara de relacionar as movimentações internas da Woovi com os registros do sistema deles para auditoria e conciliação pós-incidente.

## 2. Plano de investigação

Primeiramente eu verificaria na documentação e internamente se existe algum endpoint que realmente retorne o `correlationID` das operações de subconta.

Depois eu validaria se o comportamento atual da API é realmente não retornar essas informações em operações internas como `credit_subaccount` e `debit_subaccount`.

Também verificaria se existe alguma alternativa de conciliação ou auditoria para esses casos, já que o cliente precisa relacionar as movimentações com o sistema interno dele.

## 3. Hipóteses 

1. **O `correlationID` pode não estar disponível nos endpoints atuais**
   - Os endpoints testados pelo cliente não retornam informações de auditoria como `correlationID`.
   - Isso pode indicar uma limitação atual das operações internas de subconta.

2. **As operações internas podem funcionar diferente das operações Pix**
   - O cliente percebeu que endpoints relacionados a Pix externos possuem comportamento diferente das transferências internas.
   - Isso pode explicar porque os dados de auditoria não aparecem nessas movimentações.

3. **Pode não existir um endpoint específico para esse tipo de conciliação**
   - Os endpoints testados retornaram erro, vazio ou informações incompletas.
   - Talvez atualmente não exista um endpoint preparado para auditoria forense dessas operações internas.

## 4. Mensagem para o cliente

Boa tarde, tudo bem?

Entendi a situação e vou verificar se atualmente existe algum endpoint que retorne essas informações para operações como credit_subaccount, debit_subaccount e transferências internas, ou se existe alguma outra alternativa recomendada para essa situação.

Também vou validar se isso é uma limitação atual dos endpoints de subconta ou se existe alguma informação não documentada que possa ajudar nesse caso.

Assim que eu tiver uma resposta mais clara, retorno para vocês por aqui.

## 5. Acompanhamento interno

Caso eu confirme que atualmente não existe endpoint retornando `correlationID` para operações internas de subconta, eu registraria essa limitação e abriria um chamado interno sugerindo essa melhoria.

Caso exista alguma outra forma de consultar essas informações, eu orientaria o cliente sobre como utilizar da melhor forma.

Também verificaria se a documentação dos endpoints de subconta poderia ser mais clara em relação às informações retornadas nessas movimentações internas.

