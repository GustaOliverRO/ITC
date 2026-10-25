# Prova 2 - Introdução a Teoria da Computação 

## A Máquina de Turing
**Máquina de Turing** é um modelo capaz de expressar 
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
***'Parcial'?;***
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
ao de um AP, possuirá uma sequência de *configurações*;
		
>> **Configuração**, dada uma Máquina de Turing 
M = (Q,Σ,Γ,δ, q0,B,F), uma configuração de M é uma tripla 
(α,q,β) tal que α,β ∈ Γ^∗ e q ∈ Q.
 		
>> **Passo computacional à esquerda**, Seja M uma MT com a 
7-tupla já definida e (X1...Xi-1qXiXi+1...Xn) uma configuração 
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
qualquer um dos três casos de passos computacionais, sendo
|-lM,|-rM e |-sM;
- OBS: A notação |-*M, refere-se a vários passos de uma só 
vez, ou seja, I |-*M J se, I |-M K e K |-*M J;

>> **Configurações iniciais e finais**, sendo M uma MT como já 
definida e w ∈ Σ^∗. A configuração (ε,q0,w) é chamada de 
configuração inicial de M com w. Se p ∈ F, então qualquer 
configuração da forma (α,p,β), tal que α,β são strings de Γ^∗ 
quaisquer, é chamada de configuração final de M.
- OBS: Note que a configuração inicial, representa diretamente 
somente a disposição da string w na fita e apresença da 
computação do MT no estado inicial. Enquanto, a configuração 
final, se resume ao passo que levará a MT a um estado de 
aceitação, **uma vez nesse estado não se pode mais ter função**
**de transição definidas.**

***Fazer Exercício 5.2***

>> **String aceitas e string não aceitas por MTs**, sendo M uma 
MT já definida, dizemos que uma string w ∈ Σ^∗ é aceita por M 
se  q0w |-*M If, tal que If é uma configuração final de M. Caso 
contrário, dizemos que M não aceita w.

>> **Strings Rejeitadas por MTs**, sendo M uma MT, como já 
definida, dizemos que uma string w ∈ Σ^∗ é rejeitada por M se 
q0w |-*M In, tal que In não é uma configuração final de M e MT 
para ao atingir a configuração In.

- Se string rejeitada -> string não aceita, entretanto a volta 
não é verdade, não fornecendo um se somente se, pois haverá 
casos que ela não é aceita, mas não será rejeitada, porque a 
MT entrará em LOOP e não findará sua execução.

***Fazer Exercício 5.3***

>> **Linguagens de Máquinas de Turing**, dada uma MT M como já 
apresentado, a linguagem L(M) = {w ∈ Σ^∗:(ε,q0,w) |-∗M  Cf,
tal que Cf é uma configuração final de M} é chamada de linguagem 
de M.

>> **Linguagens Decididas por Máquinas de Turing**, seja L uma 
linguagem, se existe uma MT que **sempre para** M talque 
L(M) = L, diz que M decide L.

>> **Linguagens Aceitas por Máquinas de Turing**, seja L uma 
linguagem, se existe uma MT M tal que L(M) = L, dizemos que M 
aceita L.

- OBS: Uma linguagem que pode ser decidida por uma MT também é 
dita uma linguagem Recursiva (R) ou Decidível. Uma linguagem 
que pode ser aceita por uma MT também é dita uma lingaguem 
Recursivamente Enumerável (RE). Em resumo, reconhecer significa 
garantir a resposta positiva para palavras pertencentes à 
linguagem; decidir significa garantir uma resposta correta, 
positiva ou negativa, para toda entrada, sempre terminando.
***Exercício 5.4***

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
instância de uma MT, que é capaz de simular todas as possíveis 
MTs. A MTU pode ser vista como um modelo matemático que descreve
o que é entendido como computador, 'sendo uma máquina capaz de 
executar todas os possíveis programas de um computador'.
 
### Detalhes de "baixo nível" em MT
> De forma geral é ter o cuidado e dicernimento que estamos 
sempre trabalhando com strings, este será o formado que será 
tomado tanto no input quanto no output das MTs.

#### Notação de Vários Argumentos de Input

> A ideia aqui é como representar e diferir de forma escrita 
as represetações quando uma MT tem mais de uma string w de 
input, neste caso, que não será raro, trabalharemos da forma 
M(w1,w2,...,wn) ou M(w1w2...wn). 

#### Representando Obj. Matemáticos em Binário

> Dado um objeto matemático S, usaremos a notação (xSy) para nos 
referir a string que codifica S.

