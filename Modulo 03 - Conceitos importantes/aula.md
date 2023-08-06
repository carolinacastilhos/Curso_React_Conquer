# Conceitos importantes

## Estado e imutabilidade

- existe duas formas de alterar dados:

1. alterar diretamente os valores de uma variável.
2. substituir o objeto que contem esses dados por uma nova cópia do objeto.

- props x states: props são utilizadas para transmitir dados entre componentes. Os states são gerenciados de forma parecida com variáveis declaradas dentro de uma função, são geradas no próprio componente.

- e deve ser seguido o conceito de imutabilidade, ou seja, nunca se deve alterar o valor do estado do componente, e sim fazer uma evolução deste valor.

- utilizamos a função setState para modificar o state na propriedade.

- localStorage: mantem os dados ao fechar a página. É possível ver oq está guardado no localStorage em: Application -> Storage -> localStorage do Dev tools.

- sessionStorage: apaga os dados ao fechar a página.

- sempre que estiver trabalhando com funções ou props de componentes separados, haverá 4 momentos para separá-lo e utilizá-lo:

1. declarando (criando) a função ou prop e especificando o que ela irá realizar.
2. criando sua interface no types.ts.
3. implementando-a no index.tsx do seu componente.
4. implementando-a no momento em que o componente é invocado no App.tsx ou na página que está importando-o.
