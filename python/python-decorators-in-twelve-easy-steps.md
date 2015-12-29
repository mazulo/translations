Post original: http://simeonfranklin.com/blog/2012/jul/1/python-decorators-in-12-steps/

## Entendendo Python decorators em 12 passos fáceis!

Ok, talvez eu esteja brincando. Como um instrutor Python, entender decorators é um tópico onde acho estudantes lutando constantemente após a primeira exposição ao assunto. O motivo é que decorators são difíceis de entender! Entendê-los requer compreender vários conceitos de programação funcional bem como se sentir confortável com algumas funcionalidades únicas da definição de função do Python e sintaxe de chamada de função. *Usar* decorators é fácil (veja na [Seção 10]())! Mas escrevê-los pode ser complicado.

Eu não posso tornar os decorators fáceis - mas talvez ao caminharmos por cada pedaço desse puzzle, um passo de cada vez, eu possa ajudar você a se sentir mais confiante em entender decorators[[1]](). Pelo motivo de decorators ser um assunto complexo, esse artigo vai ser longo - mas desista dele! Eu prometo fazer cada pedaço tão simples quanto possível - e se você entender cada pedaço, vai entender como decorators funcionam! Estou tentando assumir mínimo conhecimento de Python mas esse artigo provavelmente vai ser mais útils para pessoas que já tenha tido pelo menos um trabalho ocasional com Python.

Eu gostaria também de salientar que eu usei o módulo de doctest do Python para rodar os exemplos de código neste artigo. O código parece com uma sessão no console interativo do Python (`>>>` e `...` indicam comandos Python enquanto a saída tem sua própria linha). Eventualmente podem haver comentários enigmáticos que começam com "doctest" - eles são apenas diretivas para o doctest e podem ser ignorados.

### 1. Funções
Funções em Python são criadas com a palavra chave `def` e recebe um nome e uma lista opcional de parâmetros. Elas podem retornar valores com a palavra chave `return`. Vamos fazer e chamar uma função bem simples.

````shell
>>> def foo():
...	return 1
>>> foo()
1
````
O corpo da função (assim como todas as declarações multi-linhas em Python) é obrigatório e indicado por indentação. Podemos chamar funções acrescentando parênteses ao nome da função.

### 2. Escopo
