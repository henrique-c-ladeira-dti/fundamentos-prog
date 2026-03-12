# Variáveis e Funções

Este documento apresenta os conceitos fundamentais de variáveis e funções na programação, elementos essenciais para armazenar dados e organizar código de forma reutilizável.

---

## Parte I: Variáveis

### 1.1 O Conceito de Variável

Uma **variável** é um espaço nomeado na memória do computador usado para armazenar dados que podem ser acessados e modificados durante a execução de um programa. Podemos pensar em uma variável como uma "caixa rotulada" onde guardamos informações temporariamente.

**Componentes de uma variável:**

- **Nome (identificador)** → Rótulo usado para referenciar a variável no código
- **Tipo** → Define que tipo de dado pode ser armazenado (número, texto, booleano, etc.)
- **Valor** → O dado propriamente dito armazenado na memória
- **Endereço de memória** → Localização física na RAM onde o valor está armazenado

**Analogia prática:**

Imagine um armário com gavetas etiquetadas:

- O nome da etiqueta = nome da variável
- O tipo de objeto que pode guardar = tipo da variável
- O objeto dentro da gaveta = valor da variável
- A posição da gaveta no armário = endereço de memória

### 1.2 Declaração e Inicialização

A **declaração** de uma variável é o ato de criar a variável, informando ao compilador/interpretador que um espaço de memória precisa ser reservado. A **inicialização** é o ato de atribuir um valor inicial à variável.

**Formas de declaração:**

```
# Python (tipagem dinâmica - tipo inferido automaticamente)
idade = 25                    # Declaração + inicialização
nome = "Maria"
ativo = True

# JavaScript (tipagem dinâmica)
let idade = 25;               # Variável mutável
const PI = 3.14159;          # Constante (imutável)
var altura = 1.75;           # Forma antiga (escopo diferente)

# C (tipagem estática - tipo deve ser declarado)
int idade = 25;              # Declara como inteiro e inicializa
float altura = 1.75;         # Declara como ponto flutuante
char inicial = 'M';          # Declara como caractere

# Java (tipagem estática)
int idade = 25;
String nome = "Maria";
boolean ativo = true;
```

### 1.3 Tipos de Dados Primitivos

Os tipos de dados primitivos são os tipos básicos fornecidos pela linguagem de programação.

**Tipos numéricos:**

- **int/integer** → Números inteiros (sem decimais)
  - Exemplo: `-10, 0, 42, 1000`
- **float/double** → Números de ponto flutuante (com decimais)
  - Exemplo: `3.14, -0.5, 2.71828`

**Tipos textuais:**

- **char** → Um único caractere
  - Exemplo: `'A', 'z', '7', '@'`
- **string** → Cadeia de caracteres (texto)
  - Exemplo: `"Olá Mundo", "Python", "123"`

**Tipo lógico:**

- **boolean/bool** → Valor verdadeiro ou falso
  - Exemplo: `true, false`

### 1.4 Escopo de Variáveis

O **escopo** define onde uma variável pode ser acessada no código. Compreender escopo é fundamental para evitar erros e escrever código organizado.

**Tipos de escopo:**

**1. Escopo Global:**

Variáveis declaradas fora de funções, acessíveis em todo o programa.

```python
# Python
mensagem = "Olá Mundo"  # Variável global

def exibir():
    print(mensagem)      # Acessa variável global

exibir()  # Saída: Olá Mundo
```

**2. Escopo Local:**

Variáveis declaradas dentro de funções, acessíveis apenas dentro daquela função.

```python
# Python
def calcular():
    resultado = 10 + 5   # Variável local
    return resultado

print(calcular())        # Saída: 15
# print(resultado)       # ERRO: resultado não existe fora da função
```

**3. Escopo de Bloco:**

Em algumas linguagens, variáveis existem apenas dentro de blocos específicos (if, for, while).

```javascript
// JavaScript
if (true) {
  let mensagem = "Dentro do bloco";
  console.log(mensagem); // Funciona
}
// console.log(mensagem);   // ERRO: mensagem não existe fora do bloco
```

