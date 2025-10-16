# Introdução a Eletrônica e Programação

## O que é Elétrica

A elétrica é a área que estuda e aplica o fluxo de energia elétrica.
Seu objetivo é transportar, distribuir e controlar a corrente de forma segura e eficiente.
Podemos pensar nela como a “infraestrutura” que leva energia até onde ela será usada.

Principais componentes elétricos:

<img src="../images/res-cap-ind.png" alt="Resistor, Capacitor e Indutor" width="300" style="display: block; margin: 24 auto;">

- Resistor → É feito de um material que “resiste” à passagem da corrente elétrica, diminuindo sua intensidade.

- Capacitor → Funciona, de forma simples, como duas placas metálicas separadas por um material isolante. Ele armazena energia elétrica por um curto período e depois a libera.

- Indutor → É basicamente um fio enrolado em forma de espiral. Quando a corrente passa por ele, cria-se um campo magnético que pode armazenar energia temporariamente.

## O que é Eletrônica

A eletrônica vai além de apenas transportar energia: ela processa sinais e informações.
Usa componentes capazes de controlar o fluxo elétrico de forma muito precisa, permitindo criar sistemas inteligentes, como computadores, celulares e controladores industriais.

Principais componentes eletrônicos:

<img src="../images/dio-trans.png" alt="Resistor, Capacitor e Indutor" width="300" style="display: block; margin: 24 auto;">

- Diodo → Permite que a corrente elétrica passe apenas em um sentido, como uma “válvula” para elétrons.

- Transistor → Pode amplificar sinais ou funcionar como uma chave que liga e desliga a passagem de corrente.

## O Papel dos Semicondutores

Os semicondutores são materiais que têm propriedades intermediárias entre condutores (como o cobre) e isolantes (como o vidro).
Eles permitem controlar o fluxo de elétrons de forma muito precisa, o que é essencial para criar circuitos eletrônicos complexos.

Durante a Segunda Guerra Mundial, houve grandes avanços na purificação do germânio para produzir armamentos, permitindo fabricar diodos e transistores mais confiáveis.
Pouco tempo depois, o silício passou a ser o material preferido, pois é abundante, barato e suporta temperaturas mais altas.
Com o silício, foi possível criar circuitos integrados — pequenos chips que contêm milhões (hoje, bilhões) de transistores —, tornando os dispositivos eletrônicos cada vez menores, mais rápidos e mais eficientes.

## Sistemas Numéricos

Os sistemas numéricos são formas diferentes de representar quantidades.
O que usamos no dia a dia é o sistema decimal, provavelmente adotado por termos 10 dedos nas mãos, o que facilitou a contagem e a criação de símbolos para os números de 0 a 9.

Mas na eletrônica e na computação, outros sistemas são muito importantes:

Binário → Usa apenas dois dígitos: 0 e 1. É o “idioma” dos computadores, pois representa estados de desligado (0) e ligado (1).

Hexadecimal → Usa 16 símbolos: de 0 a 9 e de A a F. É muito usado para representar valores binários de forma mais compacta.

Tabela comparativa de contagem:

📊 **[Veja a tabela completa de conversão entre sistemas numéricos](./tabela-conversao-sistemas.md)**

Note que 4 algarismo binários são representado com um único número em hexadecimal. Essa simetria se dá porque 2^4 = 16. Conversões entre binários e decimais não são tão diretas, isto porque 10 não é solução para 2^x onde x é um número inteiro.

Logo um número como 101110 em binário, podemos separá-los em grupo de 4, adicionando zeros a esquerda conforme necessário (padding).

Isso resulta numa representação 0010 1110, que em hexadecimal é 2E.
É comum em programação usarmos 0b para número binários e 0x para hexadecimais, assim: **0b00101110 = 0x2E**.

## Sistemas Eletrônicos: Analógicos e Digitais

Os sistemas eletrônicos podem ser classificados principalmente em analógicos e digitais:

Analógicos → Trabalham com sinais contínuos, que podem assumir qualquer valor dentro de um intervalo. Como o sinal pode ter infinitos valores, qualquer interferência (ruído) pode alterar levemente o resultado. Por exemplo, um microfone analógico pode captar sons indesejados ou distorções.

Digitais → Trabalham com sinais discretos, normalmente representados por 0 e 1. Pequenas interferências geralmente não afetam o funcionamento, pois o sistema só precisa identificar se o sinal está mais próximo de 0 ou de 1. Isso torna os sistemas digitais mais confiáveis em ambientes com ruído.

## Sistemas Digitais Síncronos e Assíncronos

Dentro dos sistemas digitais, existe uma diferença importante:

### Síncronos

Funcionam seguindo um relógio interno (clock). Todas as operações acontecem em momentos determinados por esse sinal de sincronização. Num sistema síncrono é mais fácil garantir que todos os componentes do sistema estejam “no mesmo passo”. Isso evita erros de comunicação entre partes diferentes do circuito e simplifica o projeto.

