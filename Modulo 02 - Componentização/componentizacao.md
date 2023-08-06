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

- No main.jsx temos:

```
ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

Tudo que estiver dentro do .render () será renderizado no navegador. Neste caso, o nosso componente App está sendo renderizado dentro da tag React.StrictMode -> Isto traz algumas funcionalidades, como a identificação de métodos de ciclo de vidas seguros, detecção de efeitos colaterais inesperados e detecção de uso de recursos defasados.

- adicionamos a pasta styles dentro de "src" com o arquivo global.css e importamos ele no main.jsx. No main, tbm apagamos o import do index.html;

- após, fomos em App.jsx, apagamos tudo dentro do return da function App para iniciarmos o nosso projeto.

- para instalar pacote de ícones para usarmos no projeto, vamos no terminal do projeto e colocamos o comando 'npm i react-feather'. Com isto, no App.jsx podemos importar o componente {Plus} from 'react-feather'; e usar o componente <Plus /> que é o ícone de +.

- na pasta 'components' adicionamos a pasta 'Task' e criamos o arquivo 'index.jsx', onde vamos criar a export function Task() { }. É necessário utilizar o export function para que possamos exportar ela para ser usada em outro arquivo.

- como boa prática, sempre separe os componentes React em pastas descritivas que façam sentido para o projeto. Um dos nomes comuns desta pasta é 'components', onde ficará os componentes responsáveis por renderiza-lo na aplicação, regras de negócio e tbm algumas partes de lógica.

- outro tipo são os adapters/adaptadores/providers, que tem a funcionalidade de realizar qualquer chamada de API, seja ela por via websockets ou outra forma de comunicação com o serviço exterior.

- outra pasta é o tipo styles, onde fica todo o css da nossa aplicação ou styles components. Dentro desta pasta é possível fazer a estilização de cada component ou ainda a global.

## Propriedades - props

- são infos que são passadas para serem utilizadas dentro do nosso componente.
- podem ser do tipo string, number ou até funções.
- conseguimos passar estas infos através de tributos;
- para poder dizer quais são as props que queremos passar para o nosso componente, a gente define elas como atributos na hora de renderizar o mesmo.
  Exemplo1:

```const myElement = <Computer brand="Dell"/>;

```

Conseguimos ver que temos o atributo brand, e esta é a propriedade que estamos passando para dentro do componente.

Exemplo2:

```function Computer(props) {
  return <h3>Eu tenho um PC {props.brand} !</h3>;
}

```

Na função, o componente recebe o argumento com o objeto props. Neste componente Computer, a gente definiu que brand seria uma dessas props, então a gente consegue passar um valor diferente em cada local da aplicação. No nosso código, props.brand será responsável por renderizar o valor que estivermos passando para este atributo.

- Os componentes em react possuem uma característica em relação as suas propriedades que é chamada de unidirectional data flow. Isto significa que as props, que são os dados transferidos de um componente para o outro, possuem uma vida de mão única, podendo ser apenas transferidas dos componentes pais para os filhos e não vice-versa. Este comportamento traz algumas vantagens no Debugging, pois como a gente sabe da onde o dado sai e para onde ele vai, fica mais fácil para controlar estes erros. E garante um maior controle à aplicação e torna as aplicações mais eficientes.
