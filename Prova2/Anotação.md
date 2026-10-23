# Prova 2 - Introdução a Teoria da Computação 

## A Máquina de Turing
> **Máquina de Turin** é um modelo capaz de expressar 
qualquer algoritmo que possamos escrever em qualquer 
linguagem de programação conhecida.

>> **Problema de Decisão**, é uma linguagem sobre um 
alfabeto binário. Encontrar um solução para um problema 
de decisão significa apresentar um algortimo que possa 
ser usado para determinar sistematicametne, em uma
quantidade finita de passos, se uma dada string pertence 
ou não a linguagem L;

> Nas Máquinas de Turing, a string de entrada se encontra
disposta na fita de dados, logo, o domínio da função 
'delta' de MTs é apenas um par(estado, símbolo), pois a 
cada momento a máquina estará em um determinado estado
lendo uma posição específica da fita de dados;
	
>> **Máquina de Turing**, é uma 7-tupla M(Q,Σ,Γ,δ,q0,B,F), 
tal que:
- Q é conjunto finito de estados;
- Σ é o alfabeto de entrada. Quando não especificado será o 
alfabeto binário;
- Γ é o alfabeto da fita, tal que o alfabeto de entrada está 
contido igual no alfabeto da fita;
- δ : (Q\F) x Γ -> Q x Γ x D é uma função parcial
'Parcial'?;
- D = {L,R,S}; -> Decisão do CABEÇOTE
- q0 é o estado inicial;
- B é o símbolo especial chamado de *símbolo branco*;
- F está contido ou igual a Q, é o conjunto de estados finais;
		
>> Terminalogia: 'a cabeça de leitura (cabeçote) da máquina 
está escaneando uma determinada célula da fita de dados'.
>>> Funcionamento,  Suponha que a função δ(q,X) retorna
(q',X',d). Neste caso, o que acontece é que a se máquina 
estiver no estado q com o símbolo X na célula sendo escaneada 
na fita, então ela fará uma transição para o estado q', 
sobreescrevendo X na fita pelo símbolo X' e moverá sua cabeça 
de leitura da seguinte maneira: (1) Se d = L, então a cabeça 
de leitura se moverá para a esquerda (ou seja, no próximo 
passo a máquina estará escaneando a célula da fita do lado 
esquerdo da célula atual); (2) Se d = R, então a cabeça de 
leitura se moverá para a direita; (3) Se q = S, então a cabeça 
de leitura continuará na posição corrente.
		
***Exercício, fazer uma MT para a linguagem L, sendo que***
***L = {a^nb^nc^n : n>= 1} , sobre o alfabeto = {a,b,c};***
		
### Linguagem de uma Máquina de Turing
>> A linguagem de uma MT, o processo de uma MT será, similar
ao de um AP, possuirá uma sequência de configuarações;
		
>> **Configuração**, dada uma Máquina de Turing 
M = (Q,Σ,Γ,δ, q0,B,F), uma configuração de M é uma tripla 
(α,q,β) tal que α,β ∈ Γ^∗ e q ∈ Q.
 		
>> **Passo computacional à esquerda**, Seja M uma MT com a 7-
tupla já definida e (X1...Xi-1qXiXi+1...Xn) uma configuração 
de M. Se δ(q,Xi)=(p,Y,L), então escrevemos
(X1...Xi−1qXiXi+1...Xn)|-l,M (X1...Xi−2pXi−1YXi+1...Xn).
Exceto nos casos que:
(1) Se i = 1, então escreve-se
(ε,q,X1...Xn)|-lM (ε, p,BY X2...Xn)
(2) Se i = n e Y = B, então escreve-se
(X1...Xn−1,q,Xn)|-lM (X1...Xn−2,p,Xn−1).
-> Essa definição acima representa um passo da computação de 
uma MT com o movimento do cabeçote da máquina à esquerda;

***Fazer Exercício 5.1*** 

>> **Passo Computacional de uma Máquina de Turing**, dada uma 
MT M, um passo computacional , denotado |-M, se refere a 
qualquer um dos três casos de passos computacionais, sendo |-
lM,|-rM e |-sM;
- OBS: A notação |-*M, refere-se a vários passos de uma só 
vez, ou seja, I|-*M J se, I|-M K e K|-*M J;

