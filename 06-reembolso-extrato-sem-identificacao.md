## Ticket #06 — Reembolso Pix aparece no extrato sem endToEndIdnem nome

## 1. Compreensão do problema

O cliente quer conciliar o extrato de abril, porém existe um lançamento de R$ 24,91 no dia 20/04 às 10:06 que aparece apenas como `Reembolso Pix`.

O problema é que não consta nome do destinatário, CPF, `endToEndId`, `correlationID` nem comentário da cobrança, dificultando a identificação de quem era aquele reembolso.

O cliente só conseguiu descobrir de quem era porque a pessoa ligou informando sobre o reembolso. Se isso não tivesse acontecido, ele não teria como identificar no extrato.

Então o cliente quer entender se é possível incluir informações como destinatário e `endToEndId` no extrato para facilitar a conciliação dos reembolsos.

## 2. Plano de investigação

Eu primeiramente confirmaria se no sistema existem dados para identificar aquele reembolso.

Depois eu verificaria se essas informações de destinatário, `endToEndId` ou `correlationID` deveriam aparecer no extrato ou se isso é uma limitação atual.

Em seguida verificaria se a documentação fala algo sobre essas informações. Caso não tenha, seria interessante sugerir essa melhoria.

## 3. Hipóteses

1. **Os dados existem, mas não aparecem no extrato**
   - Pela documentação, o reembolso possui campos como `correlationID`.
   - Pode ser que essas informações existam internamente, mas não estejam sendo exibidas no extrato.

2. **Limitação do extrato**
   - Talvez o extrato atual não mostre informações como destinatário, `endToEndId` ou comentário do reembolso.
   - Isso explicaria a dificuldade do cliente para conciliar os reembolsos.

3. **Falta de clareza na documentação**
   - Como é o terceiro contato sobre o mesmo tema, pode indicar falta de clareza sobre quais dados aparecem no extrato.
   - Caso a documentação não explique isso, talvez seja interessante melhorar essa parte.

## 4. Mensagem para o cliente

Boa tarde, tudo bem?

Entendi a situação e vou verificar as informações do extrato de reembolso para confirmar se esses dados como `endToEndId`, `correlationID` e destinatário deveriam aparecer ou se existe alguma limitação atual.

Vou conferir tambem as informações da documentação e entender melhor como essas informações estão sendo tratadas nesse caso, assim evita que essa dúvida continue acontecendo.

Assim que eu tiver uma resposta mais clara, retorno para você por aqui.

## 5. Acompanhamento interno

Caso eu descobrisse que essas informações existem no sistema mas não aparecem no extrato, eu abriria um chamado sugerindo essa melhoria, pois ajudaria bastante na conciliação do cliente.

Caso seja uma limitação atual ou comportamento esperado, eu registraria o atendimento e explicaria melhor para o cliente como isso funciona hoje.

Se a documentação não estiver clara sobre isso, eu também sugeriria uma melhoria para deixar essas informações mais explicadas.