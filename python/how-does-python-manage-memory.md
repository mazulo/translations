Post original: http://effbot.org/pyfaq/how-does-python-manage-memory.htm

## How does Python manage memory?
Os detalhes do gerenciamento de memória do Python depende da implementação. A implementação padrão em C do Python usa contagem de referência para detectar objectos inacessíveis, e um mecanismo separado para coletar ciclos de referência, periodicamente executando um algoritmos de detecção de ciclo que procura por ciclos inacessíveis e deleta os objetos envolvidos. O modulo [gc](http://effbot.org/pyref/gc.htm) fornece funções para forçar a coleta do garbage collector, obter estatísticas de debugging, e ajustar os parâmetros do coletor.

Jython é baseado no runtime do Java, então o garbage collector da JVM é usado. O mesmo se aplica ao IronPython, que usa o garbage collector CLR. Essa diferença pode causar alguns problemas sutis de portabilidade se o seu código Python depende do comportamento da implementação de contagem de referência.

Algumas vezes objetos ficam presos em tracebacks temporariamente e, portanto, não são desalocados quando você esperava que fossem. Remova os tracebacks com:

````
import sys
sys.exc_clear()
sys.exc_traceback = sys.last_traceback = None
````

Tracebacks são usados para reportar erros, implementar debuggers e coisas relacionadas. Eles contém uma porção do estado do programa extraído durante o tratamento de uma exceção (normalmente, a exceção mais recente).

Na falta de circularidades e tracebacks, programas Python não precisam gerenciar memória explicitamente.

Porque Python não usa um esquema de garbace collector mais tradicional? Por uma coisa, essa não é uma feature padrão do C, portanto, não é portável. (Sim, nós sabemos sobre a lib Boehm GC. Ela tem pedaços de código assembler para a maioria das plataformas comuns, não para todas, e embora seja mais transparente, não é completamente transparente; patches são necessários para ter o Python funcionando com ele.)

GC tradicional também traz um problema quando Python está incorporado em outras aplicações. Enquanto em um Python independente não há problema em substituir o `malloc()` e `free()` padrão com versões fornecidas pela biblioteca GC, uma aplicação Python incorporada pode querer ter suas próprias substitutas para `malloc()` e `free()`, e não querer as do Python. Agora, Python funciona com qualquer coisa que implementa `malloc()` e `free()` apropriadamente.

Note que em sistemas usando GC tradicional, código que usa recursos externos sem explicitamente liberá-los podem ficar sem recursos antes do GC entrar em ação. Considere este exemplo:

````
class Resource:
	def __init__(self):
		self.handle = allocate_resource(name)
	def __del__(self):
		if self.handle:
			self.close()
	def close(self):
		release_resource(self.handle)
		self.handle = None
	...

for name in big_list:
	x = Resource(name)
	do something with x
	x.close()
````
