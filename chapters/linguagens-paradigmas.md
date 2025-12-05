# Linguagens e Paradigmas de Programação

Este documento apresenta os diferentes tipos de linguagens de programação, seus métodos de execução e os principais paradigmas utilizados no desenvolvimento de software.

---

## Parte I: Tipos de Linguagens por Execução

### 1.1 Linguagens Compiladas

Linguagens compiladas são transformadas diretamente em código de máquina (binário) antes da execução. O compilador traduz todo o código-fonte de uma vez, gerando um arquivo executável específico para a arquitetura do processador.

**Características:**

- **Execução rápida** - Código já está em linguagem de máquina
- **Detecta erros antes da execução** - Compilação falha se houver erros
- **Executável específico** - Precisa recompilar para diferentes plataformas
- **Sem dependências em tempo de execução** - O executável é autossuficiente

**Exemplos:**

- **C** - Linguagem de sistemas, alto desempenho
- **C++** - Extensão do C com orientação a objetos
- **Rust** - Foco em segurança de memória e concorrência
- **Go** - Simplicidade e eficiência, criada pelo Google

**Processo de compilação:**

```
Código Fonte (.c, .cpp) → Compilador → Código de Máquina (executável)
    programa.c         →    gcc     →    programa.exe
```

### 1.2 Linguagens Interpretadas

Linguagens interpretadas são executadas linha por linha por um programa chamado interpretador. Não há etapa de compilação prévia - o código-fonte é lido e executado diretamente.

**Características:**

- **Execução mais lenta** - Interpretação acontece em tempo real
- **Portabilidade alta** - Mesmo código roda em qualquer sistema com o interpretador
- **Desenvolvimento mais rápido** - Não precisa recompilar
- **Erros aparecem durante execução** - Problemas descobertos ao rodar o código

**Exemplos:**

- **Python** - Sintaxe simples, ampla utilização
- **JavaScript** - Linguagem da web, roda nos navegadores
- **Ruby** - Foco em simplicidade e produtividade
- **PHP** - Desenvolvimento web server-side

**Processo de interpretação:**

```
Código Fonte (.py, .js) → Interpretador → Execução Direta
    programa.py        →    python     →    Resultado
```

### 1.3 Linguagens Compiladas para Máquina Virtual (Bytecode)

Estas linguagens combinam características de compilação e interpretação. O código é compilado para um formato intermediário (bytecode) que é executado por uma máquina virtual.

**Características:**

- **Portabilidade** - "Write once, run anywhere"
- **Performance intermediária** - Mais rápido que interpretação pura
- **Otimização em tempo de execução** - JIT (Just-In-Time) compilation
- **Gerenciamento automático de memória** - Garbage collection

**Exemplos:**

- **Java** - Roda na JVM (Java Virtual Machine)
- **C#** - Roda no CLR (.NET Common Language Runtime)
- **Kotlin** - Também usa JVM, interoperável com Java
- **Python** (parcialmente) - Compila para bytecode (.pyc) internamente

**Processo Java:**

```
Código Fonte (.java) → Compilador → Bytecode (.class) → JVM → Execução
    Main.java       →    javac    →   Main.class     → java →  Resultado
```

**Vantagens da JVM:**

- Otimizações durante execução (JIT compiler)
- Mesmo bytecode roda em Windows, Linux, macOS
- Segurança - sandboxing e verificação de bytecode

---

## Parte II: Paradigmas de Programação

Um paradigma de programação é um estilo ou metodologia para estruturar e organizar código. Cada paradigma oferece diferentes formas de pensar sobre problemas e soluções.

### 2.1 Programação Estruturada (Procedural)

Organiza código em procedimentos ou funções que operam sobre dados. Foco em sequência, seleção (if/else) e repetição (loops).

**Características:**

- Código organizado em funções/procedimentos
- Fluxo de controle explícito (loops, condicionais)
- Dados separados das operações
- Execução sequencial e top-down

**Exemplo em C:**

```c
// Função para calcular média
float calcularMedia(float notas[], int tamanho) {
    float soma = 0;

    for (int i = 0; i < tamanho; i++) {
        soma += notas[i];
    }

    return soma / tamanho;
}

int main() {
    float notas[] = {7.5, 8.0, 9.0, 6.5};
    float media = calcularMedia(notas, 4);

    if (media >= 7.0) {
        printf("Aprovado: %.2f\n", media);
    } else {
        printf("Reprovado: %.2f\n", media);
    }

    return 0;
}
```

