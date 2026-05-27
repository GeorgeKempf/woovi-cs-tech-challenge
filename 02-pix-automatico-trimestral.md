## Ticket #02 — Pix Automático trimestral entre painel e API

## 1. Compreensão do problema

Existe uma diferença entre o que aparece no painel e o que a API/documentação aceita. No painel, o cliente conseguiu selecionar a frequência trimestral e seguir o fluxo sem erros, mas pela API ele recebeu o erro `400 invalid enum value`.

Entendo que esse erro acontece quando a API espera um valor predefinido e recebe algo diferente do esperado. Nesse caso, aparentemente a API não está reconhecendo a frequência `QUARTERLY` como uma opção válida.

Isso me faz pensar que pode existir uma divergência entre painel, API e documentação.

## 2. Plano de investigação

Primeiramente eu faria uma comparação entre painel, API e documentação para ter certeza se estão de acordo uma com a outra.

Depois confirmaria os valores predefinidos (enum) da API para tirar a dúvida se a frequência trimestral realmente está sendo reconhecida, verificaria se a documentação esta atualizada.

Também testaria o fluxo do painel para validar se ele realmente está funcionando corretamente.

Caso eu confirmasse alguma divergência entre painel, API ou documentação, abriria um chamado interno para correção.

## 3. Hipóteses 

1. **Possivel divergencia entre painel e API**
    - Como o painel permite selecionar "Trimestral" mas a API não aceita `QUARTERLY` isso pode indicar uma divergência entre os dois, talvez o painel permita uma opção que a API ainda não reconhece ou suporta.
    
2. **O valor enviado está incorreto**
    - Pode ser que `QUARTERLY` não seja o enum correto que a API espera, o painel pode estar usando outro valor interno que não mostra para o cliente.

3. **Documentação desatualizada**
    - O cliente citou que na lista da documentação da API só tem `WEEKLY`, `MONTHLY`, `SEMIANNUALLY` e `ANNUALLY` isso me levanta a duvida se a documentação da API não foi atualizada com o novo enum

## 4. Mensagem para o cliente

Boa tarde, tudo bem?

Entendi o problema, vou comparar o painel, API e documentação e verificar se existe alguma divergencia entre eles, porque voce citou que na documentação aparecem apenas `WEEKLY`, `MONTHLY`, `SEMIANNUALLY` e `ANNUALLY`, enquanto no painel o trimestral funcionou normalmente.

Também vou confirmar se a API espera outro valor para a frequencia trimestral ou se existe alguma diferença entre o que está no painel e o que a API aceita.

Vou verificar a situação, assim que eu tiver uma resposta clara do que aconteceu eu lhe retorno.

## 5. Acompanhamento interno

Caso eu confirmar que o painel/API esta com uma divergencia eu abriria um chamado interno para o time responsável corrigir.

Caso o enum seja diferente do que está documentado, eu abriria um chamado sugerindo a alteração dessa possível desatualização da documentação.