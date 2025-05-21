De modo abstrato, o compilador é um programa que converte código de uma
linguagem para outra. Como se fosse uma função do tipo `compilador(str) -> str`.
No caso de compiladores que emitem código de máquina ou bytecode, seria mais
preciso dizer `compilador(str) -> bytes`, mas a idéia básica é a mesma.

De forma geral o processo é dividido em etapas como abaixo

```python
def compilador(x1: str) -> str | bytes:
    x2 = lex(x1)        # análise léxica
    x3 = parse(x2)      # análise sintática
    x4 = analysis(x3)   # análise semântica
    x5 = optimize(x4)   # otimização
    x6 = codegen(x5)    # geração de código
    return x6
```

Defina brevemente o que cada uma dessas etapas realizam e marque quais seriam os
tipos de entrada e saída de cada uma dessas funções. Explique de forma clara o
que eles representam. Você pode usar exemplos de linguagens e/ou compiladores
conhecidos para ilustrar sua resposta. Salve sua resposta nesse arquivo.

# lex(código_fonte: string) -> lista de tokens
A análise léxica consite na separação do código fonte , que será interpretado como string, e na sua divisão em tokens, que consiste em separar todos os elementos do código nas menores unidades com sentido do seu código, como: identificadores, palavras-chave, etc. 
 
# parse(tokens: list) -> árvore
 Ele vai receber a lista de tokens passados pela a análise léxica para criaras árvores sintáticas, que podem ser tanto concretas(CST) quanto abstratas(AST). A análise sintática na maioria dos compiladores é feita com base nas árvores abstratas(AST). A árvore representa a estrutura gramatical do programa. 
 Exemplo: x = 2+3 formaria uma árvore sintática de atribuição da váriável x juntamente com uma árvore sintática de operação dentro dela, lembrando que essa expressão gera 5 tokens.

# analysis(árvore) -> árvore_corrigda
Essa fase consiste na correção semântica da árvore sintática, verificando se os elementos passados fazem sentido tipos, escopos, regras, condições, etc. Ela avisa os erros da árvore para que possa ser corrigido.
Exemplo qualquer: int x = "abc"  verifica se variável foi declarada e se seus tipos são compatíveis.
 

# optimize(árvore_corrigida) -> árvore_otimizada
Complete as ? e responda aqui!

optimize(ast: tree) -> tree
Essa fase recebe a árvore sintática corrigida e cria uma árvore otimizada que tem como objetivo melhorar o desempenho do código
Exemplo: no código temos x= 2+3 ele será otimizado para x=5

# codegen(árvore_otimizada) -> código_em_bytes
transforma a árvore otimizada em um código de máquina ou código intermediário que poderá ser executado pela máquina para cumprir o que o código original pretendia.
Exemplo: gera instruções de assembly para o computador.