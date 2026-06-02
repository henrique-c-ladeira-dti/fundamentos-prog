# Python: Exemplos Práticos

Este capítulo apresenta exemplos práticos em Python com foco em execução real (usando `print`), comparando a sintaxe com C e JavaScript onde relevante.

---

## 1. Variáveis

Em Python, variáveis não precisam de declaração de tipo — o tipo é inferido automaticamente.

```python
# Números
idade = 25
altura = 1.75
temperatura = -3.5

# Texto
nome = "Ana"
cidade = 'São Paulo'

# Booleano
ativo = True
logado = False

# Exibindo os valores
print(idade)        # 25
print(altura)       # 1.75
print(nome)         # Ana
print(ativo)        # True
```

**Múltiplas atribuições:**

```python
x = y = z = 0
print(x, y, z)  # 0 0 0

a, b, c = 10, 20, 30
print(a, b, c)  # 10 20 30
```

**Verificando o tipo:**

```python
print(type(42))       # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type("texto"))  # <class 'str'>
print(type(True))     # <class 'bool'>
```

**Comparação de declaração de variáveis:**

| Aspecto         | Python           | JavaScript          | C                    |
| --------------- | ---------------- | ------------------- | -------------------- |
| Declaração      | `nome = "Ana"`   | `let nome = "Ana"`  | `char nome[] = "Ana"` |
| Tipo            | Automático       | Automático          | Obrigatório          |
| Reatribuição    | Qualquer tipo    | Qualquer tipo       | Mesmo tipo           |

---

## 2. Funções

Funções em Python são definidas com `def`.

```python
# Função simples sem retorno
def saudar():
    print("Olá, mundo!")

saudar()  # Olá, mundo!
```

```python
# Função com parâmetro
def saudar_pessoa(nome):
    print(f"Olá, {nome}!")

saudar_pessoa("Bruno")  # Olá, Bruno!
saudar_pessoa("Carla")  # Olá, Carla!
```

```python
# Função com retorno
def somar(a, b):
    return a + b

resultado = somar(3, 5)
print(resultado)  # 8
print(somar(10, 20))  # 30
```

```python
# Função com valor padrão no parâmetro
def saudar(nome, saudacao="Olá"):
    print(f"{saudacao}, {nome}!")

saudar("Diego")           # Olá, Diego!
saudar("Diego", "Oi")    # Oi, Diego!
```

```python
# Função com múltiplos retornos
def min_max(lista):
    return min(lista), max(lista)

minimo, maximo = min_max([4, 1, 9, 2, 7])
print(minimo)  # 1
print(maximo)  # 9
```

**Comparação de sintaxe de funções:**

```python
# Python
def somar(a, b):
    return a + b
```

```javascript
// JavaScript
function somar(a, b) {
    return a + b;
}
```

```c
// C
int somar(int a, int b) {
    return a + b;
}
```

> Em Python e JavaScript não é necessário declarar o tipo dos parâmetros nem do retorno. Em C, ambos são obrigatórios.

---

## 3. Estrutura Condicional

### `if` / `elif` / `else`

```python
nota = 7

if nota >= 9:
    print("Aprovado com distinção")
elif nota >= 6:
    print("Aprovado")
elif nota >= 4:
    print("Recuperação")
else:
    print("Reprovado")

# Saída: Aprovado
```

```python
# Condições compostas
idade = 20
tem_carteira = True

if idade >= 18 and tem_carteira:
    print("Pode dirigir")
elif idade >= 18:
    print("Maior de idade, mas sem carteira")
else:
    print("Menor de idade")

# Saída: Pode dirigir
```

```python
# Operador ternário (if em uma linha)
x = 10
resultado = "positivo" if x > 0 else "negativo ou zero"
print(resultado)  # positivo
```

**Comparação de sintaxe condicional:**

```python
# Python — usa indentação, sem chaves
if x > 0:
    print("positivo")
elif x == 0:
    print("zero")
else:
    print("negativo")
```

```javascript
// JavaScript — usa chaves {}
if (x > 0) {
    console.log("positivo");
} else if (x === 0) {
    console.log("zero");
} else {
    console.log("negativo");
}
```

