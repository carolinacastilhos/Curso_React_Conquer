# Como o React funciona

- Airbnb e Netflix usam o react em suas aplicações.

- SPA: Single Page Application -> uma SPA tende a carregar o essencial de uma página na sua primeira vez e conforme o usuário vai interagindo com a tela as outras informações vão sendo carregadas. Possui algumas desvantagens:

1. Falta de segurança: pode existir mais brechas de segurança que o normal e é mais difícil de testar, oq traz uma instabilidade, facilitando o ataque de hackers.
2. SEO: como na SPA nem sempre o conteúdo tem uma página única, isto acaba afetando neste monitoramento, podendo prejudicar o rankeamento nos mecanismos de buscas.
3. Primeiro carregamento demorado: como o conteúdo inicial pode levar mais tempo que o normal para ser carregado, pode ser que aplicação demore mais tempo para carregar por completo.

- Princípios do React:

1. Componentização: cada componente deve compor uma parte do quebra cabeça que no final, juntos, fazem sentido.
2. Abstração comum: para evitar que as soluções sejam feitas de forma diferente e duplicadas.
3. Saída de emergência: foi criado e é mantido pelo grupo Meta, e as suas atualizações são conforme a necessidade do time. Mas por ter se tornado uma ferramenta muito popular, teve que se adequar às necessidades de outros devs para continuar sendo usada e popular.
4. Estabilidade: haverá melhorias na ferramenta e atualizações, mas sua essencial permanecerá a mesma.

- JSX: é uma sintaxe de javascript que vai contribuir no desenvolvimento para que seja possível escrever menos código. O seu uso não é obrigatório, mas é recomendado. O navegador não consegue entender a sintaxe JSX, então é necessário que ele seja transpilado para JS e HTML. O JSX manipula o DOM (todo elemento renderizado na janela do navegador), mas tecnicamente será o JS o responsável pela lógica de renderizar o DOM; o JSX será o responsável por renderizar a lógica dentro do elemento HTML.
  Exemplo de código usando a sintaxe JSX:

```const element = <h1> Como usar o JSX </h1>
const root = ReactDOM.creatRoot(document.getElementById('root'));
root.render(element);
```

Tem uma variável element que contém uma tag HTML dentro. Depois, conseguimos ver este element ser renderizado dentro da variável root que é o elemento principal da tela.

Exemplo utilizando somente JS:

```const element = React.createElement('h1', {}, 'Não utilizando o JSX');
const root = ReactDOM.creatRoot(document.getElementById('root'));
root.render(element);
```

Neste segundo exemplo fica um pouco mais difícil de perceber oq está acontecendo. O element se trata de uma tag HTML, mas de forma diferente.

## Como configurar o ambiente

- baixar o NodeJs (versão LTS) e instalar
- no terminal podemos verificar a versão do node com o comando node -v e o comando npm -v
- NVM: Node Version Manager -> gerenciador de versões do node
- NPM: Node Package Manager -> gerenciador de pacotes do node

## Criando Projeto

- Vite: é uma ferramenta de construção originalmente criada para ser trabalhada com outros frameworks, mas com as suas atualizações tbm pode ser usada para criar projetos em react. Mais recomendado seu uso em projetos pequenos. Podemos criar aplicação escolhendo JS ou TypeScript.
- via terminal escrevemos o comando npm create vite@latest.
- definir o nome do projeto
- escolher qual framework irá usar, no caso é o react
- escolher qual a linguagem (JS ou TS)
- com isto o projeto é criado
- entrar na pasta do projeto com o comando cd vite-project (que é o nome que demos para o projeto)
- e então executamos o comando npm install, que será responsável por instalar todas as dependências do projeto
- abrir pelo terminal o vs code, após a instalação, com o comando 'code .'
- no nosso projeto teremos a pasta node_modules, onde estarão todas as dependências do nosso projeto que foram instaladas
- é criado tbm o arquivo package.json, onde é inserido algumas infos importantes do projeto como o nome dele, a versão, etc.
- dentro da pasta src, que é a principal do projeto, encontraremos a pasta assets, onde ficam as imagens e outros arquivos como main.jsx (como se fosse a estrutura do projeto), App,jsx (conteúdo da página)
- para ver como o conteúdo está sendo renderizado no navegador, digitamos no terminal o comando 'npm run dev' e acessamos o link que ele fornece

## Configurando o Projeto

- plugins: ferramentas adicionais que usamos na nossa aplicação ou código para nos ajudar e evitar erros simples. Instalamos na aba extensões do VS code. Neste projeto vamos usar 3:

1. Color Highlight
2. vscode-styled-component
3. CSS Modules

- colocar um readme.md com infos como instruções, possíveis erros e versão do node e react que deve usar.

- outras duas ferramentas necessárias:

1. ESlint: no terminal ir até o projeto 'cd .\vite-project\', depois colocar 'npm i eslint --save-dev'. Após, digitamos 'npm init @eslint/config'. Se pedir para instalar um pacote adicional, pode colocar 'y'. Depois vai pedir algumas configurações: selecionamos então que o eslint vai checar a sintaxe e encontrar problemas, que estamos usando o JS modules e react. Vai perguntar se queremos usar agora o TS e podemos dizer que 'n'. Onde o browser está sendo executado colocamos navegador. Qual formato de arquivo? JS. Se precisar de uma dependência a mais: y. Qual gerenciador de pacotes estamos usando: npm.
2. Prettier

## Estrutura do React

- para criar um novo projeto podemos colocar dois comandos:

1. npx create-react-app -> se criarmos desta forma, precisamos colocar o npm install para instalar todas as dependências e para iniciar o projeto, colocamos npm start
2. npm init vite@latest -> para criar o projeto com o vite

- organização:

1. se criar um projeto com 5 págs ou mais, deve-se criar uma pasta 'pages' dentro do da pasta 'src'.
2. vai precisar criar tbm uma pasta 'routes' na 'src'.
3. criar pasta 'components', para os componentes em comum entre as págs.
