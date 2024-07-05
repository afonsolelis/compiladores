## Aula 1 - Prazer, Compiladores! 🤝👾 (Continuação)

### A Importância dos Compiladores

Na primeira parte da aula, vimos que os compiladores são como tradutores que transformam código escrito em uma linguagem de programação (que humanos entendem) para uma linguagem que o computador entende (linguagem de máquina). 

Imagine que você quer ensinar um amigo a fazer um bolo, mas ele só fala japonês. Você precisaria de um tradutor para transmitir as instruções corretamente, certo? É exatamente isso que um compilador faz! Ele garante que o computador compreenda e execute as instruções do seu programa.

## Governo Dos States Pede para Parar de Utilizar C e Assembly

<iframe width="560" height="315" src="https://www.youtube.com/embed/_heEHuBxIBQ?si=WW0l6RF-0MkX1o65" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Fases da Compilação: Uma Análise Detalhada

#### Para um problema:

![imagem](https://res.cloudinary.com/dyhjjms8y/image/upload/v1720096770/Captura_de_tela_2024-07-04_093903_wpi4k4.png)

A compilação, como vimos, é um processo dividido em etapas. Vamos entender melhor as três principais:

1. **Análise Léxica (Fase do "dicionário"):** Nesta fase, o compilador age como um leitor que examina o código letra por letra, agrupando-as em "palavras" com significado para a linguagem, como nomes de variáveis, palavras-chave (ex.: `if`, `else`, `for`) e operadores (+, -, *, /). Imagine um corretor ortográfico verificando cada palavra e sinal de pontuação do seu texto.

![imagem](https://res.cloudinary.com/dyhjjms8y/image/upload/v1720096770/Captura_de_tela_2024-07-04_093809_mawn2u.png)

#### Análise Léxica e Expressões Regulares

A Análise Léxica é a primeira fase de um compilador, responsável por dividir o código-fonte em uma sequência de tokens. Esses tokens representam as unidades básicas da linguagem, como palavras-chave, identificadores, números, operadores, entre outros.

Para realizar a Análise Léxica, uma técnica comumente utilizada são as expressões regulares (regex). As expressões regulares são padrões que descrevem um conjunto de cadeias de caracteres. Elas permitem identificar e extrair partes específicas de um texto com base em regras definidas.

As expressões regulares são compostas por caracteres literais e metacaracteres. Alguns metacaracteres comuns incluem:

- `.` (ponto): Corresponde a qualquer caractere, exceto uma nova linha.
- `*` (asterisco): Corresponde a zero ou mais ocorrências do caractere ou grupo anterior.
- `+` (mais): Corresponde a uma ou mais ocorrências do caractere ou grupo anterior.
- `?` (interrogação): Corresponde a zero ou uma ocorrência do caractere ou grupo anterior.
- `^` (circunflexo): Corresponde ao início da linha.
- `$` (cifrão): Corresponde ao final da linha.
- `[]` (colchetes): Define um conjunto de caracteres. Por exemplo, `[aeiou]` corresponde a qualquer vogal.

Além disso, existem classes de caracteres predefinidas, como:

- `\d`: Corresponde a qualquer dígito (0-9).
- `\w`: Corresponde a qualquer caractere alfanumérico (letra ou dígito).
- `\s`: Corresponde a qualquer caractere de espaço em branco (espaço, tabulação, nova linha).

Exemplo de expressão regular para identificar números inteiros:

```python
import re

# Expressão regular para números inteiros
pattern = r'\d+'

# Texto de exemplo
text = "Eu tenho 25 anos e meu irmão tem 30 anos."

# Encontrar todos os números inteiros no texto
matches = re.findall(pattern, text)

# Imprimir os números encontrados
for match in matches:
    print(match)
```

Nesse exemplo, a expressão regular `\d+` é usada para encontrar números inteiros no texto. O método `re.findall()` é utilizado para encontrar todas as ocorrências da expressão regular no texto. O resultado será:

```
25
30
```

As expressões regulares são uma ferramenta poderosa para a Análise Léxica, permitindo identificar e extrair tokens específicos do código-fonte. Elas podem ser combinadas com outras técnicas, como autômatos finitos, para construir um analisador léxico completo.

No entanto, é importante ressaltar que as expressões regulares têm suas limitações. Elas são adequadas para identificar padrões simples e regulares, mas podem se tornar complexas e difíceis de manter para linguagens com estruturas mais complexas. Nesses casos, outras técnicas, como a análise sintática, são necessárias para lidar com a estrutura hierárquica do código-fonte.

2. **Análise Sintática (Fase da "gramática"):**  Com as "palavras" identificadas, o compilador verifica se elas estão organizadas de forma correta, seguindo as regras gramaticais da linguagem. É como analisar se a ordem das palavras em uma frase faz sentido. Por exemplo, em português, dizemos "O gato comeu o peixe", e não "Comeu peixe o gato o". 

#### Análise Sintática

A Análise Sintática é a segunda fase de um compilador, que ocorre após a Análise Léxica. Seu objetivo é verificar se a sequência de tokens gerada pela Análise Léxica está de acordo com as regras gramaticais da linguagem de programação. Em outras palavras, a Análise Sintática verifica se o código-fonte possui uma estrutura válida.

Durante a Análise Sintática, o compilador constrói uma representação estruturada do código-fonte, geralmente na forma de uma árvore de análise sintática (AST - Abstract Syntax Tree). A AST representa a estrutura hierárquica do código, mostrando a relação entre os diferentes elementos da linguagem, como expressões, comandos e blocos de código.

Existem duas abordagens principais para a Análise Sintática:

1. Análise Sintática Descendente (Top-Down Parsing):
   Nessa abordagem, a análise começa a partir da regra gramatical mais geral e tenta derivar a sequência de tokens de entrada.
   O método mais comum é a análise preditiva recursiva, que utiliza recursão para percorrer a gramática e construir a AST.
   A análise descendente é adequada para gramáticas LL (Left-to-right, Leftmost derivation), onde é possível escolher a regra correta a ser aplicada com base nos próximos tokens de entrada.

2. Análise Sintática Ascendente (Bottom-Up Parsing):
   Nessa abordagem, a análise começa a partir dos tokens de entrada e tenta reduzi-los às regras gramaticais até chegar à regra inicial.
   O método mais comum é o LR (Left-to-right, Rightmost derivation), que utiliza uma tabela de análise para determinar as ações a serem tomadas com base nos tokens de entrada.
   A análise ascendente é adequada para gramáticas mais complexas e ambíguas, onde a escolha da regra correta depende dos tokens futuros.

Exemplo de Análise Sintática usando a abordagem descendente:

```python
def parse_expression(tokens):
    def parse_term(tokens):
        if tokens[0] == 'NUMBER':
            return ('NUMBER', tokens.pop(0)[1])
        elif tokens[0] == 'LPAREN':
            tokens.pop(0)
            expr = parse_expression(tokens)
            if tokens.pop(0) != 'RPAREN':
                raise ValueError("Parêntese de fechamento ausente")
            return expr

    def parse_factor(tokens):
        term = parse_term(tokens)
        while tokens and tokens[0] in ['MULTIPLY', 'DIVIDE']:
            op = tokens.pop(0)
            right = parse_term(tokens)
            term = (op, term, right)
        return term

    expr = parse_factor(tokens)
    while tokens and tokens[0] in ['PLUS', 'MINUS']:
        op = tokens.pop(0)
        right = parse_factor(tokens)
        expr = (op, expr, right)
    return expr
```

Nesse exemplo, a função `parse_expression` realiza a análise sintática de uma expressão aritmética simples. Ela utiliza funções auxiliares `parse_term` e `parse_factor` para lidar com os diferentes níveis de precedência dos operadores. A análise é feita de forma recursiva, consumindo os tokens de entrada e construindo a AST correspondente.

A Análise Sintática é uma fase crucial do compilador, pois garante que o código-fonte esteja estruturalmente correto antes de prosseguir para as próximas etapas, como a Análise Semântica e a Geração de Código. Ela também fornece informações importantes sobre a estrutura do programa, que são usadas nas fases posteriores do processo de compilação.

3. **Análise Semântica (Fase da "interpretação"):**  Após a análise sintática, o compilador precisa entender o significado do código. Ele verifica se as operações fazem sentido, se as variáveis foram declaradas corretamente e se os tipos de dados são compatíveis. É como analisar se as frases em um texto fazem sentido juntas e transmitem a mensagem desejada.

![imagem](https://res.cloudinary.com/dyhjjms8y/image/upload/v1720096769/Captura_de_tela_2024-07-04_093819_t5qtk7.png)

### Funcionamento de um Compilador

![imagem](https://res.cloudinary.com/dyhjjms8y/image/upload/v1720096643/Captura_de_tela_2024-07-04_093530_jkncgc.png)

![imagem](https://res.cloudinary.com/dyhjjms8y/image/upload/v1720096770/Captura_de_tela_2024-07-04_093751_rvtlu6.png)


### Vamos rodar tudo isso em Python!

Aqui está um exemplo de programa em Python que demonstra as três fases principais de um compilador: análise léxica, análise sintática e análise semântica.

```python
import re

# Definição dos tokens
tokens = [
    (r'\d+', 'NUMBER'),
    (r'\+', 'PLUS'),
    (r'\-', 'MINUS'),
    (r'\*', 'MULTIPLY'),
    (r'\/', 'DIVIDE'),
    (r'\(', 'LPAREN'),
    (r'\)', 'RPAREN'),
    (r'\s+', 'WHITESPACE')
]

# Análise Léxica
def lexical_analysis(code):
    lexemes = []
    while code:
        matched = False
        for token_expr, token_type in tokens:
            match = re.match(token_expr, code)
            if match:
                value = match.group()
                if token_type != 'WHITESPACE':
                    lexemes.append((token_type, value))
                code = code[len(value):]
                matched = True
                break
        if not matched:
            raise ValueError(f"Lexema inválido: {code}")
    return lexemes

# Análise Sintática
def syntax_analysis(lexemes):
    ast = []
    while lexemes:
        token_type, value = lexemes.pop(0)
        if token_type == 'NUMBER':
            ast.append(('NUMBER', int(value)))
        elif token_type in ['PLUS', 'MINUS', 'MULTIPLY', 'DIVIDE']:
            ast.append((token_type,))
        elif token_type == 'LPAREN':
            sub_expr = syntax_analysis(lexemes)
            ast.append(('EXPR', sub_expr))
            if lexemes.pop(0)[0] != 'RPAREN':
                raise ValueError("Parêntese de fechamento ausente")
        else:
            raise ValueError(f"Token inesperado: {token_type}")
    return ast

# Análise Semântica
def semantic_analysis(ast):
    if isinstance(ast, tuple):
        if ast[0] == 'NUMBER':
            return ast[1]
        elif ast[0] in ['PLUS', 'MINUS', 'MULTIPLY', 'DIVIDE']:
            return ast[0]
        elif ast[0] == 'EXPR':
            return semantic_analysis(ast[1])
    elif isinstance(ast, list):
        if len(ast) != 3:
            raise ValueError("Expressão inválida")
        left = semantic_analysis(ast[0])
        op = semantic_analysis(ast[1])
        right = semantic_analysis(ast[2])
        if not isinstance(left, int) or not isinstance(right, int):
            raise ValueError("Operandos inválidos")
        if op == 'PLUS':
            return left + right
        elif op == 'MINUS':
            return left - right
        elif op == 'MULTIPLY':
            return left * right
        elif op == 'DIVIDE':
            if right == 0:
                raise ValueError("Divisão por zero")
            return left // right

# Exemplo de uso
code = "2 + (3 * 4) - 5"
print("Código fonte:", code)

lexemes = lexical_analysis(code)
print("Análise Léxica:", lexemes)

ast = syntax_analysis(lexemes)
print("Análise Sintática:", ast)

result = semantic_analysis(ast)
print("Análise Semântica:", result)
```

Explicação do programa:

1. Análise Léxica:
   - Definimos os tokens que o compilador reconhecerá, como números, operadores e parênteses.
   - A função `lexical_analysis` recebe o código-fonte como entrada e retorna uma lista de lexemas (tokens) encontrados no código.
   - Utilizamos expressões regulares para identificar os tokens no código-fonte.

2. Análise Sintática:
   - A função `syntax_analysis` recebe a lista de lexemas como entrada e constrói uma árvore de análise sintática (AST - Abstract Syntax Tree).
   - Percorremos os lexemas e construímos a AST com base na estrutura da expressão.
   - Tratamos parênteses aninhados recursivamente.

3. Análise Semântica:
   - A função `semantic_analysis` recebe a AST como entrada e realiza a análise semântica.
   - Percorremos a AST recursivamente e avaliamos a expressão de acordo com as regras semânticas.
   - Verificamos se os operandos são válidos e realizamos as operações aritméticas correspondentes.

No exemplo de uso, fornecemos um código-fonte simples `"2 + (3 * 4) - 5"` e aplicamos as três fases do compilador:
1. Análise Léxica: Obtemos a lista de lexemas.
2. Análise Sintática: Construímos a AST a partir dos lexemas.
3. Análise Semântica: Avaliamos a expressão e obtemos o resultado final.

Esse programa é uma simplificação das fases de um compilador e serve para ilustrar os conceitos básicos envolvidos em cada fase. Em um compilador real, essas fases são mais complexas e envolvem mais etapas e detalhes.

### A Tabela de Símbolos: Organizando a Informação

A tabela de símbolos é como um dicionário que o compilador utiliza para armazenar e organizar informações sobre todos os elementos do seu código, como variáveis, funções e classes. 

Imagine que você está organizando uma festa e precisa controlar uma lista de convidados. Para cada convidado, você anota seu nome, número de telefone e se ele confirmou presença. A tabela de símbolos funciona de maneira similar, guardando informações importantes sobre cada elemento do seu código.

### Atividade em Sala de Aula

**Objetivo:**  Compreender a importância do Debbuging!

**Enunciado:** Sabe o código mais acima sobre compilação em python? Pois é, ele está quebrado, a sua missão é ajustar o código!

**Observação:**  Discuta com seus colegas as diferenças entre variáveis e constantes, e a importância de definir o tipo de dado para cada elemento. 