```c
// C — usa chaves {}, comparação com ==
if (x > 0) {
    printf("positivo\n");
} else if (x == 0) {
    printf("zero\n");
} else {
    printf("negativo\n");
}
```

> A principal diferença do Python: **não usa chaves `{}`** — o bloco é delimitado pela **indentação**.

---

## 4. Estruturas de Repetição

### `while` — Repete enquanto a condição for verdadeira

```python
contador = 0

while contador < 5:
    print(contador)
    contador += 1

# 0
# 1
# 2
# 3
# 4
```

```python
# Acumulador com while
soma = 0
i = 1

while i <= 10:
    soma += i
    i += 1

print(soma)  # 55  (1+2+3+...+10)
```

```python
# Loop com entrada do usuário
senha = ""

while senha != "1234":
    senha = input("Digite a senha: ")
    if senha != "1234":
        print("Senha incorreta, tente novamente.")

print("Acesso liberado!")
```

```python
# Loop infinito com break
while True:
    entrada = input("Digite 'sair' para encerrar: ")
    if entrada == "sair":
        break
    print(f"Você digitou: {entrada}")

print("Programa encerrado.")
```

**Comparação de sintaxe `while`:**

```python
# Python
i = 0
while i < 5:
    print(i)
    i += 1
```

```javascript
// JavaScript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

```c
// C
int i = 0;
while (i < 5) {
    printf("%d\n", i);
    i++;
}
```

> Estrutura praticamente idêntica entre as três linguagens. As diferenças são:
> - Python: sem parênteses na condição, sem `{}`, usa indentação
> - JavaScript/C: parênteses obrigatórios na condição, blocos com `{}`
> - C: variável precisa ser declarada com tipo (`int i`)
> - C/JS: incremento com `i++`; Python usa `i += 1` (não tem `++`)

---

### `for` — Itera sobre sequências

```python
# Iterando sobre uma lista
frutas = ["maçã", "banana", "uva"]

for fruta in frutas:
    print(fruta)

# maçã
# banana
# uva
```

```python
# Iterando com range (equivalente ao for do C)
for i in range(5):
    print(i)

# 0, 1, 2, 3, 4
```

**Comparação — contar de 0 a 4:**

```python
# Python
for i in range(5):
    print(i)
```

```javascript
// JavaScript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

```c
// C
for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}
```

> O `for` do C e JavaScript é mais explícito: define **início**, **condição** e **incremento** no cabeçalho. O `for` do Python esconde esses detalhes — por isso o `while` é mais parecido com o `for` do C.

---

### `break` e `continue`

```python
# break — interrompe o loop
i = 0
while i < 10:
    if i == 5:
        break
    print(i)
    i += 1

# 0, 1, 2, 3, 4
```

```python
# continue — pula para a próxima iteração
i = 0
while i < 10:
    i += 1
    if i % 2 == 0:
        continue  # pula os pares
    print(i)

# 1, 3, 5, 7, 9
```

---

## Resumo: Diferenças de Sintaxe

| Recurso            | Python                  | JavaScript              | C                        |
| ------------------ | ----------------------- | ----------------------- | ------------------------ |
| Variável           | `x = 10`                | `let x = 10`            | `int x = 10;`            |
| Função             | `def f(a):`             | `function f(a) {`       | `int f(int a) {`         |
| Condicional        | `if x > 0:`             | `if (x > 0) {`          | `if (x > 0) {`           |
| While              | `while x < 10:`         | `while (x < 10) {`      | `while (x < 10) {`       |
| For (contador)     | `for i in range(10):`   | `for (let i=0; i<10; i++)` | `for (int i=0; i<10; i++)` |
| Blocos             | Indentação              | `{ }`                   | `{ }`                    |
| Incremento         | `i += 1`                | `i++`                   | `i++`                    |
| Fim de instrução   | Quebra de linha         | `;`                     | `;`                      |

---

**Documentos relacionados:**

- **[Exemplos Práticos em Diferentes Linguagens](./exemplos-praticos-linguagens.md)** - Programa de saudação em múltiplas linguagens
- **[Variáveis e Funções](./variaveis-funcoes.md)** - Conceitos teóricos aprofundados
