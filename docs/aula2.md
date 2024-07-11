# Aula 2 -  Compilação e Interação: Do Código ao Executável 💻🔧

No fascinante mundo da programação, as linguagens de programação e as linguagens de máquina desempenham papéis fundamentais na criação de software. Embora ambas sejam invenções humanas, as linguagens de programação oferecem uma compreensão mais acessível, utilizando auxiliares mnemônicos e açúcar sintático para facilitar o processo de desenvolvimento. Por outro lado, a linguagem de máquina é representada por um arquivo binário complexo, de difícil compreensão para os programadores.

## O que é Assembly? 🤔

Assembly é uma linguagem de baixo nível que serve como uma representação legível por humanos das instruções de linguagem de máquina. Ela fornece uma abstração mais próxima do hardware, permitindo aos programadores um controle mais direto sobre o comportamento do processador. No entanto, escrever código em Assembly pode ser uma tarefa árdua e propensa a erros, especialmente em projetos de grande escala.

## Diferenças entre Compilação e Interpretação ⚖️

Existem duas abordagens principais para processar o código-fonte e executá-lo em um computador: compilação e interpretação. Vamos explorar as diferenças entre essas duas técnicas:

| Característica | Compilação | Interpretação |
|----------------|------------|---------------|
| Velocidade de execução | Rápida | Mais lenta |
| Consumo de recursos | Menor | Maior |
| Portabilidade | Específica da plataforma | Independente da plataforma |
| Detecção de erros | Durante a compilação | Durante a execução |
| Exemplo de linguagens | C, C++, Rust | Python, JavaScript, Ruby |

🔔 É importante ressaltar que o código-fonte processado por meio de interpretação oferece maior flexibilidade e facilidade no processo de programação. No entanto, essa abordagem consome uma quantidade maior de recursos computacionais e resulta em uma execução mais lenta em comparação com o código compilado. ❗

## Consumo de Energia: Rust vs. Python 🔋

Ao comparar linguagens compiladas e interpretadas, um aspecto interessante a ser considerado é o consumo de energia. Vamos analisar a diferença entre Rust, uma linguagem compilada, e Python, uma linguagem interpretada:

```
+---------------+---------------+
|   Linguagem   | Consumo de    |
|               | Energia       |
+---------------+---------------+
| Rust          | Baixo         |
+---------------+---------------+
| Python        | Alto          |
+---------------+---------------+
```

Rust, sendo uma linguagem compilada, é conhecida por sua eficiência energética. O código Rust é compilado diretamente para instruções de máquina otimizadas, resultando em um consumo de energia menor durante a execução.

Por outro lado, Python, sendo uma linguagem interpretada, requer a presença de um interpretador para executar o código. Esse processo adicional de interpretação consome mais energia em comparação com a execução direta do código compilado.

Portanto, se a eficiência energética for uma preocupação crucial para o seu projeto, optar por uma linguagem compilada como Rust pode ser uma escolha mais adequada.

## Demonstração Prática

### Tutorial: Instalação do SDK do .NET 8 e Criação de um Projeto MVC 🚀

Neste tutorial, vamos aprender como instalar o SDK do .NET 8, criar um novo projeto MVC usando o comando `dotnet new mvc` e explorar o processo de compilação. Também faremos uma modificação no código para quebrar a compilação e, em seguida, corrigiremos o código para que a compilação seja concluída com sucesso.

## Passo 1: Instalação do SDK do .NET 8 📥