**Linguagens:** C, Pascal, Fortran, Go (parcialmente)

### 2.2 Programação Orientada a Objetos (OOP)

Organiza código em "objetos" que combinam dados (atributos) e comportamentos (métodos). Baseada em conceitos de classes, herança, encapsulamento e polimorfismo.

**Conceitos fundamentais:**

- **Classe** - Modelo/template para criar objetos
- **Objeto** - Instância de uma classe
- **Encapsulamento** - Dados privados, acesso controlado
- **Herança** - Classes filhas herdam características de classes pais
- **Polimorfismo** - Objetos de diferentes tipos respondem à mesma interface

**Exemplo em Java:**

```java
// Classe base
public class Animal {
    private String nome;

    public Animal(String nome) {
        this.nome = nome;
    }

    public void fazerSom() {
        System.out.println("Algum som");
    }

    public String getNome() {
        return nome;
    }
}

// Herança
public class Cachorro extends Animal {
    public Cachorro(String nome) {
        super(nome);
    }

    @Override
    public void fazerSom() {
        System.out.println(getNome() + " diz: Au au!");
    }
}

// Uso
public class Main {
    public static void main(String[] args) {
        Animal meuCachorro = new Cachorro("Rex");
        meuCachorro.fazerSom(); // Saída: Rex diz: Au au!
    }
}
```

**Linguagens:** Java, C++, C#, Python, Ruby, Kotlin

### 2.3 Programação Funcional

Trata computação como avaliação de funções matemáticas, evitando mudança de estado e dados mutáveis. Funções podem ser passadas como argumentos e retornadas.

**Características:**

- **Imutabilidade** - Dados não mudam após criação
- **Funções puras** - Mesmo input sempre gera mesmo output
- **Ausência de efeitos colaterais** - Funções não alteram estado externo
- **Composição de funções** - Combinar funções simples em complexas
- **Recursão** - Preferida sobre loops iterativos

**Exemplo em JavaScript (estilo funcional):**

```javascript
// Funções puras
const dobrar = (x) => x * 2;
const somar10 = (x) => x + 10;
const ehPar = (x) => x % 2 === 0;

// Composição e operações funcionais
const numeros = [1, 2, 3, 4, 5];

const resultado = numeros
  .map(dobrar) // [2, 4, 6, 8, 10]
  .filter(ehPar) // [2, 4, 6, 8, 10] (todos são pares)
  .map(somar10) // [12, 14, 16, 18, 20]
  .reduce((acc, val) => acc + val, 0); // 80

console.log(resultado); // 80

// Recursão ao invés de loop
const fatorial = (n) => (n <= 1 ? 1 : n * fatorial(n - 1));

console.log(fatorial(5)); // 120
```

**Exemplo em Haskell (funcional puro):**

```haskell
-- Definição de função
quadrado :: Int -> Int
quadrado x = x * x

-- Função de ordem superior
aplicarDuasVezes :: (a -> a) -> a -> a
aplicarDuasVezes f x = f (f x)

-- Uso
main = do
    print (aplicarDuasVezes quadrado 3)  -- (3²)² = 81
    print (map quadrado [1, 2, 3, 4])    -- [1, 4, 9, 16]
```

**Linguagens:** Haskell, Lisp, Clojure, Scala, F#, JavaScript (suporta)

### 2.4 Programação Declarativa vs Imperativa

**Programação Imperativa:**

- Foco em **como** fazer (passo a passo)
- Especifica sequência de instruções
- Controle explícito do fluxo

```javascript
// Imperativo - COMO fazer
const numeros = [1, 2, 3, 4, 5];
const pares = [];

for (let i = 0; i < numeros.length; i++) {
  if (numeros[i] % 2 === 0) {
    pares.push(numeros[i]);
  }
}

console.log(pares); // [2, 4]
```

**Programação Declarativa:**

- Foco em **o que** fazer (resultado desejado)
- Sistema decide como executar
- Abstração do controle de fluxo

```javascript
// Declarativo - O QUE fazer
const numeros = [1, 2, 3, 4, 5];
const pares = numeros.filter((n) => n % 2 === 0);

console.log(pares); // [2, 4]
```

**Exemplos de linguagens/tecnologias declarativas:**

- **SQL** - Consultas de banco de dados
- **HTML/CSS** - Estrutura e estilo de páginas
- **Prolog** - Lógica e inferência
- **Regular Expressions** - Padrões de texto

