Post original: http://www.b-list.org/weblog/2015/oct/13/wats-doc/

### Wat's up, doc?
No mesmo rumo da [maravilhosa palestra do Gary Bernhardt sobre JavaScript](https://www.destroyallsoftware.com/talks/wat), [há uma coleção de momentos de Python "wat"](https://github.com/cosmologicon/pywat) também que muitas vezes aparecem por aí. Há também um questionário relacionado na página deste último link (que eu não vou dar spoiler; você pode ler ele e checar suas respostas). Toda linguagem tem algumas partes não intuitiva — ou, no mínimo, aparentemente não intuitiva. Mas se você está trabalhando com Python, entender _porque_ esses pedaços de código se comportam dessa maneira é interessante, e potencialmente útil (OK, provavelmente não útil, mas no mínimo interessante). Então vamos dar uma olhada neles e ver o que realmente está acontecendo.

**"Convertendo para uma string e vice-versa"**
O exemplo é este:

````
>>> bool(str(False))
True
````

Esta é uma muito simples: `str(False)` é `"False"`, e `bool("False")` é `True`, porque qualquer string não vazia é `True` ("truthy", se você quer ser preciso, uma vez que a checagem boolean do Python raramente usa instancias reais de `bool`).

**"Misturar strings com inteiros"**

O exemplo:

````
>>> int(2 * 3)
6
>>> int(2 * '3')
33
>>> int('2' * 3)
222
````
