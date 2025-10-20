# Fundamentos de Eletrônica e Programação

Este documento apresenta os conceitos fundamentais que conectam a eletrônica física com a programação de computadores, formando a base para entender como funcionam os sistemas digitais modernos.

---

## Parte I: Fundamentos da Eletrônica

### 1.1 Elétrica vs Eletrônica

#### **Elétrica**

A área elétrica foca no **transporte e distribuição de energia**. É a "infraestrutura" que leva energia até onde será usada de forma segura e eficiente.

**Componentes principais:**

<div align="center">
<img src="../images/res-cap-ind.png" alt="Componentes elétricos básicos" width="350">
</div>

- **Resistor** → Limita a passagem da corrente elétrica
- **Capacitor** → Armazena energia elétrica temporariamente
- **Indutor** → Cria campos magnéticos e armazena energia

#### **Eletrônica**

A eletrônica vai além do transporte de energia: **processa sinais e informações**. Permite criar sistemas inteligentes como computadores, smartphones e controladores industriais.

**Componentes principais:**

<div align="center">
<img src="../images/dio-trans.png" alt="Componentes eletrônicos básicos" width="350">
</div>

- **Diodo** → "Válvula" que permite corrente em apenas um sentido
- **Transistor** → Amplifica sinais ou funciona como chave digital

### 1.2 O Papel dos Semicondutores

Os **semicondutores** são materiais com propriedades intermediárias entre condutores e isolantes, permitindo controle preciso do fluxo de elétrons.

**Evolução histórica:**

- **Segunda Guerra Mundial** → Avanços na purificação do germânio
- **Anos 1950+** → Silício se torna preferido (abundante, barato, suporta altas temperaturas)
- **Circuitos integrados** → Milhões/bilhões de transistores em chips pequenos

> **Resultado:** Dispositivos eletrônicos cada vez menores, mais rápidos e eficientes

---

## Parte II: Sistemas Numéricos e Representação Digital

### 2.1 Por que Diferentes Sistemas Numéricos?

O sistema **decimal** (base 10) é familiar por termos 10 dedos, mas na eletrônica outros sistemas são fundamentais:

| Sistema         | Base | Dígitos  | Uso Principal                                |
| --------------- | ---- | -------- | -------------------------------------------- |
| **Decimal**     | 10   | 0-9      | Uso humano cotidiano                         |
| **Binário**     | 2    | 0,1      | "Idioma" dos computadores (ligado/desligado) |
| **Hexadecimal** | 16   | 0-9, A-F | Representação compacta de valores binários   |

### 2.2 Conversões e Padrões

**Relação especial:** 4 bits = 1 dígito hexadecimal (porque 2⁴ = 16)

**[Tabela completa de conversão (0-255)](./tabela-conversao-sistemas.md)**

**Exemplo prático:**

```
Binário: 101110
Separar em grupos de 4: 0010 1110
Hexadecimal: 2E
Notação em programação: 0b00101110 = 0x2E
```

> **Nota:** Conversões binário ↔ hexadecimal são diretas, mas binário ↔ decimal não (10 não é potência de 2)---

## Parte III: Sistemas Digitais

### 3.1 Analógico vs Digital

| Característica | **Analógico**                 | **Digital**               |
| -------------- | ----------------------------- | ------------------------- |
| **Sinais**     | Contínuos (infinitos valores) | Discretos (0 e 1)         |
| **Ruído**      | Sensível a interferências     | Resistente a ruído        |
| **Exemplo**    | Microfone tradicional         | Processador de computador |
| **Vantagem**   | Representação natural         | Confiabilidade e precisão |

> **Por que digital venceu?** Pequenas interferências não afetam o resultado - basta identificar se está mais próximo de 0 ou 1.

### 3.2 Sincronização em Sistemas Digitais

#### **Sistemas Síncronos**

- Funcionam com relógio central (clock)
- Todas operações em tempos determinados
- Componentes "no mesmo passo"
- Evita erros de comunicação
- Projeto mais simples

#### **Sistemas Assíncronos**

- Sem clock central
- Operações quando sinais estão prontos
- Podem ser mais rápidos
- Difíceis de projetar e depurar
- Partes operam em tempos diferentes

---

## Parte IV: Lógica Digital e Processamento

### 4.1 Portas Lógicas - Os Blocos Básicos

As **portas lógicas** são os blocos fundamentais que processam sinais digitais (0 e 1). Construídas com transistores, funcionam como chaves eletrônicas inteligentes.

