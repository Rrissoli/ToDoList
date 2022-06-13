learning and training to --> DRY , SRP ,React, Saas, css modules, props, state,class component, function component.

React had created facebook
|--> componentized and replaced
|--> gerenciamento de estado
|--> reativo
--> Configurar o seu ambiente para rodar o projeto;
Aprendemos como configurar o seu ambiente para poder criar e rodar um projeto React, instalando o Node/npm e o GIT para controlarmos as versões e/ou baixarmos a aplicação do Github.
Diferenciar npx de npm;
Utilizamos o npx na aplicação e aprendemos a diferenciar o comando npx do comando npm, mostrando quando é melhor usar cada um.
Criar um projeto com create-react-app com template typescript usando npm;
Criamos um projeto utilizando npx, entendemos que o CRA (Create React App) tem possibilidade de criar projetos com template (optamos pelo typescript), escolhendo o npm como o nosso gerenciador de pacotes padrão.
O Create React App estrutura o projeto.
Entendemos como o Create React App estrutura a aplicação, vendo dos arquivos de configuração (tsconfig, package.json, package-lock.json entre outros), até as pastas/arquivos que serão atualizados por nós (pasta src, arquivos app.tsx, index.tsx, index.css entre outros).

Dentre todas as vantagens que o React nos proporciona, a componentização é uma das mais conhecidas, além de ser uma das marcas do React.

Vamos ver a criação de um class componente:

```javascript
class Botao extends React.Component {
  render() {
    return <button>Botão</button>;
  }
}
```

Só com esse pequeno componente, podemos ter várias informações interessantes, vamos separá-las em informações sobre componentização (em geral, tanto class components quanto function components) tanto sobre class components especificamente.

Sobre Componentização
Nome do Componente
O nome do componente deverá começar com letra maiúscula, mas por que?

Existe uma possibilidade no html de criar web-components, que nos permite criar tags html totalmente customizadas. Entre essas customizações, podemos customizar o nome da tag!

Para o React diferenciar um componente de um web-component, ele pede para que criemos um componente com a primeira letra maiúscula, assim ele consegue diferenciar por exemplo que <meuBotao /> é um web-component e <MeuBotao /> é um componente!

return e JSX
Para podermos criar um componente, fora a regra que citamos acima, precisamos retornar JSX, e o que seria isso exatamente?

O JSX é uma forma de "escrever HTML no JS", que é a forma que explicamos, mas não é exatamente isso.

O JSX não transfere o componente <Botao /> em HTML diretamente, antes disso, ele é transformado em uma elemento React, e aquele código é transformado em algo assim:

const Botao = React.createElement('button', {}, 'Botão');COPIAR CÓDIGO
Sem se atentar ao que isso faz agora, mas por debaixo dos panos o React transforma aquela sintaxe """HTML""" nesse palavrão que, na hora do ReactDOM.render, é transformado em DOM e, aí sim, transformado em HTML.

Você percebeu que a tag html é usada como primeiro parâmetro da função createElement como uma string?

Isso mostra que, para criarmos um componente, precisamos de uma tag "pai", logo, o código a seguir não funcionará:

```
class Botao extends React.Component {
render() {
return (
<p> Título do Botão </p>
<button>
Botão
</button>
)
}
```

Caso você precise fazer isso, leia sobre React.Fragment.

Sobre class Components
React.Component e render
Para criarmos um componente com class components, precisamos estender à classe React.Component. Nesta classe, existe apenas uma função obrigatória chamada render e, dentro dela, nós retornamos o JSX que precisamos para criar o componente!

