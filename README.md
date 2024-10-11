 # POC com Fetch - Imagens de Cachorros Aleatórios
o Codigo utilizado no <body> cria um botão que é utilizado como acionador do evento que realiza a busca da imagem aleatoria pela API "Dog CEO".

```html
<body>
    <h1>Imagens de Cachorros Aleatórios</h1>
    <button id="fetch-dog">Buscar Imagem</button>
    <div id="dog-image-container">
        <img id="dog-image" src="" alt="Imagem de cachorro aparecerá aqui" style="max-width: 500px;">
    </div>
</body>
```


 o script se trata da propria utilização da API invocada pelo evento acionado pelo botão no HTML.
```javascript
 <script>
    document.getElementById('fetch-dog').addEventListener('click', () => {
        fetch('https://dog.ceo/api/breeds/image/random')
            .then(response => response.json())
            .then(data => {
                document.getElementById('dog-image').src = data.message;
            })
            .catch(error => {
                console.error('Erro ao buscar imagem:', error);
            });
    });
</script>
```
``document.getElementById('fetch-dog').addEventListener('click', ...):`` Adiciona um ouvinte de evento ao botão. Quando o botão é clicado, a função dentro do ouvinte é executada.

``fetch('https://dog.ceo/api/breeds/image/random'):`` Utiliza a API Fetch para fazer uma requisição GET à API "Dog CEO". Esta API fornece uma imagem aleatória de um cachorro. A URL https://dog.ceo/api/breeds/image/random retorna um objeto JSON com a URL da imagem.

``.then(response => response.json())``: Quando a resposta é recebida, ela é convertida de formato bruto para JSON, permitindo que possamos acessar os dados retornados.

``.then(data => { ... })``: Após a conversão, o segundo then é chamado com o objeto JSON. O URL da imagem é acessado através de data.message e atualizado no elemento <img>.

``.catch(error => { ... })``: Captura qualquer erro que ocorra durante a requisição ou conversão, exibindo uma mensagem de erro no console para depuração.


