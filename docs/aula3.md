# Análise Léxica

## Introdução

A análise léxica, também conhecida como lexing ou tokenização, é o primeiro estágio na compilação de um programa. Esse processo envolve a conversão de uma sequência de caracteres de entrada em uma sequência de tokens, que são unidades atômicas significativas do código fonte. Esses tokens podem representar palavras-chave, identificadores, literais, operadores e outros elementos sintáticos.

## Objetivos da Análise Léxica

Os principais objetivos da análise léxica incluem:

1. **Simplificação da análise sintática**: Convertendo a entrada em tokens, a análise sintática (ou parsing) torna-se mais simples e eficiente.
2. **Detecção de erros léxicos**: Identificar e relatar erros na fase inicial da compilação.
3. **Remoção de elementos irrelevantes**: Eliminar espaços em branco, comentários e outros elementos que não afetam a execução do código.

## Componentes de um Analisador Léxico

Um analisador léxico geralmente é composto por:

- **Tabela de símbolos**: Armazena informações sobre identificadores e palavras-chave encontradas no código.
- **Regras léxicas**: Definem padrões para reconhecer tokens utilizando expressões regulares.
- **Autômatos Finitos**: Implementam as regras léxicas para varrer a entrada e produzir tokens.

## Processo de Análise Léxica

1. **Leitura da entrada**: O código fonte é lido como uma sequência de caracteres.
2. **Aplicação de regras léxicas**: Padrões são aplicados para identificar diferentes tipos de tokens.
3. **Geração de tokens**: Cada padrão identificado é convertido em um token correspondente.
4. **Tratamento de erros**: Se um padrão inválido é encontrado, um erro léxico é reportado.

## Exemplo de Tokens

Considere o seguinte trecho de código:

```python
int main() {
    int a = 10;
    int b = 20;
    int sum = a + b;
}
```

O analisador léxico pode gerar a seguinte sequência de tokens:

1. `int` (palavra-chave)
2. `main` (identificador)
3. `(` (símbolo)
4. `)` (símbolo)
5. `{` (símbolo)
6. `int` (palavra-chave)
7. `a` (identificador)
8. `=` (operador)
9. `10` (literal)
10. `;` (símbolo)
11. `int` (palavra-chave)
12. `b` (identificador)
13. `=` (operador)
14. `20` (literal)
15. `;` (símbolo)
16. `int` (palavra-chave)
17. `sum` (identificador)
18. `=` (operador)
19. `a` (identificador)
20. `+` (operador)
21. `b` (identificador)
22. `;` (símbolo)
23. `}` (símbolo)

## Desafio em Python

Agora que você compreendeu o básico sobre análise léxica, aqui está um desafio para colocar em prática seus conhecimentos. 

### Desafio: Implementar um Analisador Léxico em Python

Escreva um analisador léxico em Python que reconheça os seguintes tokens em uma expressão aritmética simples contendo inteiros, operadores (`+`, `-`, `*`, `/`) e parênteses:

- Inteiros: uma sequência de dígitos.
- Operadores: `+`, `-`, `*`, `/`
- Parênteses: `(`, `)`

Sua tarefa é implementar a função `lexical_analysis` que recebe uma string contendo a expressão aritmética e retorna uma lista de tokens.

```python
import re

def lexical_analysis(expression):
    # Definir os padrões para os tokens
    token_specification = [
        ('NUMBER',    r'\d+'),    # Inteiros
        ('PLUS',      r'\+'),     # Operador +
        ('MINUS',     r'-'),      # Operador -
        ('TIMES',     r'\*'),     # Operador *
        ('DIVIDE',    r'/'),      # Operador /
        ('LPAREN',    r'\('),     # Parêntese esquerdo
        ('RPAREN',    r'\)'),     # Parêntese direito
        ('SKIP',      r'[ \t]+'), # Espaços em branco
        ('MISMATCH',  r'.'),      # Qualquer outro caractere
    ]
    
    # Compilar as expressões regulares em um único regex
    tok_regex = '|'.join(f'(?P<{pair[0]}>{pair[1]})' for pair in token_specification)
    get_token = re.compile(tok_regex).match
    line = expression.strip()
    pos = 0
    tokens = []
    
    # Iterar sobre a string de entrada para encontrar os tokens
    while pos < len(line):
        match = get_token(line, pos)
        if match is None:
            raise RuntimeError(f'Erro léxico em {line[pos]}')
        pos = match.end()
        token_type = match.lastgroup
        if token_type == 'NUMBER':
            value = int(match.group(token_type))
            tokens.append((token_type, value))
        elif token_type != 'SKIP':
            tokens.append((token_type, match.group(token_type)))
    
    return tokens

# Teste seu analisador léxico
expression = "3 + 5 * ( 10 - 20 ) / 2"
tokens = lexical_analysis(expression)
print(tokens)
```

