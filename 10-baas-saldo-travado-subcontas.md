## Ticket #10 — BaaS: saldo travado em subcontas, operação parada

## 1. Compreensão do problema

O cliente informou que várias subcontas estão com saldo positivo aparecendo no sistema, porém o valor não está disponível para saque.

Ao tentar realizar o saque pelo endpoint `/subaccount/{id}/withdraw`, a API retorna `INSUFFICIENT_BALANCE` mesmo existindo saldo nas subcontas.

Além disso, existe uma diferença alta entre o saldo disponível e o valor do extrato, somando aproximadamente R$ 280 mil entre todas as contas afetadas.

Isso está impactando diretamente a operação do cliente e também os clientes finais deles.

## 2. Plano de investigação

Primeiramente eu verificaria se houve alguma mudança recente relacionada ao saldo das subcontas, regras de conciliação ou bloqueio de saldo.

Depois eu analisaria algumas das subcontas afetadas para comparar:
- saldo disponível;
- saldo do extrato;
- movimentações recentes;
- bloqueios ou reservas de saldo.

Também verificaria os logs do endpoint `/subaccount/{id}/withdraw` para entender porque o sistema está retornando `INSUFFICIENT_BALANCE`.

Por fim eu alinharia internamente com o time responsável antes de qualquer transferência manual entre subcontas e conta master.

## 3. Hipóteses 

1. **Saldo das subcontas pode estar bloqueado internamente**
   - O valor pode aparecer no extrato, mas ainda não estar liberado como saldo disponível para saque.
   - Isso explicaria o retorno de `INSUFFICIENT_BALANCE` mesmo com saldo visível.

2. **Problema de conciliação ou atualização de saldo**
   - Pode existir alguma falha na conciliação das subcontas fazendo com que o saldo exibido fique diferente do saldo realmente disponível.
   - Isso também explicaria a diferença entre extrato e saldo disponível.

3. **Mudança recente na regra de saldo ou saque**
   - Como o cliente perguntou se algo mudou recentemente, eu também verificaria se houve atualização em regras de saque, processamento ou retenção de saldo.
   - Talvez alguma alteração tenha impactado as subcontas afetadas.


## 4. Mensagem para o cliente

Boa tarde, tudo bem?

Entendi a situação e vou investigar o que pode estar causando essa diferença entre o saldo disponível e o saldo mostrado no extrato das subcontas.

Também vou verificar o motivo do endpoint `/subaccount/{id}/withdraw` estar retornando `INSUFFICIENT_BALANCE` mesmo com saldo aparecendo nas contas.

Vou alinhar internamente com o time responsável para entender se houve alguma alteração recente ou algum bloqueio relacionado às subcontas afetadas.

Assim que eu tiver uma resposta mais clara sobre o cenário e sobre a possibilidade de alguma ação temporária, retorno para vocês por aqui.

## 5. Acompanhamento interno

Como existe impacto financeiro alto e operação parada, eu trataria esse caso com prioridade alta internamente.

Também registraria todas as subcontas afetadas e a diferença de saldo informada pelo cliente para facilitar a investigação do time responsável.

Caso seja identificado algum problema de conciliação, atualização de saldo ou regra de bloqueio, eu abriria um chamado interno documentando o comportamento e os impactos causados na operação do cliente.