---

## Parte III: Linguagens Multi-Paradigma

Muitas linguagens modernas suportam múltiplos paradigmas, permitindo escolher a abordagem mais adequada para cada problema.

### 3.1 Python

**Paradigmas:** Procedural, OOP, Funcional (parcial)

```python
# Procedural
def calcular_area(raio):
    return 3.14 * raio ** 2

area = calcular_area(5)

# Orientado a Objetos
class Circulo:
    def __init__(self, raio):
        self.raio = raio

    def calcular_area(self):
        return 3.14 * self.raio ** 2

circulo = Circulo(5)
area = circulo.calcular_area()

# Funcional
raios = [1, 2, 3, 4, 5]
areas = list(map(lambda r: 3.14 * r ** 2, raios))
```

### 3.2 JavaScript

**Paradigmas:** Procedural, OOP, Funcional

```javascript
// Procedural
function saudacao(nome) {
  return `Olá, ${nome}!`;
}

// OOP (protótipos e classes)
class Pessoa {
  constructor(nome) {
    this.nome = nome;
  }

  saudar() {
    return `Olá, ${this.nome}!`;
  }
}

// Funcional
const saudar = (nome) => `Olá, ${nome}!`;
const pessoas = ["Ana", "João"];
const saudacoes = pessoas.map(saudar);
```

### 3.3 Scala

**Paradigmas:** OOP, Funcional (híbrido)

```scala
// OOP
class Pessoa(val nome: String) {
  def saudar(): String = s"Olá, $nome!"
}

// Funcional
val numeros = List(1, 2, 3, 4, 5)
val quadrados = numeros.map(x => x * x)
val soma = numeros.reduce(_ + _)

// Pattern Matching (funcional)
def descrever(x: Any): String = x match {
  case 0 => "zero"
  case n: Int if n > 0 => "positivo"
  case n: Int => "negativo"
  case _ => "outro tipo"
}
```

---

## Parte IV: Comparação e Escolha de Linguagens

### 4.1 Critérios de Escolha

**Performance:**

