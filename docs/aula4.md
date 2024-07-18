# Análise Semântica em Compiladores

## Objetivos da Aula
1. Entender o que é a análise semântica no contexto de compiladores.
2. Aprender as principais tarefas realizadas durante a análise semântica.
3. Realizar uma atividade prática utilizando Python para implementar verificações semânticas.

## Introdução à Análise Semântica

### O que é Análise Semântica?
A análise semântica é uma fase crucial do processo de compilação que ocorre após a análise léxica e sintática. Enquanto a análise léxica trata da identificação de tokens e a análise sintática verifica a estrutura gramatical do código-fonte, a análise semântica assegura que o código esteja conforme as regras semânticas da linguagem de programação. Esta fase verifica a correta utilização de tipos de variáveis, a resolução de referências a variáveis e funções, e outros aspectos semânticos do código.

### Principais Tarefas da Análise Semântica
- **Verificação de Tipos:** Assegura que operações e atribuições entre variáveis são feitas com tipos compatíveis.
- **Resolução de Identificadores:** Garante que todas as variáveis e funções referenciadas estão devidamente declaradas.
- **Verificação de Escopo:** Confirma que variáveis e funções são acessadas dentro de seus escopos válidos.
- **Detecção de Erros Semânticos:** Identifica problemas como o uso de variáveis não inicializadas, funções chamadas com parâmetros incorretos, etc.

## Exemplo Prático com Python

### Atividade: Implementação de Verificações Semânticas

Vamos implementar um simples analisador semântico em Python que verifica declarações de variáveis e compatibilidade de tipos em um mini-linguagem de programação fictícia.

### Passo 1: Definir a Gramática e a Tabela de Símbolos

#### Código de Exemplo
```python
# Definindo a Tabela de Símbolos
symbol_table = {}

# Função para adicionar uma variável à tabela de símbolos
def declare_variable(name, var_type):
    if name in symbol_table:
        raise Exception(f"Erro: Variável '{name}' já declarada.")
    symbol_table[name] = var_type

# Função para verificar o tipo de uma variável
def check_variable(name):
    if name not in symbol_table:
        raise Exception(f"Erro: Variável '{name}' não declarada.")
    return symbol_table[name]

# Função para verificar a atribuição de tipos
def assign_variable(name, value, value_type):
    var_type = check_variable(name)
    if var_type != value_type:
        raise Exception(f"Erro: Tipo incompatível. '{name}' é do tipo '{var_type}' mas foi atribuído um valor do tipo '{value_type}'.")

# Função para imprimir a tabela de símbolos (para depuração)
def print_symbol_table():
    print("Tabela de Símbolos:")
    for name, var_type in symbol_table.items():
        print(f"{name}: {var_type}")

# Exemplo de uso das funções
try:
    declare_variable("x", "int")
    declare_variable("y", "float")
    assign_variable("x", 10, "int")
    assign_variable("y", 3.14, "float")
    print_symbol_table()
except Exception as e:
    print(e)
```

### Explicação do Código
1. **Tabela de Símbolos:** Um dicionário que armazena os nomes das variáveis e seus respectivos tipos.
2. **Funções de Declaração e Verificação:** `declare_variable` adiciona uma variável à tabela de símbolos, `check_variable` verifica se uma variável foi declarada, e `assign_variable` verifica a compatibilidade de tipos na atribuição de valores.
3. **Teste das Funções:** Declaramos duas variáveis (`x` e `y`), atribuimos valores compatíveis a elas, e imprimimos a tabela de símbolos.

### Passo 2: Verificações Adicionais
Podemos estender este exemplo para incluir verificações mais complexas, como:
- **Verificação de Funções:** Assegurar que as funções sejam chamadas com os parâmetros corretos.
- **Escopo de Variáveis:** Implementar uma pilha de escopos para lidar com variáveis locais e globais.

### Exercício para os Alunos
1. **Adicionar Suporte para Funções:** Implementar a declaração e verificação de funções, assegurando que as chamadas de função utilizem o número correto de parâmetros com os tipos esperados.
2. **Implementar Escopos:** Modificar a tabela de símbolos para suportar escopos aninhados e garantir que variáveis locais não interfiram com variáveis globais.

### Conclusão
A análise semântica é uma etapa essencial para garantir que o código-fonte seja válido em termos de regras semânticas da linguagem de programação. Compreender e implementar estas verificações ajuda a detectar erros antes da geração do código de máquina, melhorando a confiabilidade e a correção dos programas compilados.

### Referências
- **Livro:** "Compiladores: Princípios, Técnicas e Ferramentas" de Aho, Lam, Sethi, e Ullman.
- **Documentação Python:** [https://docs.python.org/3/](https://docs.python.org/3/)

---

# Resumão do Módulo

## Pontos Principais

### Análise Léxica
- **Descrição:** Primeira fase do processo de compilação, responsável por dividir o código-fonte em unidades significativas chamadas tokens. Esses tokens incluem palavras-chave, identificadores, números, e símbolos.
- **Importância:** Facilita a análise subsequente do código, preparando-o para as fases de análise sintática e semântica.

### Análise Sintática
- **Descrição:** Verifica se a estrutura gramatical do código-fonte segue as regras da linguagem de programação. Constrói uma árvore de derivação que representa a estrutura do código.
- **Importância:** Garante que o código esteja sintaticamente correto antes de passar para a análise semântica.

### Análise Semântica
- **Descrição:** Garante que o código-fonte obedeça às regras semânticas da linguagem, como a correta utilização de tipos de variáveis e a resolução de referências a variáveis e funções.
- **Importância:** Detecta e relata erros semânticos, assegurando que o código tenha significado correto e coerência.

### Otimização de Código
- **Descrição:** Processo que melhora o desempenho do código gerado pelo compilador, reorganizando instruções para reduzir operações redundantes e aumentar a eficiência.
- **Importância:** Produz código mais eficiente, que executa mais rapidamente e utiliza menos recursos.

### Compilador
- **Descrição:** Ferramenta de software que traduz código de alto nível (como C++ ou Java) em código de máquina ou outra forma de código intermediário.
- **Importância:** Permite a execução de programas escritos em linguagens de alto nível em computadores, traduzindo-os para um formato compreensível pelo hardware.

### Tabela de Símbolos e Gramática
- **Descrição:** Utilizadas pelo analisador semântico para processar a árvore de derivação. A tabela de símbolos mantém informações sobre variáveis, funções, e outros elementos do código.
- **Importância:** Facilita a verificação semântica e a correção de erros relacionados ao uso de variáveis e funções no código.

### Linguagem Pascal
- **Descrição:** Linguagem de programação apresentada em 1970 por Niklaus Emil Wirth, que segue os paradigmas estruturado, imperativo e procedural. Um exemplo típico é um programa que recebe dois números diferentes e determina o maior.
- **Importância:** Pascal é usada para ilustrar conceitos de programação estruturada e a importância da verificação de tipos e escopos em compiladores.

### Análise de Tipos de Dados
- **Descrição:** Verificação realizada pelo analisador semântico para assegurar que operandos e operadores são compatíveis, evitando atribuições inconsistentes.
- **Importância:** Essencial para manter a integridade e coerência dos dados no código, prevenindo erros de execução.

### Funções do Analisador Semântico
- **Descrição:** Detecta variáveis declaradas mas não utilizadas, funções declaradas em duplicidade e previne o uso de nomes de funções por variáveis.
- **Importância:** Ajuda a manter o código organizado e livre de erros que possam afetar sua execução e manutenção.

