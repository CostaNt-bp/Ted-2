# Ted-2 
Central Recursiva Robusta (TED 02)

Integrantes da dupla:

Bonifácio Pinto Costa Neto(26.1.17242)
Descrição do Projeto

Esta aplicação foi desenvolvida como parte da atividade TED 02, tendo como objetivo solucionar o problema “CentralRecursiva Robusta”, proposto na plataforma beecrowd.

O sistema é responsável por executar operações matemáticas por meio de algoritmos recursivos, utilizando principalmente o cálculo do Máximo Divisor Comum (MDC) e a soma dos dígitos de um número. Além disso, a aplicação possui mecanismos de validação das entradas e utiliza exceções personalizadas para identificar e tratar dados ou operações inválidas.

Instruções para Execução

Para executar o projeto, é necessário possuir o Python 3.11 ou uma versão superior instalada no computador.

Após isso, siga os seguintes passos:

Faça o clone do repositório para sua máquina.
Abra o terminal e navegue até a pasta principal do projeto.
Execute o arquivo principal utilizando o comando:
python main.py

Informe a quantidade de operações que serão realizadas.
Em seguida, digite cada operação seguindo o formato esperado, como:
M 48 18 S 2026

Organização dos Módulos

O projeto está estruturado no pacote central_recursiva, com cada arquivo tendo uma função específica:

init.py: responsável por identificar o diretório como um pacote Python.
excecoes.py: contém as classes responsáveis pelos erros personalizados utilizados durante a execução do programa.
matematica.py: reúne os principais cálculos matemáticos e implementa as funções utilizando recursividade.
main.py: arquivo principal localizado na raiz do projeto. Ele realiza a leitura das informações fornecidas pelo usuário, verifica a validade dos dados, executa as operações matemáticas e trata possíveis erros utilizando as estruturas try, except e finally.
Implementação dos Algoritmos Recursivos

O módulo matematica.py possui duas operações principais desenvolvidas com o uso de recursividade.

MDC Recursivo

Para calcular o Máximo Divisor Comum, é utilizado o Algoritmo de Euclides.

A função recebe dois valores, a e b. Quando o segundo valor é igual a zero, o primeiro valor é retornado como resultado. Caso contrário, a função é chamada novamente utilizando b e o resto da divisão de a por b, obtido através de a % b.

Esse processo continua de maneira recursiva até que seja encontrado o MDC dos dois números.

Soma Recursiva dos Dígitos

A segunda operação realiza a soma de todos os dígitos de um determinado número.

A função verifica inicialmente se o valor recebido é igual a zero. Nesse caso, retorna 0 e encerra a recursão.

Caso contrário, o último dígito é obtido através da operação n % 10. Em seguida, esse valor é somado ao resultado de uma nova chamada da função, passando n // 10, que elimina o último dígito do número.

Dessa forma, a função continua sendo chamada até que todos os algarismos sejam processados.

Tratamento de Exceções Personalizadas

Para tornar o sistema mais seguro e preparado para lidar com entradas incorretas, foram criadas duas classes de exceção próprias, ambas derivadas da classe padrão Exception do Python.

OperacaoInvalidaError

Essa exceção é utilizada quando o usuário informa uma operação que não está entre as opções permitidas pelo sistema.

As operações válidas são:

M — cálculo do MDC;
S — soma dos dígitos.
Caso seja informado outro caractere ou comando, a exceção correspondente é acionada.

EntradaInvalidaError

Essa exceção é utilizada quando a operação informada é válida, porém os parâmetros fornecidos apresentam algum problema.

Entre os casos tratados estão números negativos, valor zero em operações de MDC ou quantidade insuficiente de parâmetros numéricos.

Com essas validações e tratamentos, o sistema consegue evitar falhas durante a execução e fornecer um processamento mais organizado e confiável das operações solicitadas.

SUBMISSÃO # 1618260

Solução Python — Central Recursiva Robusta

import sys
class OperacaoInvalidaError(Exception):
pass
class EntradaInvalidaError(Exception):
pass
def mdc
_
recursivo(a, b):
if b == 0:
return a
return mdc
_
recursivo(b, a % b)
def soma
_
digitos
_
recursivo(n):
if n < 10:
return n
return (n % 10) + soma
_
digitos
_
recursivo(n // 10)
def main():
input
_
data = sys.stdin.read().splitlines()
if not input
data:
_
return
linhas = [linha.strip() for linha in input
_
data if linha.strip()]
if not linhas:
return
q = int(linhas[0])
for i in range(1, q + 1):
if i >= len(linhas):
break
linha = linhas[i]
partes = linha.split()
if not partes:
continue
operacao = partes[0]
try:
# Validação do tipo de operação
if operacao not in ('M'
,
'S'):
raise OperacaoInvalidaError()
# Operação M: MDC
if operacao ==
'M'
:
if len(partes) != 3:
raise EntradaInvalidaError()
try:
a = int(partes[1])
b = int(partes[2])
except ValueError:
raise EntradaInvalidaError()
if a <= 0 or b <= 0:
raise EntradaInvalidaError()
print(f"MDC = {mdc
_
recursivo(a, b)}")

