
## DesafioWes - Vaga Dev

-Repositório criado para armazenar o conteúdo do desafio proposto pela Kinghost.


## Qual objetivo do projeto

-Esse projeto visa criar um front-end para consumir a [API da Marvel](https://developer.marvel.com/documentation/authorization)


## Tecnologias Utilizadas


-JavaScript, HTML, CSS - Utilizei pois e a linguagem que tenho um pouco de conhecimento e estou estudando ultimanente.


## Requisitos

-A aplicação em si não precisa de nenhuma tecnologia especifica, basta fazer a manipulação dos arquivos no FTP que ira funcionar.


## Como executar

- Basta clonar esse repositorio: 
git clone https://github.com/wesleibl/desafioWes.git



## Como funciona a conexao a API

-Nos arquivos .html, possuem a tag <script> dentro do script, foi criado um fetch() fazendo a conexao com url distintas de cada personagem.
Foi preciso gerar a Key de autenticação no site da Marvel: https://developer.marvel.com/docs
  
-Deve fazer um hash de md5(ts+privateKey+publicKey)
o resultado sera sua hash para conexão, ele tambem pede o timespam
no exemplo um usuario com a chave: public key of "1234" e a private key of "abcd" podera fazer conexoes validas usando: http://gateway.marvel.com/v1/public/comics?ts=1&apikey=1234&hash=ffd275c5130566a2916217b101f26150 (o valor do hash:ts+privateKey+publicKey)

-Na function getContent(), conseguimos fazer a conexão e precisamos declarar apartir de qual item do Array na API queremos pegar, na funçao foi declarado: 
let hero = data.data.results[0]
ou seja, a varivel hero agora ja esta na posição inicial para fazer as buscas.

-Na função exibirNome()
declaramos novamente a variavel hero para reconhcer a função getContent()
utilizando o  document.getElementById() conseguimos pegar a informação da API e passar para ID que esta declarada mais abaixo no HTML, detalhe nesse caso ser que nas thumbnails elas precisam especificar o .path e o .extension então foi necessario usar uma concatenação para unificar ambos, conforme abaixo:
let imgIron = `${hero.thumbnail.path}${'.'}${hero.thumbnail.extension}`

Podemos ver que nas paginas ironman.html e spiderman.html, o nome, imagem e descrição sao conetados da API, apenas as Comics que foram adicionadas manualmente.