### 1.5 Nomenclatura de Variáveis

Seguir convenções de nomenclatura torna o código mais legível e profissional.

**Regras gerais:**

- Usar nomes descritivos: `idade_usuario` em vez de `x`
- Começar com letra ou underscore: `_contador`, `total`
- Não usar palavras reservadas: `if`, `while`, `for`
- Evitar caracteres especiais (exceto underscore)

**Convenções por linguagem:**

```
# Python - snake_case
primeiro_nome = "João"
idade_usuario = 30
valor_total = 100.50

# JavaScript/Java - camelCase
primeiroNome = "João";
idadeUsuario = 30;
valorTotal = 100.50;

# C++ - snake_case ou camelCase
int primeiro_nome;    // snake_case
int primeiroNome;     // camelCase

# Constantes - UPPERCASE
const PI = 3.14159;
MAX_TENTATIVAS = 5;
```

---

## Parte II: Funções

### 2.1 O Conceito de Função

Uma **função** é um bloco de código reutilizável que realiza uma tarefa específica. Funções permitem organizar o código, evitar repetição e facilitar manutenção.

**Analogia prática:**

Pense em uma função como uma "máquina" que:

- Recebe **entradas** (parâmetros/argumentos)
- Processa essas entradas (executa código)
- Produz uma **saída** (retorno)

Exemplo: Uma máquina de suco que recebe frutas (entrada), processa-as (mistura) e produz suco (saída).

**Vantagens de usar funções:**

- **Reutilização** → Escrever código uma vez, usar várias vezes
- **Organização** → Dividir problemas complexos em partes menores
- **Manutenção** → Alterar código em um único lugar
- **Legibilidade** → Código mais fácil de entender
- **Testabilidade** → Testar partes específicas do programa

### 2.2 Anatomia de uma Função

```python
# Python
def calcular_area(base, altura):    # Cabeçalho da função
    """
    Calcula a área de um retângulo.

    Parâmetros:
        base (float): Base do retângulo
        altura (float): Altura do retângulo

    Retorna:
        float: Área calculada
    """
    area = base * altura            # Corpo da função
    return area                     # Retorno
```

**Componentes:**

1. **Palavra-chave de definição** → `def` (Python), `function` (JS), tipo de retorno (C/Java)
2. **Nome da função** → Identificador que usamos para chamá-la
3. **Parâmetros** → Valores de entrada entre parênteses (podem ser zero ou mais)
4. **Corpo** → Bloco de código que executa a tarefa
5. **Retorno** → Valor devolvido pela função (opcional em algumas linguagens)

### 2.3 Declaração de Funções em Diferentes Linguagens

**Python:**

```python
def somar(a, b):
    return a + b

resultado = somar(5, 3)  # resultado = 8
```

**JavaScript:**

```javascript
// Declaração tradicional
function somar(a, b) {
  return a + b;
}

// Arrow function (ES6+)
const somar = (a, b) => a + b;

let resultado = somar(5, 3); // resultado = 8
```

**C:**

```c
// Declaração antes do main
int somar(int a, int b) {
    return a + b;
}

int main() {
    int resultado = somar(5, 3);  // resultado = 8
    return 0;
}
```

**Java:**

```java
public class Calculadora {
    public static int somar(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        int resultado = somar(5, 3);  // resultado = 8
    }
}
```

### 2.4 Parâmetros e Argumentos

**Parâmetros** são variáveis declaradas na definição da função. **Argumentos** são os valores reais passados quando a função é chamada.

```python
# Python
def apresentar(nome, idade):    # 'nome' e 'idade' são PARÂMETROS
    print(f"{nome} tem {idade} anos")

apresentar("Maria", 25)         # "Maria" e 25 são ARGUMENTOS
```

**Tipos de passagem:**

**1. Parâmetros posicionais:**

```python
def dividir(dividendo, divisor):
    return dividendo / divisor

resultado = dividir(10, 2)      # 10/2 = 5.0
resultado = dividir(2, 10)      # 2/10 = 0.2  (ordem importa!)
```