### Teste esperado

Para a expressão `"3 + 5 * ( 10 - 20 ) / 2"`, a saída esperada seria:

```python
[('NUMBER', 3), ('PLUS', '+'), ('NUMBER', 5), ('TIMES', '*'), 
 ('LPAREN', '('), ('NUMBER', 10), ('MINUS', '-'), ('NUMBER', 20), 
 ('RPAREN', ')'), ('DIVIDE', '/'), ('NUMBER', 2)]
```

Boa sorte e divirta-se resolvendo o desafio!

# Análise Sintática

## Introdução

A análise sintática, também conhecida como parsing, é o segundo estágio do processo de compilação. Ela envolve a análise da sequência de tokens gerada pelo analisador léxico para construir uma estrutura hierárquica, como uma árvore de análise sintática (AST - Abstract Syntax Tree). Essa árvore representa a estrutura gramatical do código fonte conforme definido pela gramática da linguagem de programação.

## Objetivos da Análise Sintática

Os principais objetivos da análise sintática incluem:

1. **Verificação da estrutura gramatical**: Garantir que a sequência de tokens obedeça às regras gramaticais da linguagem.
2. **Construção de estruturas hierárquicas**: Criar representações estruturais do código, como árvores de análise ou grafos.
3. **Detecção de erros sintáticos**: Identificar e relatar erros gramaticais.

## Componentes de um Analisador Sintático

Um analisador sintático geralmente é composto por:

- **Gramática da linguagem**: Um conjunto de regras que define a estrutura da linguagem.
- **Analisador léxico**: Um componente que fornece a sequência de tokens.
- **Algoritmo de parsing**: Responsável por construir a árvore de análise a partir dos tokens.

## Processo de Análise Sintática

1. **Recebimento dos tokens**: A sequência de tokens gerada pelo analisador léxico é recebida.
2. **Aplicação de regras gramaticais**: As regras gramaticais são aplicadas para construir a árvore de análise.
3. **Detecção de erros sintáticos**: Erros são detectados e reportados se a sequência de tokens não obedecer às regras gramaticais.

## Exemplos de Gramáticas

Considere a seguinte gramática para expressões aritméticas simples:

- Expressão → Termo {("+" | "-") Termo}
- Termo → Fator {("*" | "/") Fator}
- Fator → Número | "(" Expressão ")"

## Exemplo de Implementação

Abaixo está uma implementação básica de um analisador sintático para expressões aritméticas em Python. Ele utiliza um analisador léxico para gerar tokens e, em seguida, constrói uma árvore de análise sintática (AST).