- **Codificação Binária**, dado um objeto matemático S, a 
notação xSy se refere a string que representa a codificação de S 
em binário. A maneira exata de como codificar o objeto S depende 
do tipo de objeto em questão e deve sempre estar clara no 
contexto.

***OBS: É dito também como uma "descrição" de tal objeto***
***isto server para qualquer objeto ou somente para***
***representação em binário de MTs ?***

Exemplo o Grafo G e o xGy, sendo coisas distintas.

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
alterações, por isso de M(x) = y.

> **Função Computável**, uma função f : Σ∗ → Σ∗ para a qual 
existe uma MT M tal que ∀x ∈ Σ∗, M(x) = f (x), é denominada uma 
função computável.

### Problema da PARADA

> Em suma, este problema nos prova que há linguagens que não há
algoritmos (MTs) que as decidam/resolvam, entrando no conjunto
das Linguagem Recursivamente Enumeráveis. Na prova para a 
linguagem Lh, foi utilizado de propriedades mostradas em EXs 
anteriores, até que chegasse em uma máquina que seu comportamento
é uma contradição lógica.

- **Ver com o professor**, é dito que foi utilizado o método de prova por contradição, logo, assumimos a existência de uma Mh 
que decide Lh para depois provar por contradição esse equívoco. 
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
"Computabilidade" é ter uma MT U que receberá uma string que
será composta pela descrição xMy de um MT e uma string binária x
e efetuará a execução dessa computação de forma que o resultado
computacional de U(xMy,x) = M(x), ou seja, a MTU vai encapsular
e "emular" a execução que seria feita pela MT M com a string de
input x;
**Teorema**, existe uma MT U tal que ∀ MT M e ∀x ∈ Σ∗, temos 
U(xMy, x) = M(x).

**Teorema**, a lingaguem Lh é Recursivamente Enumerável, ou seja,
ela pode ser aceita por uma MT, mas não decidida.

**Teorema**, existe linguagem L tal que L ∈/ RE.

**--Exercicios 6.1 a 6.3--**

### MT, Pseudo-Código, generalidade e especifidade
É apresentado a ideia que para certos problemas, não é necessário
de maneira direta apresentar uma MT que resolva aquilo, pois 
será algo extremamente complicado, porém é mais fácil apresentar
um pseudo-código que resolva e por haver uma equivalencia entre
MTs e linguagem de programação, de maneira lógica você já estará 
apresentando a MT que resolva aquilo. 
Mas as MTs tem seu lado importante no meio técnico que é para a 
prova e concluções de hipóteses e teoremas, pois é mais fácil 
trabalhar com este objeto matemático para esse foco, enquanto,
se o foco for apresentar somente a resolução de um problema, 
talvez seguir pelo caminho das MTS não a decisão mais tranquila.

### MT não Determinísticas (MTN)
> **Máquina de Turing Não Determinística (MTN)**, é uma 7-tupla
N = (Q,Σ,Γ,(δ0,δ1),q0,B,F), de forma que cada um dos componentes 
Q,Σ,Γ,q0,B,F desta tupla tem o mesmo sigficado do caso de 
máquinas de Turing determinísticas. A diferença é que N não tem 
apenas uma função de transição, mas um par (δ0,δ1) de funções 
de transição.

> A semântica do não determinismo aqui é que a cada passo a 
máquina tem a capacidade de adivinha qual das funções ela deve
usar para fazer a transição. **A linguagem de uma MTN N é o** 
**conjunto de toda strig para a qual existe uma computação que**
**a aceite, ou seja, toda a string x tal que, a cada passo,** 
**existe uma escolha entre δ0 e δ1 que leve N a aceitar x.**

> **Configuração de uma MTN**, dada uma MTN N = 
(Q,Σ,Γ,(δ0,δ1),q0,B,F), uma Configuração de N é uma tripla 
(α,q,β) tal que α,β ∈ Γ^∗ e q ∈ Q.
>> Terminologia: Uma configuração (α,q,β) de uma MTN N é dita 
final, se q é um estado final de N.

> **Passo Computacional Não Deterministico |-N**, seja N =
(Q,Σ,Γ,(δ0,δ1),q0,B,F) uma Máquina de Turing não determinística e 
C uma configuração da máqina N.
• Se a aplicação da função δ0 faz máquina sair da configuração C 
e atingir a configuração C0, então escrevemos C |-N0 C0.
• Se a aplicação da função δ0 faz máquina sair da configuração C 
e atingir a configuração C1, então escrevemos C |-N1 C1.
Escrevemos C |-N C0 tanto para o caso de C|-N0 C0 ou para o caso
de C |-N1 C0.