**2. Parâmetros nomeados:**

```python
def criar_perfil(nome, idade, cidade):
    return f"{nome}, {idade} anos, de {cidade}"

# Passagem nomeada (ordem não importa)
perfil = criar_perfil(idade=30, cidade="São Paulo", nome="João")
```

**3. Parâmetros com valor padrão:**

```python
def saudar(nome, saudacao="Olá"):
    return f"{saudacao}, {nome}!"

print(saudar("Maria"))              # Saída: Olá, Maria!
print(saudar("João", "Bem-vindo"))  # Saída: Bem-vindo, João!
```

**4. Número variável de argumentos:**

```python
# Python - *args
def somar_varios(*numeros):
    return sum(numeros)

print(somar_varios(1, 2, 3))        # Saída: 6
print(somar_varios(10, 20, 30, 40)) # Saída: 100

# Python - **kwargs (argumentos nomeados)
def exibir_info(**dados):
    for chave, valor in dados.items():
        print(f"{chave}: {valor}")

exibir_info(nome="Ana", idade=28, cidade="Rio")
# Saída:
# nome: Ana
# idade: 28
# cidade: Rio
```

### 2.5 Retorno de Funções

O comando `return` encerra a execução da função e devolve um valor para quem a chamou.

**Função com retorno:**

```python
def calcular_quadrado(numero):
    return numero ** 2

resultado = calcular_quadrado(5)  # resultado = 25
```

**Função sem retorno (procedimento):**

```python
def exibir_mensagem(texto):
    print(texto)
    # Não há return - retorna None implicitamente

exibir_mensagem("Olá!")  # Apenas exibe, não retorna valor
```

**Retorno múltiplo (Python):**

```python
def calcular_operacoes(a, b):
    soma = a + b
    subtracao = a - b
    multiplicacao = a * b
    return soma, subtracao, multiplicacao

s, sub, mult = calcular_operacoes(10, 5)
# s = 15, sub = 5, mult = 50
```

**Retorno antecipado:**

```python
def verificar_idade(idade):
    if idade < 0:
        return "Idade inválida"  # Retorna imediatamente
    if idade < 18:
        return "Menor de idade"
    return "Maior de idade"      # Só executa se nenhum return anterior foi acionado
```

### 2.6 Funções como Objetos de Primeira Classe

Em linguagens como Python e JavaScript, funções são "cidadãos de primeira classe", ou seja, podem ser:

- Atribuídas a variáveis
- Passadas como argumentos para outras funções
- Retornadas por outras funções

**Atribuição a variáveis:**

```python
def saudar(nome):
    return f"Olá, {nome}!"

# Atribuir função a uma variável
cumprimentar = saudar

print(cumprimentar("Carlos"))  # Saída: Olá, Carlos!
```

**Função como argumento:**

```python
def executar_operacao(funcao, valor):
    return funcao(valor)

def dobrar(x):
    return x * 2

def triplicar(x):
    return x * 3

print(executar_operacao(dobrar, 5))     # Saída: 10
print(executar_operacao(triplicar, 5))  # Saída: 15
```

**Função retornando função:**

```python
def criar_multiplicador(fator):
    def multiplicar(x):
        return x * fator
    return multiplicar

vezes_dois = criar_multiplicador(2)
vezes_tres = criar_multiplicador(3)

print(vezes_dois(10))   # Saída: 20
print(vezes_tres(10))   # Saída: 30
```

### 2.7 Recursão

**Recursão** ocorre quando uma função chama a si mesma. É uma técnica poderosa para resolver problemas que podem ser divididos em subproblemas semelhantes.

**Estrutura básica:**

```python
def funcao_recursiva(parametro):
    # Caso base: condição de parada
    if condicao_de_parada:
        return valor_base

    # Caso recursivo: função chama a si mesma
    return funcao_recursiva(novo_parametro)
```

**Exemplo: Fatorial**

```python
def fatorial(n):
    # Caso base
    if n == 0 or n == 1:
        return 1

    # Caso recursivo
    return n * fatorial(n - 1)

print(fatorial(5))  # 5! = 5 × 4 × 3 × 2 × 1 = 120
```

