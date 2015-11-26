Post original: http://spin.atomicobject.com/2015/11/11/all-the-commits/

## Porque eu faço muitos git commit
Recentemente me juntei a um novo projeto, e um dos meus colegas de equipe me perguntou: "Porque você 'commita' tanto?". Eu decidi escrever este post para explicar meus motivos para ele e para qualquer outra pessoa que possa se deparar com meu trabalho no futuro.

### Commits pequenos podem ser seu melhor amigo.
Assim como funções, commits pequenos focam em uma coisa: uma simples mudança. Isso força nossa mensagem do commit ser mais descritiva (desculpa caras, "fixed some stuff" não está sendo nada descritivo).
Vamos dar uma olhada neste exemplo:

````
git commit -am "Updated 'Contact us' to 'Need Help? Contact Us!'"
````

Neste caso, você pode simplesmente olhar as mudanças feitas no commit, mas porque olhar no código quando a descrição está ali na sua frente? Commits pequenos tornam extremamente fácil encontrar uma mudança específica que entrou, especialmente quando tiver uma lista delas para analisar. Também tornam simples de ver como o projeto foi construído, pedaço por pedaço.

#### 1. Simplificam a revisão do código.
Commits pequenos tornam revisões de código muito mais fáceis. Permitem que você revise as mudanças, umas de cada vez, e compartilhe da mentalidade do autor. Os commits contam uma história, como se o autor estivesse explicando as mudanças para uma pessoa.

#### 2. Ajudam você a compartilhar conhecimento.
Recentemente, eu aprendi que adicionar uma quebra de linha depois da declaração de um `return` em JavaScript é a mesma coisa que não retornar nada (se você ficou curioso, veja [esta resposta no Stack Overflow](http://stackoverflow.com/a/8528606) para a explicação). Eu removi a quebra de linha e comitei o resultado:

````
git commit -am "A return followed by a line break doesn't actually return anything"
````

Graças aos pequeno commits, fui capaz de compartilhar esse conhecimento com meus colegas de equipe, sabendo que seria salvo para sempre. Se há uma coisa que eu aprendi como um programador, é que há uma razão para tudo. Algumas vezes, o raciocínio não está claro e o comentário do código não faz sentido (pode imaginar cara `return` de funções JavaScript tendo um comentário dizendo "Quebra de linha não vão retornar esse dado"). Pequenos commits ajudam a preencher esta lacuna.

(continua...)
