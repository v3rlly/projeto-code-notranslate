# projeto code NOtranslate
projeto que tem como objetivo ignorar palavras chave / codigos ao traduzir um artigo estrangeiro sobre programação

A idéia desse projeto é ignorar códigos de programação ao traduzir uma página no chrome.
Quando você não sabe inglês e quer ler um artigo ensinando algum assunto sobre programação e o navegador traduz palavras chave como por exemplo "function" "Object" "String" "try {..}" etc

O projeto deve ser uma extensão pro Google Chrome e visa ignorar essas palavras que não devem ser traduzidas quando a pessoa for ler o artigo. Ainda estou pensando na melhor forma de fazer para evitar conflitos.

De início a minha ideia foi a seguinte:

1. cria uma lista de palavras que devem ser ignoradas ao traduzir a página
2. pega todo o codigo dentro do ```<body>``` da página
3. varre o ```<body>``` e vai colocando essas palavras dentro da tag ```<span>``` com a classe ```notranslate```

---


#### Primeira idéia

```javascript
// lista de palavras
let word_list = [
"throw new Error",
"Error object",
"Try…catch",
"Throw",
"Error Handling",
"call stack",
"function"
];


// para cada palavra da lista faça o seguinte
word_list.forEach(word =>
{
   // codigo pelo qual a palavra vai ser substituida
   let replaceWith = '<span class="notranslate"> '+word+' </span>';
   
   // substitui essa palavra em todo o <body> da página, pela mesma palavra só que dessa vez envolvida pela tag <span>
   document.querySelectorAll('body')[0].innerHTML = document.querySelectorAll('body')[0].innerHTML.split(word).join(replaceWith);
});

```


#### Exemplo com tags e classes

Alguns artigos costumam envolver o código dentro de alguma [tag](https://www.w3schools.com/tags/default.asp) ou [classe](https://www.w3schools.com/html/html_classes.asp) específica que se repete em todos os outros blocos de código. O desenvolvedor do site do artigo faz isso pra destacar o código com uma determinada sintaxe ou estilo diferente. No medium.com por exemplo, você tem a opção de destacar o código utilizando sintaxe de markdown e no final isso resulta no código entre as tags '\<pre\>\<\/pre\>'

Dito isso, uma outra ideia seria varrer o <body> pegar essa classe ou tag e adicionar incluir a nossa classe 'notranslate'

exemplo:

```html
<div class="code">
   Function foo(){
   console.log("bar")
   }
</div>
```


codigo:
```javascript

// seleciona todos os elementos que contenham a classe 'code'
let codeBlock = document.querySelectorAll(".code");

codeBlock.forEach(e =>
{
   // adiciona a classe 'notranslate'
   e.classList.add("notranslate")
});
```


é só isso mesmo..
