# Prova 2 - Introdução a Teoria da Computação 

## A Máquina de Turing
> **Máquina de Turin** é um modelo capaz de expressar 
qualquer algoritmo que possamos escrever em qualquer 
linguagem de programação conhecida.

> **Problema de Decisão**, é uma linguagem sobre um 
alfabeto binário. Encontrar um solução para um problema 
de decisão Lsignifica apresentar um algortimo que posse 
ser usado para determinar sistematicametne, em uma 
quantidade finita de passos, se uma dada string pertence 
ou não a linguagem L;

Na Máquinas de Turing, a string de entrada se encontra
disposta na fita de dados, logo, o domínio da função 
'delta' de MTs é apenas um par(estado, símbolo), pois a 
cada momento a máquina estará em um determinado estado
lendo uma posiçao específica da fita de dados;
	
> *Máquina de Turing*, é uma 7-tupla M(Q,Σ,Γ,δ,q0,B,F), 
tal que:
- Q é conjunto finito de estados;
- Σ é o alfabeto de entrada. Quando não especificado será o alfabeto binário;
- Γ é o alfabeto da fita, tal que o alfabeto de entrada esta contifo igual no alfabeto da fita;
- δ : (Q\F) x Γ -> Q x Γ x D é uma função parcial
- D = {L,R,S};
- q0 é o estado inicial;
- B é o símbolo especial chamado de *símbolo branco*;
- F está contido ou igual a Q, é o conjunto de estados finais;
		
> Terminalogia: 'a cabeça de leitura (cabeçote) da máquina está escaneando uma determinada célula da fita de dados'.
>> Funcionamento,  Suponha que a função δ(q,X) retorna
(q',X',d). Neste caso, o que acontece é que a se máquina estiver no estado q com o símbolo X na célula sendo escaneada na fita, então ela fará uma transição para o estado q', sobreescrevendo X na fita pelo símbolo X' e moverá sua cabeça de leitura da seguinte maneira: (1) Se d = L, então a cabeça de leitura se moverá para a esquerda (ou seja, no próximo passo a máquina estará escaneando a célula da fita do lado esquerdo da célula atual); (2) Se d = R, então a cabeça de leitura se moverá para a direita; (3) Se q = S, então a cabeça de leitura continuará na posição corrente.
		
Exercício, fazer uma MT para a linguagem L, sendo que
L = {a^nb^nc^n : n>= 1} , sobre o alfabeto = {a,b,c};
		
### Linguagem de uma Máquina de Turing
> Linguagem de uma MT, o processo de uma MT será, similar ao de um AP, possuirá uma sequência de configuarações;
		
> Configuração, dada uma Máquina de Turing M = (Q,Σ,Γ,δ, q0,B,F), uma configuração de M é uma tripla (α,q,β) tal que α,β ∈ Γ^∗e q ∈ Q.
		
- Paramos na página 79, continuar anotações em 5.2.3;
		
		
		
	