```python
import re

# Analisador Léxico
def lexical_analysis(expression):
    token_specification = [
        ('NUMBER',    r'\d+'),    
        ('PLUS',      r'\+'),     
        ('MINUS',     r'-'),      
        ('TIMES',     r'\*'),     
        ('DIVIDE',    r'/'),      
        ('LPAREN',    r'\('),     
        ('RPAREN',    r'\)'),     
        ('SKIP',      r'[ \t]+'), 
        ('MISMATCH',  r'.'),      
    ]
    
    tok_regex = '|'.join(f'(?P<{pair[0]}>{pair[1]})' for pair in token_specification)
    get_token = re.compile(tok_regex).match
    line = expression.strip()
    pos = 0
    tokens = []
    
    while pos < len(line):
        match = get_token(line, pos)
        if match is None:
            raise RuntimeError(f'Erro léxico em {line[pos]}')
        pos = match.end()
        token_type = match.lastgroup
        if token_type == 'NUMBER':
            value = int(match.group(token_type))
            tokens.append((token_type, value))
        elif token_type != 'SKIP':
            tokens.append((token_type, match.group(token_type)))
    
    return tokens

# Analisador Sintático
class Parser:
    def __init__(self, tokens):
        self.tokens = tokens
        self.pos = 0
    
    def parse(self):
        return self.expression()
    
    def expression(self):
        node = self.term()
        while self.current_token() in ('PLUS', 'MINUS'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.term())
        return node
    
    def term(self):
        node = self.factor()
        while self.current_token() in ('TIMES', 'DIVIDE'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.factor())
        return node
    
    def factor(self):
        token = self.current_token()
        if token == 'NUMBER':
            self.next_token()
            return ('NUMBER', self.current_value())
        elif token == 'LPAREN':
            self.next_token()
            node = self.expression()
            if self.current_token() == 'RPAREN':
                self.next_token()
                return node
            else:
                raise RuntimeError("Erro: ')' esperado")
        else:
            raise RuntimeError(f"Erro: Token inesperado {token}")
    
    def current_token(self):
        return self.tokens[self.pos][0] if self.pos < len(self.tokens) else None
    
    def current_value(self):
        return self.tokens[self.pos - 1][1]
    
    def next_token(self):
        self.pos += 1

# Função principal para realizar a análise léxica e sintática
def main():
    expression = "3 + 5 * ( 10 - 20 ) / 2"
    tokens = lexical_analysis(expression)
    print("Tokens:", tokens)
    
    parser = Parser(tokens)
    ast = parser.parse()
    print("AST:", ast)

# Executar a função principal
if __name__ == "__main__":
    main()
```

## Desafio em Python

Agora que você compreendeu o básico sobre análise sintática, aqui está um desafio para colocar em prática seus conhecimentos.

### Desafio: Implementar um Analisador Sintático Completo

Escreva um analisador sintático que, além de analisar expressões aritméticas simples, seja capaz de analisar expressões com variáveis. Considere a seguinte gramática estendida:

- Expressão → Termo {("+" | "-") Termo}
- Termo → Fator {("*" | "/") Fator}
- Fator → Número | Identificador | "(" Expressão ")"
- Identificador → [a-zA-Z_][a-zA-Z0-9_]*

Implemente a função `parse` para lidar com variáveis e teste-a com uma expressão que inclua variáveis.

```python
import re

def lexical_analysis(expression):
    token_specification = [
        ('NUMBER',    r'\d+'),
        ('ID',        r'[a-zA-Z_][a-zA-Z0-9_]*'),
        ('PLUS',      r'\+'),
        ('MINUS',     r'-'),
        ('TIMES',     r'\*'),
        ('DIVIDE',    r'/'),
        ('LPAREN',    r'\('),
        ('RPAREN',    r'\)'),
        ('SKIP',      r'[ \t]+'),
        ('MISMATCH',  r'.'),
    ]
    
    tok_regex = '|'.join(f'(?P<{pair[0]}>{pair[1]})' for pair in token_specification)
    get_token = re.compile(tok_regex).match
    line = expression.strip()
    pos = 0
    tokens = []
    
    while pos < len(line):
        match = get_token(line, pos)
        if match is None:
            raise RuntimeError(f'Erro léxico em {line[pos]}')
        pos = match.end()
        token_type = match.lastgroup
        if token_type in ('NUMBER', 'ID'):
            value = match.group(token_type)
            tokens.append((token_type, value))
        elif token_type != 'SKIP':
            tokens.append((token_type, match.group(token_type)))
    
    return tokens

class Parser:
    def __init__(self, tokens):
        self.tokens = tokens
        self.pos = 0
    
    def parse(self):
        return self.expression()
    
    def expression(self):
        node = self.term()
        while self.current_token() in ('PLUS', 'MINUS'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.term())
        return node
    
    def term(self):
        node = self.factor()
        while self.current_token() in ('TIMES', 'DIVIDE'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.factor())
        return node
    
    def factor(self):
        token = self.current_token()
        if token == 'NUMBER':
            self.next_token()
            return ('NUMBER', self.current_value())
        elif token == 'ID':
            self.next_token()
            return ('ID', self.current_value())
        elif token == 'LPAREN':
            self.next_token()
            node = self.expression()
            if self.current_token() == 'RPAREN':
                self.next_token()
                return node
            else:
                raise RuntimeError("Erro: ')' esperado")
        else:
            raise RuntimeError(f"Erro: Token inesperado {token}")
    
    def current_token(self):
        return self.tokens[self.pos][0] if self.pos < len(self.tokens) else None
    
    def current_value(self):
        return self.tokens[self.pos - 1][1]
    
    def next_token(self):
        self.pos += 1

def main():
    expression = "x + 3 * ( y - 2 ) / z"
    tokens = lexical_analysis(expression)
    print("Tokens:", tokens)
    
    parser = Parser(tokens)
    ast = parser.parse()
    print("AST:", ast)

if __name__ == "__main__":
    main()
```