**Como funciona:**

```
fatorial(5)
→ 5 × fatorial(4)
→ 5 × (4 × fatorial(3))
→ 5 × (4 × (3 × fatorial(2)))
→ 5 × (4 × (3 × (2 × fatorial(1))))
→ 5 × (4 × (3 × (2 × 1)))
→ 5 × (4 × (3 × 2))
→ 5 × (4 × 6)
→ 5 × 24
→ 120
```

**Exemplo: Sequência de Fibonacci**

```python
def fibonacci(n):
    # Casos base
    if n <= 1:
        return n

    # Caso recursivo
    return fibonacci(n - 1) + fibonacci(n - 2)

# Primeiros 7 números da sequência
for i in range(7):
    print(fibonacci(i), end=" ")
# Saída: 0 1 1 2 3 5 8
```

**Cuidados com recursão:**

- Sempre definir um caso base (condição de parada)
- Garantir que o problema diminui a cada chamada
- Evitar recursão muito profunda (pode estourar a pilha de chamadas)

---

## Parte III: Boas Práticas

### 3.1 Princípios de Funções Eficientes

**1. Princípio da Responsabilidade Única:**

Cada função deve fazer **uma coisa** e fazê-la bem.

```python
# ❌ Ruim - faz muitas coisas
def processar_usuario(nome, idade, email):
    validar_email(email)
    salvar_no_banco(nome, idade, email)
    enviar_email_boas_vindas(email)
    gerar_relatorio(nome)

# ✅ Bom - funções separadas
def validar_dados(email):
    return validar_email(email)

def salvar_usuario(nome, idade, email):
    salvar_no_banco(nome, idade, email)

def enviar_boas_vindas(email):
    enviar_email_boas_vindas(email)
```

**2. Funções Devem Ser Pequenas:**

Idealmente, uma função deve caber na tela sem rolagem.

**3. Nomes Descritivos:**

O nome da função deve indicar claramente o que ela faz.

```python
# ❌ Ruim
def proc(d):
    return d * 2

# ✅ Bom
def dobrar_valor(numero):
    return numero * 2
```

**4. Evitar Efeitos Colaterais:**

Funções não devem modificar variáveis globais inesperadamente.

```python
# ❌ Ruim - modifica variável global
contador = 0

def incrementar():
    global contador
    contador += 1

# ✅ Bom - retorna valor sem efeito colateral
def incrementar(valor):
    return valor + 1

contador = incrementar(contador)
```

### 3.2 Comentários e Documentação

Documente funções complexas para facilitar compreensão e manutenção.

**Python - Docstrings:**

```python
def calcular_imc(peso, altura):
    """
    Calcula o Índice de Massa Corporal (IMC).

    Args:
        peso (float): Peso em quilogramas
        altura (float): Altura em metros

    Returns:
        float: Valor do IMC calculado

    Example:
        >>> calcular_imc(70, 1.75)
        22.86
    """
    return peso / (altura ** 2)
```

**JavaScript - JSDoc:**

```javascript
/**
 * Calcula o Índice de Massa Corporal (IMC)
 * @param {number} peso - Peso em quilogramas
 * @param {number} altura - Altura em metros
 * @returns {number} Valor do IMC calculado
 */
function calcularIMC(peso, altura) {
  return peso / altura ** 2;
}
```

---

## Resumo

**Variáveis:**

- Espaços nomeados na memória para armazenar dados
- Possuem nome, tipo, valor e endereço de memória
- O escopo define onde podem ser acessadas
- Devem ter nomes descritivos seguindo convenções

**Funções:**

- Blocos reutilizáveis de código
- Recebem parâmetros e podem retornar valores
- Organizam código e evitam repetição
- Devem ter responsabilidade única e nomes claros
- Podem ser recursivas (chamar a si mesmas)

Dominar variáveis e funções é fundamental para escrever código eficiente, organizado e manutenível em qualquer linguagem de programação.