Funciona a pasta public;
Abordamos sobre a pasta public, para que ela serve e por que raramente mexemos nela, mostramos também o arquivo index.html e como que o React popula ele com os componentes.
Criar um componente com class component e como utilizá-lo;
Criamos um componente com class component, mostrando toda a sintaxe desde o extends até o retorno e o export.
O que é JSX;
Vimos que o React retorna na verdade um JSX, não um HTML, também falamos de algumas diferenças entre os dois.
Criar um function component;
Também criamos um componente com function component (a forma mais atual de se escrever componentes desde a versão 16.8), e mostramos como é mais simples criarmos dessa forma.
Utilizar o método map para renderizar arrays.
Renderizamos arrays de JSX com o método map, mostrando que assim conseguimos aproveitar parte do JSX e mudar apenas o valor de item para item, utilizando assim o princípio DRY (Don't Repeat Yourself).

Nossa estrutura já está bem robusta e bem parecida do que será ao final, e só falta o cronômetro. Porém, a página ainda está com um aspecto feio, então iremos estilizá-la neste passo.

Primeiramente, instalaremos o Sass, que é o pré-processador CSS que iremos utilizar no curso. No próprio site do NPM acessível neste link, encontraremos a parte "Usage", em que diz que podemos instalar com npm install --save-dev sass apenas.

Portanto, copiaremos este comando e voltaremos ao VSCode, pois será desta forma que instalaremos no terminal, o qual abriremos apertando as teclas de "Ctrl" mais aspas simples, ou acessando "Ver > Terminal" na barra superior de opções.

Colaremos o comando npm install --save-dev sass e executaremos com a tecla "Enter" para instalarmos.

Feita a instalação, aparecerá uma "devDependencies" no package.json, que é uma dependência de desenvolvimento chamada "sass".

**UTILIZANDO O SAAS E CSS MODULES**
Agora poderemos nos atentar ao problema de sobreposição que falamos anteriormente.

Recapitulando, imaginemos que precisamos ter uma planilha com todas as classes criadas e dizer: "nao podemos utilizar "inputContainer" e nem "novaTarefa", porque já as usamos no código".

Seria muito maçante, pois podemos utilizar outras classes sem sobrepor a outras, existem soluções para isso.

Se temos um app e um site pequenos, usamos pacotes externos com CSS e colocarmos uma classe nossa, a possibilidade de ter uma sobreposição é bem alta, afinal estes arquivos importados são bem grandes.

Então, para conseguirmos criar uma classe única mesmo que o nome seja genérico para não termos o problema de sobreposição. Temos um pacote que o resolve, chamado CSS Modules.

Como estamos utilizando o TypeScript, precisaremos de um plugin chamado typescript-plugin-css-modules, que pode ser encontrado no site da NPM aqui com este pacote.

Na parte "Installation", vemos a forma de instalá-lo com npm install -D typescript-plugin-css-modules. Então copiaremos e acessaremos o terminal no VSCode com "Ctrl + aspas simples" ou em "Ver > Terminal" na barra superior de opções, para então colarmos o comando de instalação com o botão direito do mouse, pois o atalho "Ctrl + V" provavelmente não funcionará.

Executando com "Enter", esperaremos enquanto instala e voltaremos à página da NPM no navegador. Ainda na parte de "Installation" mais adiante, pede-se que coloquemos este plugin no arquivo tsconfig.json, pois é onde está a configuração de TypeScript.

Então copiaremos apenas a linha com o nome de "plugins": fornecido no site, sem copiar também o "compilerOptions":, pois já temos o em nosso arquivo.

{
"compilerOptions": {
"plugins": [{ "name": "typescript-plugin-css-modules" }]
}
}COPIAR CÓDIGO
Depois, retornaremos ao VSCode, e caso a instalação do pacote já tenha sido concluída, poderemos fechar o terminal.

Dentro do nosso arquivo tsconfig.json na aba lateral, acessaremos o "compilerOptions": e colaremos o código copiado na linha seguinte logo após "jsx:" "react-jsx",.

Com isso, teoricamente tudo já estará configurado na nossa aplicação. De volta ao browser, abriremos nossa página do "Alura Studies" e a atualizaremos com a tecla "F5".

Porém, ainda está "inputContainer", então ainda não funcionou. Para resolvermos isso, começaremos entendendo o "AppStyle".

Acessaremos style.scss da pasta "pages" no VSCode. Ao invés de usarmos este arquivo, precisaremos primeiro renomeá-lo para style.module.scss, afinal não será apenas um arquivo de estilo, e sim passará a ser um módulo.

A segunda mudança é, ao invés de só importarmos o .scss de uma só vez, o importaremos como se fosse um objeto. Então, no topo do código, faremos import style a partir de './style,module.scss'.

Copiaremos este style e, ao invés do className ser uma string, passará a ser uma variável JavaScript com uso das chaves. Dentro, colocaremos style.AppStyle para exportarmos um grande objeto no lugar de simplesmente aceitar strings como estilo, afinal já é um módulo.

import React from 'react';
import Formulario from '../components/Formulario';
import Lista from '../components/Lista';
import style from './style.module.scss';

function App() {
return (

<div className={style.AppStyle}>
<Formulario />
<Lista />
</div>
);
}

export default App;COPIAR CÓDIGO
Este objeto terá as classes que colocamos no css-modules. Neste caso, como o nome da classe que colocamos é AppStyle, usaremos o módulo style que importamos, seguido de ponto e de nome da classe.

Apertaremos "Ctrl + S" e voltaremos à nossa página no navegador, e a atualizaremos novamente.

Feito isso, acessaremos o "Inspect" com a aba "Elements" aberta, e abaixo da <div> de id="root", notaremos que está "style, que é o nome do arquivo que colocamos, seguido de underline, seguido do nome da classe AppStyle que estabelecemos, seguido de dois underlines e uma hash completamente aleatória para que seja único, isso tudo ao invés de somente "AppStyle".

Se nos atentarmos a não termos o mesmo nome de módulos por exemplo, o pacote ajuda a não termos problemas de sobreposição de CSS por darmos nomes iguais, pois é aleatório.

Para deixarmos mais polido, ao invés de usarmos style.module.scss, colocaremos o nome do módulo que queremos.

Por exemplo, se estamos no componente App(), renomearemos o nome do arquivo para App.module.scss, e importaremos o style deste módulo.

import React from 'react';
import Formulario from '../components/Formulario';
import Lista from '../components/Lista';
import style from './App.module.scss';

function App() {
return (

<div className={style.AppStyle}>
<Formulario />
<Lista />
</div>
);
}

export default App;COPIAR CÓDIGO
Voltando a página no navegador e atualizando com "F5", veremos que o nome da classe na <div> em "Elements" do "Inspect" estará muito mais descritiva. Ou seja, conseguimos ver que estamos no módulo App, o nome da classe é AppStyle e um hash aleatório novamente.

Portanto, conseguimos até saber onde está o estilo, resolvemos o problema de sobreposição e ainda deixamos o código mais polido.

Faremos a mesma coisa com os outros estilos que temos, começando pelo style.scss do componente "Botao" que será renomeado para Botao.module.scss.

Em seguida, importaremos style dentro de './Botao.module.scss', e o className mudará para style.botao entre chaves. Depois, apertaremos "Ctrl + S"para salvarmos e voltaremos ao navegador.

import React from 'react';
import style from './Botao.module.scss';

class Botao extends React.Component {
render() {
return (
<button className={style.botao}>
Botão
</button>
)
}
}

export default Botao;COPIAR CÓDIGO
Atualizando, inspecionaremos o botão e encontraremos a classe com o nome "Botao_botao\_\_ seguido de um hash aleatório. Então já está funcionando.

Após isso, iremos ao componente "Formulario" no VSCode e faremos a mesma metodologia, alterando o arquivo style.scss para Formulario.module.scss e depois importando o style de ./Formulario.module.scss' no topo do código.

Em seguida, alteraremos o primeiro className que passará a ser igual a style.novaTarefa entre chaves, e tanto o segundo quanto o terceiro nome serão style.inputContainer entre chaves também.

import React from 'react';
import Botao from '../Botao';
import style from './Formulario.module.scss';

class Formulario extends React.Component {
render() {
return (

<form className={style.novaTarefa}>
<div className={style.inputContainer}>
<label htmlFor="tarefa">
Adicione um novo estudo
</label>
<input
                    type="text"
                    name="tarefa"
                    id="tarefa"
                    placeholder="O que você quer estudar"
                    required
                />
</div>
<div className={style.inputContainer}>

//código posterior omitidoCOPIAR CÓDIGO
Já que estamos usando dois estilos, se estivéssemos utilizando o padrão que ficaria como {style.novaTarefa\_\_container} por exemplo, que normalmente é uma forma de boa escrita, poderia até funcionar.

Mas se colocássemos um hífen, teríamos problemas. Para resolver caso estivéssemos usando um estilo que possui -, poderíamos envolvê-lo em colchetes e inserir uma string com as aspas duplas.

Ou seja, é a mesma forma pois estamos utilizando um objeto de qualquer maneira, mas colocamos colchetes e string para caracteres especiais que o JavaScript não consegue entender.

Como não temos este problema em nosso projeto, podemos simplesmente usar style. com o nome da classe.

Salvando o arquivo, voltaremos ao navegador e inspecionaremos o estilo do fomulário para vermos o hash aleatório em class.

Estando tudo certo, iremos ao componente "Lista" para aplicarmos o mesmo processo. O arquivo de estilo será renomeado para Lista.module.scss e importaremos style no index.js.

Depois, mudaremos o primeiro className para style.listaTarefas e o segundo onde havia "item" para style.item entre chaves, e por fim atualizaremos a página no navegador para vermos o resultado.

import React from 'react';
import style from './Lista.module.scss';

function Lista() {
const tarefas = [{
tarefa: 'React',
tempo: '02:00:00'
}, {
tarefa: 'JavaScript',
tempo: '01:00:00'
}, {
tarefa: 'TypeScript',
tempo: '03:00:00'
}]
return (

<aside className={style.listaTarefas}>
<h2> Estudos do dia </h2>
<ul>
{tarefas.map((item, index) => (
<li key={index} classsName="item">
<h3> {item.tarefa} </h3>
<span> {item.tempo} </span>
</li>
))}
</ul>
</aside>
)
}

export default Lista;COPIAR CÓDIGO
No inspetor de código da lista, veremos os nomes com os hashs aleatórios, da mesma forma que os componentes anteriores.

Portanto, já conseguimos mudar todos os nossos estilos mais específicos, menos o reset que não é necessário, pois é algo mais global.

Usar o CSS inline;
Aprendemos como criar o CSS inline direto no atributo, como variável JS e utilizando condicionais para mudar o estilo.
Utilizar CSS e Sass no projeto;
Vimos como importar CSS e SASS no projeto é fácil dentro de um projeto criado com Create React App.
Colocar o CSS Modules em um projeto com Create React App + Typescript;
Configuramos o projeto para aceitar CSS Modules.
Vantagens de se utilizar CSS Modules.
Discutimos as vantagens de se utilizar CSS Modules na aplicação
#   T o D o L i s t  
 