### Teste esperado

Para a expressão `"x + 3 * ( y - 2 ) / z"`, a

 saída esperada seria:

```python
Tokens: [('ID', 'x'), ('PLUS', '+'), ('NUMBER', '3'), ('TIMES', '*'), 
         ('LPAREN', '('), ('ID', 'y'), ('MINUS', '-'), ('NUMBER', '2'), 
         ('RPAREN', ')'), ('DIVIDE', '/'), ('ID', 'z')]
AST: ('PLUS', ('ID', 'x'), ('DIVIDE', ('TIMES', ('NUMBER', '3'), ('MINUS', ('ID', 'y'), ('NUMBER', '2'))), ('ID', 'z')))
```

Boa sorte e divirta-se resolvendo o desafio!


# Resumão!

## Análise de Compilação: Léxica, Sintática e Semântica

## Introdução

O processo de compilação de um programa pode ser dividido em várias fases distintas. Cada fase tem um papel crucial na transformação do código fonte em código executável. As três principais fases são a análise léxica, a análise sintática e a análise semântica.

## Análise Léxica

### Objetivo

A análise léxica, também conhecida como lexing ou tokenização, é a primeira etapa do processo de compilação. Seu objetivo é converter a sequência de caracteres do código fonte em uma sequência de tokens, que são as menores unidades significativas do código.

### Componentes

- **Tabela de símbolos**: Armazena informações sobre identificadores e palavras-chave.
- **Regras léxicas**: Definem padrões para reconhecer tokens usando expressões regulares.
- **Autômatos Finitos**: Implementam as regras léxicas para varrer a entrada e produzir tokens.

### Exemplo de Tokens

Para o código `int a = 10;`, os tokens podem ser: `int`, `a`, `=`, `10`, `;`.

### Implementação

```python
import re

def lexical_analysis(expression):
    token_specification = [
        ('NUMBER',    r'\d+'),
        ('ID',        r'[a-zA-Z_][a-zA-Z0-9_]*'),
        ('PLUS',      r'\+'),
        ('MINUS',     r'-'),
        ('TIMES',     r'\*'),
        ('DIVIDE',    r'/'),
        ('LPAREN',    r'\('),
        ('RPAREN',    r'\)'),
        ('SKIP',      r'[ \t]+'),
        ('MISMATCH',  r'.'),
    ]
    
    tok_regex = '|'.join(f'(?P<{pair[0]}>{pair[1]})' for pair in token_specification)
    get_token = re.compile(tok_regex).match
    line = expression.strip()
    pos = 0
    tokens = []
    
    while pos < len(line):
        match = get_token(line, pos)
        if match is None:
            raise RuntimeError(f'Erro léxico em {line[pos]}')
        pos = match.end()
        token_type = match.lastgroup
        if token_type in ('NUMBER', 'ID'):
            value = match.group(token_type)
            tokens.append((token_type, value))
        elif token_type != 'SKIP':
            tokens.append((token_type, match.group(token_type)))
    
    return tokens
```

## Análise Sintática

### Objetivo

A análise sintática, ou parsing, é a segunda etapa do processo de compilação. Seu objetivo é analisar a sequência de tokens para construir uma estrutura hierárquica, como uma árvore de análise sintática (AST), que representa a estrutura gramatical do código.

### Componentes

- **Gramática da linguagem**: Conjunto de regras que define a estrutura da linguagem.
- **Analisador léxico**: Componente que fornece a sequência de tokens.
- **Algoritmo de parsing**: Constrói a árvore de análise a partir dos tokens.

### Exemplo de Gramática

Para expressões aritméticas simples:
- Expressão → Termo {("+" | "-") Termo}
- Termo → Fator {("*" | "/") Fator}
- Fator → Número | Identificador | "(" Expressão ")"

### Implementação

