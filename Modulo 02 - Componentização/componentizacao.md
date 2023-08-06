# Componentização

## Como fucionam os componentes

- os componentes em react se assemelham a funções no JS em vários sentidos. Um deles é que eles recebem parâmetros de entrada q são chamadas de props. Eles retornam elementos que geralmente são JSX. Vantagens: reutilização, abstração e evitar redundância no código.
- importante que quebre o componente na menor unidade reaproveitável de código.
- os componentes podem se criados usando function declaration, function expression, arrow function e class.
  Exemplo com arrow function:

```const Hello = () => <h2>Hello World!</h2>;
export default Hello;
```

Neste exemplo, o componente Hello se trata de uma arrow function que retorna um elemento HTML h2, portanto se trata de um elemento JSX. Exporta apenas a const Hello, exemplo de abstração e reaproveitamento do código.

## Tipos de componentes

### Class components (Stateful components)

- a nomenclatura é declarada por meio de uma classe.
- exercem funções mais complexas.
- possuem um estado (state) e um ciclo de vida (life cycle).

### Functional Components (Stateless components)

- normalmente são declarados como uma função JS.
- função mis de display.
- os estados podem ser passados como props para os componentes filhos.
- não são capazes de gerenciar estado. Tem poder de receber essas propriedades como parâmetros (props) e retorna um elemento JSX. Então, geralmente, depende de um class component que possa enviar suas infos para ele e ele exercer seu papel no projeto.

Exemplo1 - Class component:

```import {Component} from 'react'

class Hello extends Component {
    render() {
        return <h3>Olá, {this.props.name}</h3>
    }
}
export default Hello
```

Exemplo2 - functional component:

```const Hello = () => <h2>Hello World!</h2>;

export default Hello;

const Hello = (props) => <h3>Olá, {props.name}</h3>
export default Hello

```

Esta função executa o mesmo papel do exemplo 1, mas com uma performance melhor e sintaxe mais amigável. A partir da versao 16.0 do react, foi introduzido a função do react hooks e através dela os functional componentes conseguem gerenciar estado. **Assim, Class components caíram em desuso no React. Dê preferência para functional components com Hooks para gerenciar estado e ciclo de vida.**

## Ciclo de vida

- os componentes que trabalham com state, sejam class ou functional components juntamente com hooks, possuem um ciclo de vida dentro da aplicação. Os componentes que são montados em tela, sofrem alterações durante o seu uso e depois são desmontados.
- a cada passo do seu ciclo de vida, é possível chamar métodos que interceptam esta renderização ou captam infos deste ciclo.

### Inicialização / Initialization

são obtidas as props e state para que o processo se tenha início; isto é feito pelo constructor.

### Montagem / Mounting

- o primeiro ciclo é o componentWillMount, que se passa antes da renderização
- depois disto ocorre a renderização, onde é construída a visualização do componente em tela
- por último, temos o processo de componentDidMount, que é o local recomendado para executar chamadas de APIs, referenciar componentes criados ou inclusive alterar um state.

### Atualização / Updation

- o primeiro processo é o componentWillReceiveProps que é executado toda vez que uma propriedade for atualizada, recebendo os novos elementos como parâmetros.
- após, temos o shouldComponentUpdate, que vai determinar se o componente deve realizar renderização novamente ou não, baseado nos parâmetros recebidos no componentWillReceiveProps.
- Caso seja necessário renderizar novamente, passamos para o componentWillUpdate e depois disto ocorre uma nova renderização e o componentDidUpdate.
- o mesmo ocorre com os states.

### Desmontagem / Unmounting

componentWillUnmont, onde os componentes serão desmontados, encerrando sua execução na aplicação.

## Criando um primeiro componente

- o arquivo main.jsx será responsávle pelo processo de renderização, enquanto no arquivo App.jsx serão carregados todos os componentes periféricos.