#### **Portas Básicas**

| Porta    | Símbolo | Função       | Saída = 1 quando...            |
| -------- | ------- | ------------ | ------------------------------ |
| **AND**  | &       | E lógico     | **Todas** entradas = 1         |
| **OR**   | \|      | OU lógico    | **Pelo menos uma** entrada = 1 |
| **NOT**  | ~       | Negação      | Entrada = 0 (inverte)          |
| **XOR**  | ⊕       | OU exclusivo | **Apenas uma** entrada = 1     |
| **NAND** | ~&      | AND negado   | **Nem todas** entradas = 1     |
| **NOR**  | ~\|     | OR negado    | **Nenhuma** entrada = 1        |

### 4.2 Computadores: Digital vs Analógico

#### **Computadores Digitais** (Padrão atual)

- Processamento binário (0 e 1)
- Imune a pequenos ruídos
- Programação flexível
- Armazenamento confiável

#### **Computadores Analógicos** (Histórico)

- Sinais contínuos
- Usados em cálculos científicos
- Sensíveis a ruído
- Menos flexíveis

### 4.3 Aritmética com Portas Lógicas

#### **Somador de 1 Bit (Half Adder)**

| A   | B   | **Soma (XOR)** | **Carry (AND)** |
| --- | --- | -------------- | --------------- |
| 0   | 0   | 0              | 0               |
| 0   | 1   | 1              | 0               |
| 1   | 0   | 1              | 0               |
| 1   | 1   | 0              | 1               |

**Exemplo:** 1 + 1 = 10 (binário)

- Soma = 0, Carry = 1 → Resultado = 10₂

> **Conceito-chave:** Operações matemáticas complexas são construídas combinando portas lógicas simples.

### 4.4 Arquitetura Básica: A ALU

A **ALU (Arithmetic Logic Unit)** é o "cérebro matemático" do processador.

<div align="center">
<img src="../images/alu.png" alt="Diagrama simplificado da ALU" width="400">
</div>

**Componentes:**

- **Entradas A e B** → Valores para processar
- **Seletor de operação** → Define qual operação executar
- **Saída** → Resultado da operação
- **Flags de status** → Informações adicionais (carry, overflow, etc.)

> **Na prática:** Quando você escreve `ADD A, B` em assembly, isso controla os sinais que dizem à ALU qual operação fazer.

---

## Parte V: Software e Sistemas Operacionais

### 5.1 Níveis de Abstração

#### **Evolução da Complexidade**

```
Hardware Puro → Microcontrolador → Console Simples → PC Moderno
     ↓               ↓                ↓              ↓
Controle direto → Código firmware → OS básico → OS completo
```

### 5.2 Compilação e Execução

#### **Sem Sistema Operacional**

- Exemplo: Microcontroladores, videogames antigos
- Código fala diretamente com hardware
- Controle total, mas responsabilidade total

#### **Com Sistema Operacional Simples**

- Exemplo: PlayStation 1, Super Nintendo
- Rotinas básicas para gráficos/som
- Alguma abstração, ainda próximo ao hardware

#### **Com Sistema Operacional Completo**

- Exemplo: Windows, Linux, macOS, PlayStation 5
- Camada robusta entre programa e hardware
- Drivers mediam acesso aos dispositivos
- Multitarefa, segurança, compatibilidade

### 5.3 Drivers e Hardware

**Camada fina de SO:** Programa → Hardware (controle direto)  
**Camada complexa de SO:** Programa → SO → Driver → Hardware

> **Compilação alvo-específica:**
>
> - Para SO: Usa APIs e bibliotecas do sistema
> - Para microcontrolador: Fala com registradores e pinos

---

## Conclusão

Este documento conecta os fundamentos físicos da eletrônica com a programação moderna, mostrando como:

1. **Componentes básicos** evoluíram para **sistemas complexos**
2. **Sistemas numéricos** facilitam a **comunicação homem-máquina**
3. **Portas lógicas simples** constroem **processadores poderosos**
4. **Camadas de abstração** tornam a programação **mais acessível**
5. **Interfaces diversas** atendem **diferentes necessidades**

> **Próximo passo:** Aplicar estes conceitos em projetos práticos de programação e eletrônica!

**Documentos relacionados:**

- **[Interfaces de Usuário e Terminal](./interfaces-terminal.md)** - Comandos práticos e interfaces
- **[Tabela de Conversão de Sistemas Numéricos](./tabela-conversao-sistemas.md)** - Referência completa