>> **Configurações iniciais e finais**, sendo M uma MT como já 
definida e w  ∈ Σ^∗. A configuração (ε,q0,w) é chamada de 
configuração inicial de M com w. Se p ∈ F, então qualquer 
configuração da forma (α, p,β), tal que α,β são strings de Γ^∗ 
quaisquer, é chamada de configuração final de M.
- OBS: Note que a configuração inicial, representa diretamente 
somente a disposição da string w na fita e apresenta da 
computação do MT no estado inicial. Enquanto, a configuração 
final, se resume ao passo que levará a MT a um estado de 
aceitação, **uma vez nesse estado não se pode mais ter função**
**de transição definidas.**

***Fazer Exercício 5.2***

>> **String aceitas e string não aceitas por MTs**, sendo M uma 
MT já definida, dizemos que uma string w ∈ Σ^∗ é aceita por M 
se  q0w|-*M If, tal que If é uma configuração final de M. Caso 
contrário, dizemos que M não aceita w.

>> **Strings Rejeitadas por MTs**, sendo M uma MT, como já 
definida, dizemos que uma string w ∈ Σ^∗ é rejeitada por M se 
q0w|-*M In, tal que In não é uma configuração final de M e MT 
para ao atingir a configuração In.

- Se string rejeitada -> string não aceita, entretanto a volta 
não é verdade, não fornecendo um se somente se, pois haverá 
casos que ela não é aceita, mas não será rejeitada, porque a 
MT entrará em LOOP e não findará sua execução.

***Fazer Exercício 5.3***

>> **Linguagens de Máquinas de Turing**, dada uma MT M como já 
apresnetado, a linguagem L(M)={w ∈ Σ^∗:(ε,q0,w)|-∗M Cf, tal 
que Cf é uma configuração final de M} é chamada de linguagem 
de M.

>> **Linguagens Decididas por Máquinas de Turing**, seja L uma 
linguagem, se existe uma MT que M talque L(M) = L, diz que M 
decide L.

>> **Linguagens Aceitas por Máquinas de Turing**, seja L uma 
linguagem, se existe uma MT M tal que L(M) = L, dizemos que M 
decide L.

- OBS: Uma linguagem que pode ser decidida por uma MT também é 
dita uma linguagem Recursiva (R) ou Decidível. Uma linguagem 
que pode ser aceita por uma MT também é dita uma lingaguem 
Recursivamente Enumerável (RE). Em resumo, reconhecer significa 
garantir a resposta positiva para palavras pertencentes à 
linguagem; decidir significa garantir uma resposta correta, 
positiva ou negativa, para toda entrada, sempre terminando.

### Um Alg. é uma MT que sempre para

>> **Algoritmo** é uma máquina de turing que sempre para.

***Fazer Exercício 5.5 à 5.10***

### Variações de Máquina de Turing

>> **Teorema** se uma MT com alfabeto da fita  Γ decide uma 
linguagem L, então existe uma MT M' com alfabeto da fita
Γ' = {0,1,B} que decide L.

>> **Teorema** se uma MT M com k fitas decide uma linguagem L, 
então existe uma MT M'com uma fita que decide L.

***Fazer Exercício 5.11 à 5.13***



## Computabilidade
> Será estudado/abordado dois teoremas, o primeiro é a prova que
existem problemas que não podem ser resolvidos por algoritmos,
o segundo é a existência de uma Maquina de Turing Universal, uma
instância de uma MT, que é cvapaz de simular todas as possíveis 
MTs. A MTU pode ser vista como um modelo matemático que descreve
o que é entendido como computador, 'sendo uma máquina capaz de 
executar todas os possíveis progrmas de computador'.
 
### Detalhes de "baixo nível" em MT
> De forma geral é ter o cuidado e dicernimento que estamos 
sempre trabalhando com strings, este será o formado que será 
tomado tanto no input quanto no output das MTs.

#### Notação de Vários Argumentos de Input

A ideia aqui será como representar e diferir de forma escrita 
nas represetações quando uma MT tem mais de uma string w de 
input, neste caso, que não será raro, trabalharemos da forma 
M(w1,w2,...,wn) ou M(w1w2...wn). 

#### Representando Obj. Matemáticos em Binário

Dado um objeto matemático S, usaremos a notação (xSy) para nos 
referir a string que codifica S.

- **Codificação Binária**, dado um objeto matemático S, a 
notação xSy se refere a string que representa a codificação de S 
em binário. A maneira exata de como codificar o objeto S depende 
do tipo de objeto em questão e deve sempre estar clara no 
contexto.
Exemplo do Grafo G e do xGy, sendo coisas extremamente distintas
**-> Ver algoritmos para transformar uma MT M em uma xMy;**
**-> Está no Exemplo 6.2**

