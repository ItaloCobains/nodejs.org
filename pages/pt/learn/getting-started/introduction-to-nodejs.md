---
title: Introdução ao Node.js
layout: learn
authors: ItaloCobains
---

# Introdução ao Node.js

Node.js é um ambiente de execução JavaScript de código aberto e multiplataforma.É uma ferramenta popular para quase qualquer tipo de projeto!

Node.js executa o motor JavaScript V8, o núcleo do Google Chrome, fora do
navagador. Isso permite que o Node.js seja muito performático.

Um aplicativo Node.js roda em um único processo, sem criar uma nova thread para
cada requisição. Node.js fornece um conjunto de primitivas de E/S assíncronas em
sua biblioteca padrão que impedem que o código JavaScript bloqueie. Geralmente,
as bibliotecas em Node.js são escritas usando paradigmas não-bloqueantes,
tornando o comportamento de bloqueio a execução e não a norma.

Quando o Node.js realiza uma operação de E/S, como ler da rede, acessar um banco
de dados ou o sistema de arquivos, em vez de bloquear e despediçar ciclos da CPU
esperando, o Node.js retorna as operações quando a resposta chega.

Isso permite que o Node.js lide com milhares de conexões simultâneas com um
único servidor sem introduzir o ônus de gerenciar a concorrência de threads, que
poderia ser uma fonte significativa de bugs.

Node.js tem uma vantagem única porque milhões de desenvolvedores frontend que
escrevem JavaScript para o navegador agora podem escrever o código do lado do
servidor além do código do lado do cliente, sem a necessidade de aprender uma
linguagem completamente diferente.

No Node.js, os novos padrões ECMAScript podem ser usados sem problemas, pois
você não precisa esperar todos os seus usuários atualizarem seus navegadores -
você está no controle de decidir qual versão do ECMAScript usar alterando a
versão do Node.js, e também pode habilitar recursos experimentais específicos
executando o Node.js com flags.

# Um Exemplo de Aplicação Node.js

O exemplo mais comum de Hello World em Node.js é um servidor web:

```cjs
const { createServer } = require('node:http');

const hostname = '127.0.0.1';
const port = 3000;

const server = createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

```mjs
import { createServer } from 'node:http';

const hostname = '127.0.0.1';
const port = 3000;

const server = createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

Para executar este código, salve-o como um arquivo `server.js` e execute `node
server.js` node seu terminal.

Este código primeiro inclui o [módulo `http` do Node.js](https://nodejs.org/api/http.html).

Node.js possui uma [biblioteca padrão](https://nodejs.org/api/) fantástica,
incluindo suporte de primeira classe para redes.

O método `createServer()` de `http` cria um novo servidor HTTP e o retorna.

O servidor é configurado para escutar na porta e nome de host especificados.
Quando o servidor está pronto, a função de callback é chamada, neste caso
informando-nos que o servidor está em execução.

Sempre que uma nova requisição é recebida, o [evento `request`](https://nodejs.org/api/http.html#http_event_request) é chamado, fornecendo dois objetos: uma requisição (um objeto [`http.IncomingMessage`](https://nodejs.org/api/http.html#http_class_http_incomingmessage)) e uma resposta (um objeto [`http.ServerResponse`](https://nodejs.org/api/http.html#http_class_http_serverresponse)).

Esses dois objetos são essenciais para lidar com a chamada HTTP.

O primeiro fornece os detalhes da requisição. Neste exemplo simples, isso não é
usado, mas você poderia acessar os cabeçalhos e dados da requisição.

O segundo é usado para retornar dados ao chamador.

Neste caso, com:

```js
res.statusCode = 200;
```

nós definimos a propriedade statusCode para 200, indicando um resposta
bem-sucedida.

Definimos o cabeçalho Content-Type:

```js
res.setHeader('Content-Type', 'text/plain');
```

e fechamos a resposta, adicionando o conteúdo como argumento para `end()`:

```js
res.end('Hello World\n');
```

### Mais exemplos

Veja https://github.com/nodejs/examples para uma lista de exemplos de Node.js
que vão além do hello world.