> **Lingaugens aceitas por MTNs**, dada uma Máquina de Turing não 
Determinística N = (Q,Σ,Γ,(δ0,δ1),q0,B,F), a linguagem L(N) =
{w ∈ Σ^∗;(ε,q0,w)|-∗N CF, tal que CF é uma configuração final
de N} é chamada de linguagem de N.

> **Árvore de Computações Possíveis de MTNs**,...

**Teorema**, se L é aceita por uma MTN N, então ∀x ∈ L, a árvore 
de computações possíveis de N com x tem pelo menos um ramo 
finito.

**Teorema**, se N é uma MTN, então existe uma MT M tal que 
L(M) = L(N);
**Teorema**, se M é uma MT, então existe uma MTN N tal que 
L(N) = L(M);
***Exercícios 6.4 a 6.14***

## A Tese de Church-Turing
- Se um probelma computacional pode ser resolvido por algum 
dispositivo fisicamente realizável, então ele pode ser resolvido
por uma máquina de turing.


> Salvo engano o cápitulo tratará da prova e de como é possível 
a equivalência entre MT M e linguagem de programação de baixo e 
consequentemente de alto nível.

### MTs são equivalente a linguagem de programação
-> Entender a explicação sobre os conceito do modelo RAM, 
programação em assembly com o Pi;

### Vídeo 1
A tese de Church-turing de maneira geral é que a noção intuitiva 
de algoritmos é igual a algoritmos de máquina de turing. Por 
consequência se uma função é efetivamente computável, então ela é 
computável por meio de uma máquna de turing.

A máquina de turing será uma base de modelo universal de 
computação tudo e qualquer coisa que pode ser resolvido por meio 
de computador pode ser resolvido por máquina de turing.

**Tese de Church-Turing**, define que **tudo que é computável**, 
deve ser computável por **Máquinas de Turing**. Essa tese não 
pode ser provada, ela é uma hipótese (ou definição/axioma). No 
entanto, é universalmente aceita.

**Algoritmo**, é...

## Vídeo 2

- **Tese de Church-Turing**, um problema de decisão, ou uma 
função, é  **algoritmicamente computável** se, e somente se, 
existe uma MT que a decide, ou a computa. 
O ponto central é que com esta equivalência, não é mais 
necessário  a construção direta de um Máquina de Turing para a 
resolução de um problema é possível agora, pensar em um 
algoritmo, de forma mais ampla que resolva tal impasse e por 
consequência, haverá a MT que a resolve.

## Complexidade de Kolmogorov

### Informação, Complexidade e Aleatoriedade
>

> **A descrição de uma string**, uma descrição de x é uma string
xMyw tal que M é uma máquina de truring e w ∈ Σ^∗ e M(w) = x.

> **Descrição mínima**, uma descrição mínima de uma string x,
denotada d(x), é a menor string xMyw em ordem lexicográgica tal
que xMyw é uma descrição de x.

> **Complexidade de Kolmogorov**, relacionada a uma string,
denotada K(x), é o tamanho da descrição mínima de x, ou seja, 
K(x) = |d(x)|.

**Teorema**, existe uma constante c tal que ∀x ∈ Σ^∗,
K(x) ≤ |x|+c.

### Incompressibilidade de informação
> **String compressíveis e incompressíveis**, uma string é x é 
c-compressível se K(x) ≤ |x|−c. Caso x não seja c-compressível, 
dizemos que x é c-incompressível. Se uma string for 
1-incompressível, diremos simplesmente que ela é incompressível.

> **Propriedade**, uma propriedade é uma função booleana 
P : Σ^∗ → {0,1}. Dada uma string x ∈ Σ^∗, se P(x) = 1, diremos que x tem a propriedade P ou que a propriedade P é verdadeira para x. Caso contrário, diremos que a string x não tem a
propriedade P ou que a propriedade P é falsa para x.

> **Propriedade ubíqua**, é uma propriedade P que satisfaz o 
seguinte critério: a fração de strings de tamanho n cuja 
propriedade P é falsa tende a 0 quando n tende ao infinito.

> **Propriedade de strings Aleatórias**, se P é ubíqua, então 
dizemos que P é uma propriedade de string aleatórias.

**Teorema**, seja P uma propriedade computável de strings 
aleatórias. Seja I o conjunto de strings incompressíveis. Então, 
a quantidade de strings x em I tal que P é falsa é finita.

### Incomputabilidade da Complexidade de Kolmogorov




