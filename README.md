# projeto code NOtranslate
projeto que tem como objetivo ignorar palavras chave / codigos ao traduzir um artigo estrangeiro sobre programação

A idéia desse projeto é ignorar códigos de programação ao traduzir uma página no chrome.
Quando você não sabe inglês e quer ler um artigo ensinando algum assunto sobre programação e o navegador traduz palavras chave como por exemplo "function" "Object" "String" "try {..}" etc

O projeto deve ser uma extensão pro Google Chrome e visa ignorar essas palavras que não devem ser traduzidas quando a pessoa for ler o artigo. Ainda estou pensando na melhor forma de fazer para evitar conflitos.

De início a minha ideia foi a seguinte:

1. cria uma lista de palavras que devem ser ignoradas ao traduzir a página
2. pega todo o codigo dentro do ```<body>``` da página
3. varre o ```<body>``` e vai colocando essas palavras dentro da tag ```<span>``` com a classe ```notranslate```

##### exemplo

```javascript
let word_list = [
"throw new Error",
"Error object",
"Try…catch",
"Throw",
"Error Handling",
"call stack",
"function"
];


word_list.forEach(word =>
{
   let replaceWith = '<span class="notranslate"> '+word+' </span>';
   document.querySelectorAll('body')[0].innerHTML = document.querySelectorAll('body')[0].innerHTML.split(word).join(replaceWith);
});

```