```python
class Parser:
    def __init__(self, tokens):
        self.tokens = tokens
        self.pos = 0
    
    def parse(self):
        return self.expression()
    
    def expression(self):
        node = self.term()
        while self.current_token() in ('PLUS', 'MINUS'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.term())
        return node
    
    def term(self):
        node = self.factor()
        while self.current_token() in ('TIMES', 'DIVIDE'):
            token = self.current_token()
            self.next_token()
            node = (token, node, self.factor())
        return node
    
    def factor(self):
        token = self.current_token()
        if token == 'NUMBER':
            self.next_token()
            return ('NUMBER', self.current_value())
        elif token == 'ID':
            self.next_token()
            return ('ID', self.current_value())
        elif token == 'LPAREN':
            self.next_token()
            node = self.expression()
            if self.current_token() == 'RPAREN':
                self.next_token()
                return node
            else:
                raise RuntimeError("Erro: ')' esperado")
        else:
            raise RuntimeError(f"Erro: Token inesperado {token}")
    
    def current_token(self):
        return self.tokens[self.pos][0] if self.pos < len(self.tokens) else None
    
    def current_value(self):
        return self.tokens[self.pos - 1][1]
    
    def next_token(self):
        self.pos += 1

# Função principal para realizar a análise léxica e sintática
def main():
    expression = "x + 3 * ( y - 2 ) / z"
    tokens = lexical_analysis(expression)
    print("Tokens:", tokens)
    
    parser = Parser(tokens)
    ast = parser.parse()
    print("AST:", ast)

if __name__ == "__main__":
    main()
```

## Análise Semântica

### Objetivo

A análise semântica é a terceira etapa do processo de compilação. Seu objetivo é verificar a correção semântica do programa, assegurando que ele faz sentido dentro do contexto da linguagem. Isso inclui verificação de tipos, escopo de variáveis e outras regras semânticas.

### Componentes

- **Tabela de símbolos**: Armazena informações sobre identificadores, seus tipos e escopos.
- **Regras semânticas**: Definem as verificações necessárias para garantir a correção semântica do código.

### Processo

1. **Verificação de tipos**: Assegurar que as operações são realizadas entre tipos compatíveis.
2. **Resolução de identificadores**: Garantir que todas as variáveis e funções estão declaradas antes de serem usadas.
3. **Análise de escopo**: Verificar que as variáveis estão acessíveis apenas dentro do seu escopo.

### Exemplo de Verificação de Tipos

Para a expressão `x + 3`, onde `x` é uma variável do tipo `int`:

```python
class SemanticAnalyzer:
    def __init__(self, ast, symbol_table):
        self.ast = ast
        self.symbol_table = symbol_table
    
    def analyze(self):
        return self._analyze_node(self.ast)
    
    def _analyze_node(self, node):
        if isinstance(node, tuple):
            op = node[0]
            left = self._analyze_node(node[1])
            right = self._analyze_node(node[2])
            if op in ('PLUS', 'MINUS', 'TIMES', 'DIVIDE'):
                if left != 'int' or right != 'int':
                    raise RuntimeError(f"Erro semântico: operação {op} inválida entre {left} e {right}")
                return 'int'
        elif node[0] == 'NUMBER':
            return 'int'
        elif node[0] == 'ID':
            identifier = node[1]
            if identifier not in self.symbol_table:
                raise RuntimeError(f"Erro semântico: variável {identifier} não declarada")
            return self.symbol_table[identifier]
        else:
            raise RuntimeError(f"Erro semântico: nó inválido {node}")

# Função principal para realizar a análise semântica
def main():
    expression = "x + 3 * ( y - 2 ) / z"
    tokens = lexical_analysis(expression)
    print("Tokens:", tokens)
    
    parser = Parser(tokens)
    ast = parser.parse()
    print("AST:", ast)
    
    symbol_table = {'x': 'int', 'y': 'int', 'z': 'int'}
    analyzer = SemanticAnalyzer(ast, symbol_table)
    analyzer.analyze()
    print("Análise semântica concluída com sucesso")

if __name__ == "__main__":
    main()
```

## Conclusão

A análise léxica, sintática e semântica são etapas fundamentais do processo de compilação, cada uma desempenhando um papel crucial na transformação do código fonte em um programa executável. A análise léxica converte o código em tokens, a análise sintática constrói a estrutura gramatical e a análise semântica verifica a correção contextual do programa. Compreender essas etapas é essencial para o desenvolvimento de compiladores e intérpretes eficientes.