### Funções Computavéis
Uma MT que sempre para resolvendo um problema de decisão pode
ser vista como uma máqina computando um função booleana. Com a 
ideia que para uma string binária w aceita pela máquina, tem-se 
fM(w) = 1 e, no c.c, em que uma string w é rejeitada pela 
máquina, temos fM(w) = 0;
 
> **Função Booleana Computável**, seja F : {0,1}^* -> {0,1}
uma função boolena. Suponha que existe um algoritmo M que tem o 
seguinte comportamento:
* Se f(x) = 1, então M aceita x;
* Se f(x) = 0, então M rejeita x;
-> Isto seria uma função booleana computável;

- **Notação**, suponha que uma string binária x é fornecida como
input de um MT M, com base no resultado da computação pode ter as
seguintes represetnações:
- M(x) = 1 quando M aceita  x e para;
- M(x) = 0 quando M rejeita x e para;
- M(x) = PARA quando M para com x, independete de aceitar ou 
rejeitar;
- M(x) = LOOP quando M não para com a entrada x;

- (i)  Se M é um algoritmo, então ∀x ∈ Σ∗, temos que M(x) = PARA.
- (ii) Se f é uma função booleana computatável, então existe um 
algoritmo M tal que ∀x ∈ Σ^∗ ocorre que M(x) = f(x).

**Notação**, seja M = (Q, Σ, Γ, δ , q0, B, F) uma MT e x ∈ Σ^∗. 
Suponha que y = y'y'' e que (ε, q0, x)|-^∗M (y′, qP, y′′), onde 
qP ∈ Q e a máquina M para após antingir a configuração
(y′, qP, y′′). Então escrevemos M(x) = y.
-> De forma geral, essa notação passa a ideia que dada uma string
binária x e uma MT M, M(x) = y será a parte da string que ficou
na fita após a ação de PARAR da MT, ou seja, na fita inicia x, 
mas após inumeros passos computacionais da MT, x pode sofrer 
alterações, por isso de M(x) = y, neste caso também.

> **Função Computável**, uma função f : Σ∗ → Σ∗ para a qual 
existe uma MT M tal que ∀x ∈ Σ∗, M(x) = f (x), é denominada uma 
função computável.

### Problema da PARADA

> Em suma, este problema nos prova que há linguagens que não há
algoritmos (MTs) que as decidam/resolvam, entrando no conjunto
das Linguagem Recursivamente Enumeráveis. Na prova para a 
linguagem Lh, foi utilizado de propriedade mostradas em EXs 
anteriores, até que chegasse em uma máquina que seu comportamento
é uma contradição lógica.

- Ver com o professor é dito que foi utilizado o método de prova 
por contradição, logo, assumimos a existência de uma Mh que 
decide Lh para depois provar por contradição esse equívoco. 
Porém, fiquei com um questionamento que no passo da prova em que:
- Se M(x) = PARA, então Mh(xMy,x) = 1;
- Se M(x) = LOOP, então Mh(xMy, x) = 0;
- Fique com dúvida nessa segunda implicação, como que a máquina
em si saberá que ela entrou em loop ? Essa terminologia seria 
somente na parte "teórica", porque fiquei com um impasse, que 
neste caso, a segunda implicação nunca seria possível de analisar
quebrando logo ali a prova da não existência da MT que decide a 
Lh.

### Máquina de Turing Universal
A ideia central aqui como já relatada no inicio do tópico 
"Computabilidade" é de ter uma MT U que receberá uma string que
será composta pela descrição xMy de um MT e uma string binária x
e efetuará a execução dessa computação de forma que o resultado
computacional de U(xMy,x) = M(x), ou seja, meio que a MTU vai 
encapsular e "emular" a execução que seria feita pela MT M com a 
string de input x;
**Teorema**, existe uma MT U tal que ∀ MT M e ∀x ∈ Σ∗, temos 
U(xMy, x) = M(x).

**Teorema** 

**Teorema**

**--Exercicios 6.1 a 6.3--**

Parei na Página 96;
### MT, Pseudo-Código, generalidade e especifidade

### MT não Determinísticas (MTN)



## A Tese de Church-Turing

> Salvo engano o cápitulo tratará da prova e de como é possível 
a equivalência entre MT M e linguagem de programação de baixo e 
consequentemente de alto nível.

## Complexidade de Kolmogorov