### Assíncronos

Não dependem de um clock central. As operações acontecem assim que os sinais chegam e estão prontos. Apesar de poderem ser mais rápidos em alguns casos, são mais difíceis de projetar e depurar, pois cada parte do sistema pode estar operando em tempos diferentes.

## Portas Lógicas e Lógica Booleana

As portas lógicas são blocos básicos que processam sinais digitais.
Elas recebem entradas (0 ou 1) e produzem uma saída (0 ou 1) de acordo com uma regra específica.
Na prática, essas portas são construídas usando transistores, que funcionam como pequenas chaves eletrônicas.

Principais portas lógicas:

AND (E) → Só retorna 1 se todas as entradas forem 1.

OR (OU) → Retorna 1 se pelo menos uma entrada for 1.

NOT (NÃO) → Inverte o sinal: transforma 1 em 0 e 0 em 1.

XOR (OU Exclusivo) → Retorna 1 se apenas uma das entradas for 1.

XNOR (OU Exclusivo Negado) → Retorna 1 se as entradas forem iguais.

NAND (E Negado) → Retorna 0 apenas se todas as entradas forem 1 (inverso da AND).

NOR (OU Negado) → Retorna 1 apenas se todas as entradas forem 0 (inverso da OR).

## Computadores Digitais vs Analógicos

Um computador digital trabalha com informações representadas em forma binária (0 e 1). Isso torna o processamento mais confiável, pois pequenas variações ou ruídos não afetam o resultado final — basta identificar se o sinal está mais próximo de 0 ou de 1.
Já um computador analógico trabalha com sinais contínuos, onde qualquer valor dentro de um intervalo é possível. Eles eram usados em cálculos científicos e controles industriais antes da popularização dos digitais, mas são mais sensíveis a ruídos e menos flexíveis para tarefas complexas.

## Operações de Soma e Subtração com Portas Lógicas

As portas lógicas não servem apenas para comparar sinais — elas também podem ser combinadas para realizar operações matemáticas.
Por exemplo, para somar dois números binários, usamos circuitos chamados somadores (adders), que combinam portas AND, OR e XOR para calcular o resultado e o “vai um” (carry).
Para subtração, podemos usar um somador junto com portas NOT para inverter bits e aplicar o método do complemento de dois.

Somando dois números de 1 bit
Para somar dois números binários de 1 bit (A e B), usamos um circuito chamado meio somador (half adder), que combina duas portas lógicas:

Porta XOR → Calcula o bit de resultado (Soma). Observe que o resultado sempre é 0 se as entradas forem iguais.

Porta AND → Calcula o “vai um” (Carry). Observe que no carry, a saída é 1 apenas se ambas entradas forem 1.

Tabela verdade – Meio Somador:

| A   | B   | Soma (XOR) | Carry (AND) |
| --- | --- | ---------- | ----------- |
| 0   | 0   | 0          | 0           |
| 0   | 1   | 1          | 0           |
| 1   | 0   | 1          | 0           |
| 1   | 1   | 0          | 1           |

📌 Exemplo:
1 + 1 (em binário) → Soma = 0, Carry = 1 → Resultado final = 10 (binário).

## Funcionamento Básico de uma ALU

A ALU (Unidade Lógica e Aritmética) é a parte do processador responsável por fazer cálculos e comparações.
Ela é composta de forma bem simplificada por:

<img src="../images/alu.png" alt="Resistor, Capacitor e Indutor" width="300" style="display: block; margin: 24 auto;">

Entradas → dois valores (A e B) binários para serem processados.

Selecionador de operação → um conjunto de bits que indica qual operação fazer (soma, subtração, comparação, etc.).

Saída → o resultado da operação.

Status → resultado de status da operações, é o exemplo do carry citado anteriormente.

A ALU é formada por combinações de portas lógicas. O que você escreve em código de máquina ou assembly (como ADD A, B) é traduzido internamente para sinais que controlam essas portas, dizendo à ALU qual operação executar.

📌 É importante lembrar que o computador não é só a ALU: ele também tem memória, circuitos de controle, interfaces de entrada e saída e outros componentes que trabalham juntos.

## Compilação e Sistemas Operacionais

Um programa escrito por você normalmente passa por um processo chamado compilação, que transforma o código em instruções que o processador entende.

Sem Sistema Operacional → Em chips simples, como um microcontrolador, o programa é gravado diretamente na memória e controla o hardware sem intermediários. É comum em dispositivos como controles remotos, brinquedos eletrônicos ou placas de automação.

Com Sistema Operacional Simples → Alguns videogames antigos, como o PlayStation 1, não tinham um sistema operacional complexo como os PCs atuais. O jogo carregava diretamente no hardware, usando apenas rotinas básicas para acessar gráficos, som e controles.