- **Compiladas (C, C++, Rust)** - Aplicações de sistema, jogos, sistemas embarcados
- **VM (Java, C#)** - Aplicações empresariais, Android
- **Interpretadas (Python, Ruby)** - Scripts, prototipagem rápida

**Domínio de aplicação:**

- **Web frontend** - JavaScript, TypeScript
- **Web backend** - Python, Java, Node.js, Go, PHP
- **Mobile** - Swift (iOS), Kotlin (Android), React Native (JavaScript)
- **Data Science** - Python, R, Julia
- **Sistemas operacionais** - C, C++, Rust
- **Jogos** - C++, C#, Rust

**Curva de aprendizado:**

- **Iniciantes** - Python, JavaScript
- **Intermediário** - Java, C#, Go
- **Avançado** - C++, Rust, Haskell

### 4.2 Tabela Comparativa

| Linguagem      | Tipo de Execução | Paradigma Principal | Uso Comum                 | Dificuldade |
| -------------- | ---------------- | ------------------- | ------------------------- | ----------- |
| **C**          | Compilada        | Estruturada         | Sistemas, Embarcados      | Alta        |
| **C++**        | Compilada        | OOP/Estruturada     | Jogos, Sistemas           | Alta        |
| **Java**       | Bytecode/JVM     | OOP                 | Empresarial, Android      | Média       |
| **Python**     | Interpretada     | Multi-paradigma     | Scripts, Data Science     | Baixa       |
| **JavaScript** | Interpretada     | Multi-paradigma     | Web (frontend/backend)    | Baixa       |
| **Go**         | Compilada        | Estruturada         | Servidores, Microserviços | Baixa       |
| **Rust**       | Compilada        | Multi-paradigma     | Sistemas, Performance     | Alta        |
| **C#**         | Bytecode/CLR     | OOP                 | Desktop, Jogos (Unity)    | Média       |
| **Swift**      | Compilada        | Multi-paradigma     | iOS, macOS                | Média       |
| **Kotlin**     | Bytecode/JVM     | OOP/Funcional       | Android, Backend          | Média       |
| **Haskell**    | Compilada        | Funcional Puro      | Acadêmico, Pesquisa       | Muito Alta  |
| **PHP**        | Interpretada     | OOP/Estruturada     | Web Backend               | Baixa       |

### 4.3 Exemplos Práticos por Domínio

**Aplicação Web Completa:**

```
Frontend:  JavaScript/TypeScript + React/Vue/Angular
Backend:   Python (Django/Flask) ou Node.js (Express) ou Java (Spring)
Database:  SQL (PostgreSQL) ou NoSQL (MongoDB)
```

**Aplicativo Mobile:**

```
iOS:       Swift + SwiftUI
Android:   Kotlin + Jetpack Compose
Híbrido:   JavaScript + React Native ou Flutter (Dart)
```

**Data Science:**

```
Análise:   Python (pandas, numpy, matplotlib)
ML/AI:     Python (scikit-learn, TensorFlow, PyTorch)
Big Data:  Scala (Apache Spark) ou Python (PySpark)
```

**Sistemas de Baixo Nível:**

```
Kernel:    C
Drivers:   C ou Rust
Embarcados: C ou C++
```

---

## Parte V: Conceitos Importantes

### 5.1 Tipagem

**Tipagem Estática** (tipos verificados em tempo de compilação):

- Erros de tipo detectados antes da execução
- Melhor performance - compilador pode otimizar
- Exemplos: Java, C, C++, Rust, Go

```java
// Java - Tipagem estática
int numero = 42;
String texto = "Olá";
numero = "texto"; // ERRO de compilação!
```

**Tipagem Dinâmica** (tipos verificados em tempo de execução):

- Mais flexível, desenvolvimento mais rápido
- Erros de tipo aparecem durante execução
- Exemplos: Python, JavaScript, Ruby, PHP

```python
# Python - Tipagem dinâmica
numero = 42
texto = "Olá"
numero = "agora é texto"  # OK! Tipo mudou em runtime
```

**Tipagem Forte vs Fraca:**

```python
# Python - Tipagem forte
"3" + 3  # ERRO: não converte automaticamente

# JavaScript - Tipagem fraca
"3" + 3  // "33" - converte número para string automaticamente
```

### 5.2 Gerenciamento de Memória

**Manual (C, C++):**

```c
// Programador controla alocação/liberação
int* ptr = (int*)malloc(sizeof(int));
*ptr = 42;
free(ptr);  // Obrigatório liberar memória
```

**Automático - Garbage Collection (Java, Python, JavaScript):**

```java
// Sistema gerencia automaticamente
Object obj = new Object();
// Memória liberada automaticamente quando não há mais referências
```

**Ownership (Rust):**

```rust
// Sistema de ownership - sem garbage collector
let s = String::from("olá");
// Memória liberada automaticamente ao sair do escopo
// Compilador garante segurança em tempo de compilação
```

### 5.3 Concorrência e Paralelismo

**Threads (Java, C++):**

```java
Thread t = new Thread(() -> {
    System.out.println("Executando em thread separada");
});
t.start();
```

**Async/Await (JavaScript, Python, C#):**

```javascript
async function buscarDados() {
  const response = await fetch("https://api.exemplo.com/dados");
  const data = await response.json();
  return data;
}
```

**Goroutines (Go):**

```go
go func() {
    fmt.Println("Executando em goroutine")
}()
```

---

## Conclusão

A escolha de linguagem e paradigma depende de vários fatores:

1. **Requisitos do projeto** - Performance, portabilidade, prazo
2. **Domínio de aplicação** - Web, mobile, sistemas, data science
3. **Experiência da equipe** - Curva de aprendizado
4. **Ecossistema** - Bibliotecas, frameworks, comunidade
5. **Manutenibilidade** - Facilidade de manter e evoluir o código

**Não existe linguagem "melhor"** - cada uma tem seus pontos fortes e fracos. O importante é entender os fundamentos e escolher a ferramenta adequada para cada problema.

**Recomendação para iniciantes:**

1. Comece com **Python** ou **JavaScript** (sintaxe simples, multi-paradigma)
2. Aprenda fundamentos de **programação estruturada**
3. Estude **orientação a objetos**
4. Explore **programação funcional** para expandir perspectivas
5. Experimente linguagens de diferentes paradigmas

**Documentos relacionados:**

- **[Fundamentos de Eletrônica e Programação](./introducao.md)** - Como hardware executa código
- **[Interfaces de Usuário e Terminal](./interfaces-terminal.md)** - Executando programas
- **[Controle de Versão com Git](./git-controle-versao.md)** - Gerenciando código-fonte