Antes de começarmos, certifique-se de ter o SDK do .NET 8 instalado em seu sistema. Você pode baixar o SDK do .NET 8 a partir do site oficial da Microsoft: [Download .NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

Siga as instruções de instalação específicas para o seu sistema operacional.

## Passo 2: Criação de um Novo Projeto MVC 🆕

Abra o terminal ou prompt de comando e navegue até o diretório onde deseja criar o projeto. Em seguida, execute o seguinte comando para criar um novo projeto MVC:

```
dotnet new mvc -o MeuProjetoMVC
```

Isso criará uma nova pasta chamada "MeuProjetoMVC" contendo a estrutura básica de um projeto MVC.

## Passo 3: Compilação do Projeto ⚙️

Navegue para o diretório do projeto recém-criado:

```
cd MeuProjetoMVC
```

Em seguida, execute o seguinte comando para compilar o projeto:

```
dotnet build
```

Se tudo estiver correto, a compilação será concluída com sucesso e você verá uma mensagem semelhante a esta:

```
Build succeeded.
    0 Warning(s)
    0 Error(s)
```

## Passo 4: Quebrando a Compilação 💥

Agora, vamos fazer uma modificação no código para quebrar a compilação. Abra o arquivo `Controllers/HomeController.cs` em um editor de texto e adicione um erro de sintaxe intencional. Por exemplo, remova um ponto e vírgula (`;`) no final de uma linha.

Salve o arquivo e execute novamente o comando `dotnet build`. Desta vez, a compilação falhará e você verá uma mensagem de erro indicando o problema:

```
Build failed.
    1 Error(s)
```

A mensagem de erro fornecerá detalhes sobre o erro de sintaxe que você introduziu.

## Passo 5: Corrigindo o Código 🔧

Agora, vamos corrigir o código para que a compilação seja concluída com sucesso. Abra novamente o arquivo `Controllers/HomeController.cs` e corrija o erro de sintaxe que você introduziu anteriormente.

Salve o arquivo e execute novamente o comando `dotnet build`. Desta vez, a compilação será concluída com sucesso.

## Principais Livros de Compilação

Claro! Aqui está um resumo dos principais livros sobre compilação e compiladores, que são essenciais para quem deseja aprofundar seus conhecimentos nessa área:

## 1. **"Compilers: Principles, Techniques, and Tools" (Dragon Book)**
Autores: Alfred V. Aho, Monica S. Lam, Ravi Sethi, Jeffrey D. Ullman

### Resumo:
Conhecido como o "Dragon Book" devido à ilustração de um dragão na capa, este livro é considerado a bíblia dos compiladores. Ele cobre todos os aspectos fundamentais da construção de compiladores, incluindo análise léxica, análise sintática, análise semântica, otimização de código, geração de código e técnicas de compilação avançadas. É amplamente utilizado em cursos universitários e é uma referência essencial para qualquer pessoa interessada em compiladores.

## 2. **"Engineering a Compiler"**
Autores: Keith D. Cooper, Linda Torczon

### Resumo:
Este livro oferece uma abordagem prática e detalhada para a engenharia de compiladores. Ele aborda os princípios básicos e as técnicas avançadas de construção de compiladores, com ênfase em exemplos práticos e implementações reais. É ideal para estudantes e profissionais que desejam entender como os compiladores funcionam na prática e como aplicar esses conhecimentos em projetos reais.

## 3. **"Modern Compiler Implementation in C/Java/ML"**
Autor: Andrew W. Appel

### Resumo:
Esta série de livros, disponível em versões para C, Java e ML, fornece uma introdução prática à implementação de compiladores. Cada versão do livro é adaptada para a linguagem de programação específica, oferecendo exemplos e exercícios práticos. O livro cobre tópicos como análise léxica, análise sintática, geração de código intermediário, otimização e geração de código final. É uma excelente escolha para quem deseja aprender a implementar compiladores em uma linguagem específica.

## 4. **"Advanced Compiler Design and Implementation"**
Autor: Steven Muchnick

### Resumo:
Este livro é voltado para leitores que já possuem um conhecimento básico sobre compiladores e desejam explorar técnicas avançadas de design e implementação. Ele cobre tópicos como otimização de código, análise de dependências, paralelismo, e técnicas de compilação para arquiteturas modernas. É uma leitura essencial para quem deseja aprofundar seus conhecimentos e trabalhar em projetos de compiladores de alto desempenho.

## 5. **"The Definitive ANTLR 4 Reference"**
Autor: Terence Parr

### Resumo:
Este livro é um guia completo para o ANTLR (Another Tool for Language Recognition), uma ferramenta popular para a construção de analisadores léxicos e sintáticos. Ele fornece uma introdução prática ao uso do ANTLR, com exemplos detalhados e explicações claras. É ideal para desenvolvedores que desejam criar linguagens de domínio específico (DSLs) ou trabalhar com análise de linguagem.

## 6. **"Programming Language Pragmatics"**
Autor: Michael L. Scott

### Resumo:
Embora não seja exclusivamente sobre compiladores, este livro oferece uma visão abrangente sobre a teoria e a prática das linguagens de programação, incluindo a construção de compiladores. Ele aborda tópicos como semântica de linguagem, design de linguagem, e técnicas de implementação. É uma excelente leitura para entender o contexto mais amplo em que os compiladores operam.

# Análise Léxica: Geração de Tokens em Detalhes 🔍📄

Nesta aula, vamos explorar a análise léxica e a geração de tokens em detalhes, utilizando a linguagem de programação Python. A análise léxica é a primeira fase do processo de compilação, onde o código-fonte é dividido em unidades menores chamadas tokens.

## O que são Tokens? 🎫

Tokens são unidades básicas de um programa que possuem um significado próprio. Eles podem ser palavras-chave, identificadores, literais, operadores ou símbolos especiais. Cada token é classificado de acordo com sua categoria léxica.

## Exemplo de Código-Fonte 💻

Vou demonstrar como isso funciona com uma equação simples em C#.

Vamos considerar a seguinte equação em C#:

```csharp
int result = 3 + 5 * (2 - 8);
```

### Passos da Análise Léxica

1. **Entrada do Código-Fonte:**
   ```csharp
   int result = 3 + 5 * (2 - 8);
   ```

2. **Divisão em Tokens:**
   A análise léxica divide o código-fonte em unidades menores chamadas tokens. Cada token representa uma unidade sintática do código, como palavras-chave, identificadores, operadores, literais, etc.

3. **Tabela de Tokens:**
   Aqui está a tabela de tokens gerada a partir da equação acima:

   | Token       | Tipo            | Descrição                        |
   |-------------|-----------------|----------------------------------|
   | `int`       | Palavra-chave   | Tipo de dado inteiro             |
   | `result`    | Identificador   | Nome da variável                 |
   | `=`         | Operador        | Operador de atribuição           |
   | `3`         | Literal         | Número inteiro                   |
   | `+`         | Operador        | Operador de adição               |
   | `5`         | Literal         | Número inteiro                   |
   | `*`         | Operador        | Operador de multiplicação        |
   | `(`         | Delimitador     | Parêntese de abertura            |
   | `2`         | Literal         | Número inteiro                   |
   | `-`         | Operador        | Operador de subtração            |
   | `8`         | Literal         | Número inteiro                   |
   | `)`         | Delimitador     | Parêntese de fechamento          |
   | `;`         | Delimitador     | Ponto e vírgula (fim da instrução)|

### Explicação Detalhada

- **Palavras-chave:** São termos reservados pela linguagem de programação. No exemplo, `int` é uma palavra-chave que indica que a variável `result` é do tipo inteiro.
- **Identificadores:** São nomes dados a variáveis, funções, classes, etc. No exemplo, `result` é um identificador.
- **Operadores:** São símbolos que representam operações. No exemplo, `=`, `+`, `*`, e `-` são operadores.
- **Literais:** São valores constantes diretamente representados no código. No exemplo, `3`, `5`, `2`, e `8` são literais inteiros.
- **Delimitadores:** São caracteres que delimitam estruturas de código. No exemplo, `(`, `)`, e `;` são delimitadores.

- **Palavras-chave:** São termos reservados pela linguagem de programação. No exemplo, `int` é uma palavra-chave que indica que a variável `result` é do tipo inteiro.
- **Identificadores:** São nomes dados a variáveis, funções, classes, etc. No exemplo, `result` é um identificador.
- **Operadores:** São símbolos que representam operações. No exemplo, `=`, `+`, `*`, e `-` são operadores.
- **Literais:** São valores constantes diretamente representados no código. No exemplo, `3`, `5`, `2`, e `8` são literais inteiros.
- **Delimitadores:** São caracteres que delimitam estruturas de código. No exemplo, `(`, `)`, e `;` são delimitadores.

## Implementação do Analisador Léxico em Python 🐍

Agora, vamos implementar um analisador léxico simples em Python para gerar os tokens a partir do código-fonte acima.

```python
import re

def tokenize(code):
    # Definição das expressões regulares para cada tipo de token
    token_specs = [
        ('KEYWORD', r'if|then|else|end|print'),
        ('IDENTIFIER', r'[a-zA-Z_][a-zA-Z0-9_]*'),
        ('NUMBER', r'\d+(\.\d+)?'),
        ('OPERATOR', r'[><=!+\-*/%]'),
        ('STRING', r'".*?"'),
        ('LPAREN', r'\('),
        ('RPAREN', r'\)'),
        ('NEWLINE', r'\n'),
        ('SKIP', r'[ \t]+'),
    ]

    # Compilação das expressões regulares
    token_regex = '|'.join('(?P<%s>%s)' % pair for pair in token_specs)
    regex = re.compile(token_regex)

    # Geração dos tokens
    tokens = []
    for match in regex.finditer(code):
        token_type = match.lastgroup
        token_value = match.group(token_type)
        if token_type != 'SKIP':
            tokens.append((token_type, token_value))

    return tokens

# Código-fonte de exemplo
code = '''
if x > 10 then
    print("Hello, World!")
else
    print("x is less than or equal to 10")
end
'''

# Chamada da função de tokenização
tokens = tokenize(code)

# Impressão dos tokens gerados
for token in tokens:
    print(token)
```

Neste exemplo, utilizamos expressões regulares para definir os padrões de cada tipo de token. Em seguida, compilamos essas expressões regulares em um único padrão usando o módulo `re` do Python.

A função `tokenize` recebe o código-fonte como entrada e itera sobre as correspondências encontradas pelo padrão de expressão regular. Para cada correspondência, extraímos o tipo de token e seu valor. Ignoramos os tokens do tipo `SKIP`, que representam espaços em branco e tabulações.

Por fim, imprimimos os tokens gerados, que serão semelhantes a:

```
('KEYWORD', 'if')
('IDENTIFIER', 'x')
('OPERATOR', '>')
('NUMBER', '10')
('KEYWORD', 'then')
('KEYWORD', 'print')
('LPAREN', '(')
('STRING', '"Hello, World!"')
('RPAREN', ')')
('KEYWORD', 'else')
('KEYWORD', 'print')
('LPAREN', '(')
('STRING', '"x is less than or equal to 10"')
('RPAREN', ')')
('KEYWORD', 'end')
```

Cada token é representado por uma tupla contendo o tipo de token e seu valor correspondente.

## Vamos Brincar no Colab!

Claro! Vamos refazer o exemplo anterior e criar uma tabela de símbolos usando o pandas no Google Colab. Aqui está o código atualizado:

```python
import re
import pandas as pd

def tokenize(code):
    # Definição das expressões regulares para cada tipo de token
    token_specs = [
        ('KEYWORD', r'if|then|else|end|print'),
        ('IDENTIFIER', r'[a-zA-Z_][a-zA-Z0-9_]*'),
        ('NUMBER', r'\d+(\.\d+)?'),
        ('OPERATOR', r'[><=!+\-*/%]'),
        ('STRING', r'".*?"'),
        ('LPAREN', r'\('),
        ('RPAREN', r'\)'),
        ('NEWLINE', r'\n'),
        ('SKIP', r'[ \t]+'),
    ]

    # Compilação das expressões regulares
    token_regex = '|'.join('(?P<%s>%s)' % pair for pair in token_specs)
    regex = re.compile(token_regex)

    # Geração dos tokens
    tokens = []
    for match in regex.finditer(code):
        token_type = match.lastgroup
        token_value = match.group(token_type)
        if token_type != 'SKIP':
            tokens.append((token_type, token_value))

    return tokens

# Código-fonte de exemplo
code = '''
if x > 10 then
    print("Hello, World!")
else
    print("x is less than or equal to 10")
end
'''

# Chamada da função de tokenização
tokens = tokenize(code)

# Criação da tabela de símbolos usando o pandas
symbol_table = pd.DataFrame(tokens, columns=['Token Type', 'Token Value'])

# Impressão da tabela de símbolos
print("Tabela de Símbolos:")
print(symbol_table)
```

Neste exemplo atualizado, utilizamos o pandas para criar uma tabela de símbolos a partir dos tokens gerados. Após chamar a função `tokenize` com o código-fonte de exemplo, criamos um DataFrame do pandas chamado `symbol_table` usando os tokens como dados e especificando as colunas como "Token Type" e "Token Value".

Por fim, imprimimos a tabela de símbolos usando o método `print`.

Ao executar este código no Google Colab, você verá a seguinte saída:

```
Tabela de Símbolos:
   Token Type            Token Value
0     KEYWORD                     if
1  IDENTIFIER                      x
2    OPERATOR                      >
3      NUMBER                     10
4     KEYWORD                   then
5     KEYWORD                  print
6      LPAREN                      (
7      STRING        "Hello, World!"
8      RPAREN                      )
9     KEYWORD                   else
10    KEYWORD                  print
11     LPAREN                      (
12     STRING  "x is less than or equal to 10"
13     RPAREN                      )
14    KEYWORD                    end
```

A tabela de símbolos exibe cada token encontrado no código-fonte, juntamente com seu tipo de token correspondente.

## Conclusão 🎉

Compilação e interpretação são duas abordagens distintas para processar o código-fonte e executá-lo em um computador. Enquanto a compilação oferece maior velocidade de execução e menor consumo de recursos, a interpretação proporciona maior flexibilidade e portabilidade. A escolha entre essas abordagens depende dos requisitos específicos do projeto, levando em consideração fatores como desempenho, consumo de energia e facilidade de desenvolvimento.

Ao compreender as diferenças entre compilação e interpretação, os programadores podem tomar decisões informadas sobre qual abordagem adotar para seus projetos, buscando o equilíbrio ideal entre eficiência e produtividade. 🚀


## Indicação de Livros:

![image](https://www.casadocodigo.com.br/cdn/shop/products/ProgramacaoFuncionaleConcorrenteemRust_ebook_large.jpg?v=1631652169)

Link: [Programação Funcional e Concorrente em Rust](https://www.casadocodigo.com.br/products/livro-rust-funcional-concorrente)

![image](https://www.casadocodigo.com.br/cdn/shop/products/ASP.NETCoreMVC__Amazon_large.jpg?v=1631571623)

Link: [ASP.NET Core MVC](https://www.casadocodigo.com.br/products/livro-aspnet-core-mvc)