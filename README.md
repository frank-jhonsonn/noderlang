# Noderlang - nó Erlang em Node.js

O Noderlang permite que os programas Node.js operem facilmente em ambientes BEAM,
aparecendo como um nó BEAM normal para outros nós.

``` js
const { Nó, envio, self, tupla: t } = require('noderlang');

// Inicia um nó de distribuição. Ele estará disponível como `js@hostname`.
Node.start('js', função assíncrona* root() {
  // Átomos são representados em JavaScript como Símbolos.
  send([Symbol('some_process'), 'foo@bar'], t(self(), Symbol('hello!')));

  Algo.startLink([]);

  enquanto (verdadeiro) {
    // `yield` é como `receive` em Erlang.
    const mensagem = rendimento;

    console.log(messagea);
  }
});

// Você também pode usar GenServer.
class Algo estende GenServer {
  assíncrona handleCall(valor) {
    // O valor de retorno é usado como resposta.
    retorne outroValor - 2;
  }

  assíncrono handleCast(valor) {
    // Fazer chamadas é simples.
    const otherValue = await GenServer.call(somePid, valor + 2);
  }

  assíncrona handleInfo(valor) {
    console.log('obteve informações', valor);
  }
}
```

## Status atual

Atualmente, isso é WIP. Funcionalidade básica como passagem de mensagens e GenServer
trabalho, mas a estabilidade geral precisa ser melhorada.

Isso é muito inspirado por [Pyrlang][].

[Pyrlang]: https://github.com/Pyrlang/Pyrlang