Com Sistema Operacional Completo → Computadores pessoais (PCs) usam sistemas operacionais como Windows, Linux ou macOS, que oferecem uma enorme variedade de funções, compatibilidade com diferentes tipos de hardware e suporte para diversos programas ao mesmo tempo. Consoles mais modernos também, como o PlayStation 5, têm sistemas operacionais robustos que gerenciam memória, gráficos, rede e múltiplas tarefas ao mesmo tempo. Isso permite rodar jogos, aplicativos e serviços online simultaneamente.

Podemos imaginar uma linha evolutiva da complexidade do sistema operacional:

Microcontroladores → Super Nintendo → PlayStation 1 → PlayStation 5/PC

À medida que avançamos nessa linha:

O controle direto do hardware diminui.
A camada de software entre o programa e o hardware aumenta.
A compilação precisa considerar mais recursos e restrições do sistema operacional.
Nos primeiros exemplos, o código fala quase diretamente com o hardware.
Nos últimos, o código conversa com o sistema operacional, que por sua vez controla o hardware.

## Controle de Hardware e Drivers

Quando o sistema operacional é uma camada fina, o programa tem mais controle direto sobre o hardware.
Quando o sistema operacional é mais complexo, o acesso ao hardware é mediado por drivers — pequenos programas que sabem como conversar com cada dispositivo (placa de vídeo, impressora, etc.).

Compilar para um sistema operacional significa gerar um programa que usa as funções e bibliotecas que o SO oferece.
Compilar para um microcontrolador sem SO significa escrever código que fala diretamente com os registradores e pinos do chip.

## Terminal e Interfaces Gráficas

No sistema operacional, podemos interagir de duas formas principais:

Terminal → Uma interface baseada em texto, onde digitamos comandos e recebemos respostas. É muito usado para administração, programação e controle direto do sistema.

Interface Gráfica (GUI) → Uma interface visual com janelas, ícones e botões, pensada para facilitar o uso por pessoas que não querem memorizar comandos.
Essas duas formas estão relacionadas: a interface gráfica é, na prática, um programa que envia comandos ao sistema, assim como o terminal, mas de forma visual e mais amigável.

# Usando o Terminal no macOS – Comandos Básicos

O **terminal** é uma forma de interagir com o computador usando texto, digitando comandos que o sistema operacional executa.  
No macOS, o terminal segue a base do **Unix**, então muitos comandos funcionam igual no Linux.

A seguir, alguns comandos e operadores essenciais para começar:

---

## Comandos

```bash
### `pwd` – Print Working Directory
# pwd
# Saída: /Users/seunome/Documents
# Mostra o caminho completo da pasta onde você está no momento.

# cd – Change Directory
# Muda para outra pasta (diretório).
cd /Users/seunome/Desktop

# Acessar a pasta pessoal (home):
cd ~
# ou simplesmente
cd

# pbpaste
# Cola no terminal o conteúdo que está na área de transferência (clipboard).
pbpaste > texto.txt
# Cola o que está no clipboard dentro do arquivo texto.txt

# pbcopy
# Copia para a área de transferência o que for enviado para ele.
cat texto.txt | pbcopy
# Copia o conteúdo do arquivo texto.txt para o clipboard
ls – List
# Lista os arquivos e pastas do diretório atual.

# ls
# Com argumentos adicionais:

# -a → Mostra arquivos ocultos (que começam com .)
# -l → Mostra detalhes (permissões, tamanho, data)
# -al → Combina os dois (arquivos ocultos + detalhes)
ls -al

# open
# Abre um arquivo ou pasta com o aplicativo padrão do macOS.
open foto.jpg
open .
# O ponto (.) abre a pasta atual no Finder

# cat – Concatenate
# Mostra o conteúdo de um arquivo no terminal.
cat texto.txt

# grep – Global Regular Expression Print
# Procura por uma palavra ou padrão dentro de arquivos ou na saída de outro comando.
grep "erro" log.txt
# Mostra todas as linhas do arquivo log.txt que contêm a palavra "erro"
cat log.txt | grep "sucesso"
# Filtra a saída do cat para mostrar apenas linhas com "sucesso"


# Operadores

# | (pipe)
# Envia a saída de um comando como entrada para outro comando.
cat texto.txt | pbcopy
# O conteúdo do arquivo é enviado para o pbcopy

# > (redirecionamento)
# Envia a saída de um comando para um arquivo, substituindo o conteúdo existente.
echo "Olá mundo" > arquivo.txt
# Cria ou substitui arquivo.txt com o texto "Olá mundo"

# >> (redirecionamento com append)
# Envia a saída de um comando para um arquivo, adicionando ao final sem apagar o conteúdo existente.
echo "Nova linha" >> arquivo.txt
# Adiciona "Nova linha" ao final do arquivo.txt
```
