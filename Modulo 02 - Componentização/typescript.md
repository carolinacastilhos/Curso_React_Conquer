# TypeScript

- mesmo fazendo uma aplicação em TS, todo código deve ser convertido em JS pq o browser não entende outra sintaxe que não a de JS.
- TS as variáveis são tipadas. Tanto as variáveis quanto os valores sãp tipados. Chamado de tipagem estática ou forte.
- No JS temos a tipagem dinâmica: valores tipados + variáveis não tipadas.

- no TS temos os tipos: number, string, boolean, Any, Array, void, null and undefined, unknown, enum e tuple.

- TS não diferencia inteiros de floats, isto significa que a gente pode declarar uma variável number que recebe um valor inteiro e depois recebe um valor float.

- Any: esta variável pode receber valor de qualquer tipo. Geralmente vem por uma API ou é declarada por um usuário.

- Array pode ser declarado de dois tipos:

1. let varList: number[] = [1,2,3,4];
2. let varList: Array<number> = [1,2,3,4];

- Enum: permite a declaração de valores constantes pré-definidos.
  Exemplo:

```
enum Cor {
    AMARELO,
    AZUL,
    VERMELHO,
}

let color: Cor;
color = Cor.AZUL;
```

- unknown: variável que ainda não sabemos o seu tipo, então pode ter seu tipo alterado para qualquer outro.

- undefined: são exatamente do tipo que os seus nomes dizem.

- void: é um retorno de funções que não retorna valor algum.

```function myFunction(): void {
    console.log("Eu não retorno valor algum");
}
```

- com o TS tbm podemos explorar todo o potencial de POO.

- para realizar a instalação do TS, precisa já ter o Node e o npm.
  Então digta o comando 'npm i -g typescript'. Após terminado o processo de instalação, pode digitar 'tsc -v' para ver se deu tudo certo, retornando a versão.

- a sintaxe do JSX se mantém a mesma para o template em JS ou TS.

- para criar um projeto com TS, pode escrever no terminal 'npx create-react-app my-projects-ts --template typescript'

- se já temos o projeto sem TS, digitamos 'npm install --save-dev typescript'. É necessário depois alterar dentro do arquivo package.json e adicionar 'tsc &&' no comando "build", juntamente com oq já estava escrito.
