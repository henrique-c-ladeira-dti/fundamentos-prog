# Exemplos Práticos em Diferentes Linguagens

Este documento apresenta programas simples implementados em diferentes linguagens de programação, demonstrando sintaxe básica, entrada/saída e estruturas fundamentais de cada linguagem.

---

## Programa: Saudação Personalizada

Um programa simples que solicita o nome do usuário e exibe uma mensagem de saudação personalizada.

**Funcionalidade:**
1. Solicitar nome do usuário
2. Ler a entrada
3. Exibir mensagem: "Greetings, [Nome]."

---

### Python

**Características:**
- Sintaxe simples e legível
- Tipagem dinâmica
- Interpretada
- Ideal para iniciantes

**Código:**

```python
# Solicita o nome do usuário
nome = input("Digite seu nome: ")

# Exibe a saudação
print(f"Greetings, {nome}.")
```

**Execução:**

```bash
# Salvar o arquivo como saudacao.py
python saudacao.py

# Saída esperada:
# Digite seu nome: Maria
# Greetings, Maria.
```

**Explicação linha por linha:**

```python
# input() - função que lê entrada do usuário
# O texto entre parênteses é exibido como prompt
nome = input("Digite seu nome: ")

# print() - função que exibe saída no console
# f"..." - f-string permite interpolar variáveis com {}
print(f"Greetings, {nome}.")
```

**Variações do código:**

```python
# Versão mais detalhada com tratamento
nome = input("Digite seu nome: ")

if nome:  # Verifica se nome não está vazio
    print(f"Greetings, {nome}.")
else:
    print("Greetings, Stranger.")
```

```python
# Versão com função
def saudar(nome):
    return f"Greetings, {nome}."

nome = input("Digite seu nome: ")
mensagem = saudar(nome)
print(mensagem)
```

---

## Comparação: Entrada e Saída em Diferentes Linguagens

| Linguagem | Função de Entrada | Função de Saída | Dificuldade |
|-----------|-------------------|-----------------|-------------|
| Python    | `input()`         | `print()`       | Muito Baixa |
| JavaScript| `prompt()` (browser) / `readline` (Node.js) | `console.log()` | Baixa |
| Java      | `Scanner.nextLine()` | `System.out.println()` | Média |
| C         | `scanf()` / `fgets()` | `printf()` | Alta |
| Go        | `fmt.Scan()` | `fmt.Println()` | Média |

---

## Próximos Exemplos

Este documento será expandido com implementações do mesmo programa em:

- JavaScript (Node.js e Browser)
- Java
- C
- C++
- Go
- Rust
- E outras linguagens populares

Cada exemplo demonstrará as particularidades sintáticas e conceituais de cada linguagem.

---

**Documentos relacionados:**
- **[Fundamentos de Eletrônica e Programação](./introducao.md)** - Base teórica de como código é executado
- **[Interfaces de Usuário e Terminal](./interfaces-terminal.md)** - Como executar programas no terminal
