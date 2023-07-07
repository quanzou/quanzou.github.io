---
layout: post
title: "The Play of The Cards"
katex: True
toc: true
categories:
  - Math
tags:
  - gambling
date:   2023-06-23 12:29:09 PM
---

A "perfect" hand at bridge means all $$13$$ cards of a suit comprising each hand.
The odds of one perfect hand is $$\tfrac{52\choose 13}{\binom{4}{1}}=158,753,389,900$$, 
while the odds of four perfect hands are 
$$\tfrac{\binom{52}{13}\binom{39}{13}\binom{26}{13}\binom{13}{13}}{4!}=2,235,197,406,895,366,368,301,600,000$$. 
The chances of this event happening are so humongous that it is almost impossible.
If six billion people in the world they all played one hand of cards every five 
minutes, twelve hours a day, such a coincidence would happen about once every 
ten trillion years. 

However, there were the astounding number of "perfect" hands reported each year:

[https://www.google.com/search?q=four+perfect+bridge+hands](https://www.google.com/search?q=four+perfect+bridge+hands&tbm=bks&tbs=bkt:s&source=newspapers]){: target="_blank"}.

The obvious explanation is that some decks are not randomly shuffled or dealt. 
It is worthwhile to note that two perfect shuffles of a "fresh" deck (arranged, 
conventionally, by suits in ascending ranks) followed by simple cuts order the 
cards for a deal of four "perfect" hands at bridge. 

## Randomness and Shuffling 

Intuitively, a deck of cards is **fair** if each outcome is enumerated and is 
represented identically as all others. The question of randomness is meaningful 
only when the ordering is being changed by some process such as shuffling. 

A **simple cut** __*c*__ translates the top card of the deck to the bottom; thus the 
power $$c^i$$ of this operation phase shifts the order $$1, 2, 3,\cdots,i,j,k,\cdots,2n$$ 
into the order $$j,k, \cdots,2n, 1, 2, 3,\cdots,i$$.

The **perfect (Faro) shuffle** __*s*__ on a 2n-card deck separates the top $$n$$ 
cards from the bottom $$n$$ cards and precisely interleaves them. 

If the top and bottom cards remaining unchanged in position, it's called 
an **perfect out-shuffle**: 

$$s(1, 2, 3,\cdots, n - 1, n, n + 1,\cdots, 2n - 1, 2n) = (1,n + 1,2,n + 2,\cdots, n, 2n)$$

The **modified perfect shuffle** **_s'_** constitutes the same operation as **_s'_**, 
but with the $$(n + 1)$$st card moving to the top and the $$n$$th card to the bottom. 
it's called an **perfect in-shuffle**: 

$$s'(1, 2, 3,\cdots, n - 1, n, n + 1,\cdots, 2n - 1, 2n) = (n + 1,1,n + 2,2,\cdots, 2n, n)$$

The **amateur shuffle** $$\bm{s_a}$$ divides the deck approximately into two
groups of $$n$$ cards and interleaves them singly or in clusters of 2, 3, or 4 
according to some probability distribution. 

Finally, the random shuffle $$\bm{s_r}$$ as an operation equivalent to 
scattering the deck and retrieving the cards blindly.

### Card Position After Single Perfect Shuffle

Since both types of perfect shuffle are completely deterministic, the cutting 
and interwaving motions could surely be described into an equation. 

If the card in position $$a_0$$ is moved to position $$a_1$$ 
by the **perfect out-shuffle**, __*s*__, then 

$$a_1 \equiv 2a_0 - 1, \quad\quad \pmod{2n-1}$$ 

For the non-trival example, let $$n=2$$, then 
$$s(1,2,3,4) = (1,{\color{red}3},{\color{red}2}, 4)$$. 
The first half card(s) $$2$$ becomes $$2\times 2-1=3$$ 
(remainder $$0$$ is treated as $$3$$); the second half card(s) $$3$$ 
wraps around at $$2\times 3-1 \pmod{3}=2$$.  

If the card in position $$b_0$$ is moved to position $$b_1$$ by the 
**perfect in-shuffle** **_s'_**, then

$$b_1 \equiv 2b_0, \quad\quad \pmod{2n+1}$$ 

Similary, $$s'(1,2,3,4) = (3,{\color{red}1},{\color{red}4},2)$$. 
The first half card(s) $$1$$ becomes $$2\times 1 \pmod{5} = 2$$; 
the second half card(s) $$4$$ wraps around at $$2\times 4 \pmod{5}=3$$.  

It's clear that the $$2\times$$ the original position is due to the operation 
of splitting the deck into $$2$$ equal parts and subsequently interweaving them; 
The modulo operator is a position correction for cards from the second half by 
wrapping $$2\times$$ the original position around.

### Card Position After Multiple Perfect Shuffle

After $$k$$ iterations of **perfect out-shuffle** __*s*__, the card originally 
in position $$a_0$$ has moved to position $$a_k$$. That is

$$\begin{aligned}
a_1 &= 2a_{0} - 1,    &\quad \pmod{2n-1} & \quad  \\
a_k &= 2a_{k-1} - 1,  &\quad \pmod{2n-1} & \quad k\ge 2
\end{aligned}$$ 

the formula for $$a_k$$ can be re-written as the $$k$$ recursive steps format: 

$$a_k = \overbrace{2(\cdots 2(2}^{k} a_0 - \underbrace{1)-1\cdots)-1}_{k} \pmod{2n-1}$$

By the **properties of modular arithmetic**, we can work out 
two recursive steps of **perfect out-shuffle**: 

$$\begin{aligned}
a_k &= 2a_{k-1} -1 \pmod{2n-1}\\
&= (2\pmod{2n-1}) \cdot (a_{k-1}\pmod{2n-1}) - 1 \pmod{2n-1}\\
&= (2\pmod{2n-1}) \cdot ((2a_{k-2} -1) \pmod{2n-1}) - 1 \pmod{2n-1}\\
&= (2\cdot 2 a_{k-2} \pmod{2n-1}) - 3 \pmod{2n-1}\\
&= 2^2a_{k-2} - (2^2 - 1)  \pmod{2n-1}
\end{aligned}$$ 

If working out all $$k$$ recursive steps of **perfect out-shuffle**, then we 
arrive at another formula for **perfect out-shuffle**. 

$$ a_k \equiv 2^k a_{0} - (2^k - 1), \quad\quad  \pmod{2n-1}$$

noting that $$a_k=1$$ for $$a_0 =1$$ and $$a_k=2n$$ for $$a_0=2n$$. 

The **perfect in-shuffle** **_s'_**, follows the similar formula: 

$$ b_k \equiv 2^k b_{0}, \quad\quad  \pmod{2n+1}$$

## Randomness and Cycling

If the **perfect out/in-shuffle** operation __*s/s'*__ are iterated $$f$$ times 
on a $$2n$$-card deck, where $$f$$ is minimal iteration required for the deck 
to be restored to its original ordering. 

We notice that a deck of cards is restored to its original ordering if and 
only if **every card is restored to its own original position**. that is, 

$$\begin{aligned}
2^k a_{0} - (2^k - 1) \pmod{2n-1} &= a_0\\
2^k b_{0} \pmod{2n+1} & = b_0
\end{aligned}$$ 

By noticing that $$1 \pmod{2n-1} = 1$$ and further applying the 
**properties of modular arithmetic** and some algebraic manipulation, we have 

$$\begin{aligned}
2^k \pmod{2n-1} \cdot (a_{0} - 1)&= a_0-1 \\
2^k \pmod{2n+1} \cdot b_{0} & = b_0
\end{aligned}$$ 

Thus, the equation can be further generalized as:

$$2^k \pmod{N} = 1, \quad\quad N=2n\pm 1$$

### Discrete Logarithm Problem and Euler's Totient Function

The equation above becomes a general **Discrete Logarithm Problem** (DLP). 

Let $$G$$ be any group and $$\odot$$ be the group operation. For any 
$$k \in \mathbb{Z}_{>0}$$, let $$g\in G$$, then we define 
$$g^k = \overbrace{g\odot\cdots\odot g}^{k-times}$$. Then for a given $$a \in G$$, 
the $$k$$ that satisfies $$g^k=a$$ is called discrete logarithm of $$a$$ to base $$g$$. 
It can also be written as $$k=\log_g a$$.

If we denote $$\odot$$ as the multiplicative group operation, and its identity 
element as $$1$$, *i.e.*, $$b^0=1$$, then the  **Discrete Logarithm Problem** (DLP) 
is specified as find $$k\in\mathbb{Z}_{>1}$$ such that $$a \equiv g^k \pmod{n}$$, 
given $$a, g, n \in \mathbb{Z}_{+}$$, if such $$k$$ exists. The integer $$k$$ 
is termed as a **discrete logarithm** of $$a$$ with respect to the base $$g$$ 
modulo $$n$$, commonly in cryptography. However, no efficient method is known 
for computing the solution, if exists, in general. 

Before, we dive deeper into the concept of **index**, the **discrete logarithm** 
equivalence in number theory, we have to introduce several definitions: 
**Euler's totient function**, **Carmichael’s theorem** and **Primitive Root**.

**Euler's totient function** counts the positive integers up to a given integer 
$$n$$ that are relatively prime to $$n$$. **Euler's phi function**, $$\varphi(n)$$, 
is the count of integers $$k$$ in the range $$1 \le k \le n$$ for which the 
greatest common divisor $$\mathrm{gcd}(n, k)=1$$. The integers $$k$$ of this 
form are referred to as **totatives** of n.

$$\begin{aligned}
\varphi(n) &= n \prod_{p\mid n} \left(1-\frac{1}{p}\right)\\
& = p_1^{r_1-1}(p_1{-}1)\,p_2^{r_2-1}(p_2{-}1)\cdots p_i^{r_i-1}(p_i{-}1)
\end{aligned}$$

where the product is over all prime divisors of $$n$$, 
$$n = p_1^{r_1} p_2^{r_2} \cdots  p_i^{r_i}$$ is the prime factorization of $$n$$, 
$$p_1, p_2,\ldots,p_r$$ are distinct prime numbers.

For example, there are $$8$$ numbers relative prime (coprime) to 
$$20: 1, 3, 7, 9, 11, 13, 17, 19$$.

$$\begin{aligned}
\varphi(20) &= \varphi(2^2 5) =20\,(1-\tfrac12)\,(1-\tfrac15)=20\cdot\tfrac12\cdot\tfrac45=8\\
\mathrm{or}\quad & = 2^{2-1}(2{-}1)\,5^{1-1}(5{-}1) = 2\cdot 1\cdot 1\cdot 4 = 8
\end{aligned}$$

The set of integers $$\{0, 1, 2, \dots, n − 1\}$$ is called the 
**least residue system modulo** $$\bm{n}$$, *e.g.*, $$\{0, 1, 2, 3\}$$ modulo $$4$$. 
Any set of $$n$$ integers, which are pair-wise incongruent modulo $$n$$, is called a 
**complete residue system modulo** $$\bm{n}$$, *e.g.*, $$\{1, 2, 3, 4\}$$ modulo $$4$$. 
The least residue system must be a complete residue system, and a complete residue 
system is simply a set containing precisely one representative of each residue 
class modulo $$n$$. 

A subset of integers from a complete system of residues modulo $$n$$ that are 
coprime with $$n$$, is called **reduced system of residues** $$\bm{n}$$. It contains 
exactly $$\varphi(n)$$ integers, which are pair-wise incongruent modulo $$n$$. 
*e.g.*, $$\{1, 3\}$$ modulo $$4$$. 

In 1640, Pierre de Fermat first proposed a theorem (**Fermat's little theorem**) 
without proof: If $$p$$ is a <font color=red>prime</font> number, then for any 
interger $$a$$, the number $$a^p-a$$ is an integer multiple of 
$$p$$, $$a^p\equiv a \pmod{p}$$.

Next, in 1736, Leonhard Euler proved Fermat's little theorem, and generalized it to 
the case where $$n$$ is not prime, *i.e.*, the **Euler's theorem**: if $$a$$ 
and $$n$$ are <font color=red>coprime</font> positive integers, then $$a$$ 
raised to the power $$\varphi(n)$$ is congruent to $$1$$ modulo $$n$$, 
$$a^{\varphi(n)}\equiv1\pmod{n}$$.

Finally, in 1910, Robert Carmichael defined the **Carmichael's function**, 
$$\lambda(n)$$, as the smallest positive integer $$\lambda$$ such that 
$$a^\lambda\equiv1\pmod{n}$$ holds for <font color=red>every integer</font> $$a$$ <font color=red>coprime</font> to $$n$$. 
He also proposed **Carmichael's theorem** to compute $$\lambda(n)$$: 

$$
\lambda(p^r)=\begin{cases}
\varphi\left(p^r\right) & p^r = 2,4,3^r,5^r,7^r,11^r,13^r,17^r,19^r,23^r,29^r,31^r,\dots \\
\varphi\left(2^{r-2}\right) & r\ge3, 2^r = 8,16,32,64,128,256,\dots
\end{cases}
$$

Let $$n = \prod_i p_i^{r_i}$$ be the prime factorization of $$n$$, 
then $$\lambda(n)$$ is the **least common multiple** of the $$\lambda$$ on the 
prime power factors:

$$\lambda(n)=\mathrm{lcm}\Bigl(\lambda\left(p_i^{r_i}\right)\Bigr)$$

$$\lambda(n)$$ is the exponent of the multiplicative group of integers modulo $$n$$ 
while $$\varphi(n)$$ is the order of that group. 

Now, we define a **primitive root modulo** $$\bm{n}$$ is an integer $$p$$ such that 

$$p^{\varphi(n)} \equiv 1 \pmod{n} \quad\mathrm{and}\quad p^{r} \not\equiv 1 \pmod{n}$$

for $$1\le r \le \varphi(n)$$. The powers of primitive root $$p$$, 
$$p^0=1,\dots,p^{\varphi(n)-1}$$ are incongruent modulo $$n$$, and form a 
**reduced system of residues modulo** $$\bm{n}$$. In other words, $$p$$ is a 
**primitive root modulo** $$\bm{n}$$ if for every integer $$a$$ coprime to $$n$$, 
there is some integer $$r$$ such that $$p^r\equiv a \pmod{n}$$. 
*e.g.*, given $$\varphi(4)=2$$, we have $$3^0\equiv 1 \pmod{4}$$, 
$$3^1\equiv 3 \pmod{4}$$ and $$3^2\equiv 1 \pmod{4}$$. Thus, $$\{3\}$$ is the 
primitive root modulo $$4$$. 

Therefore, for every number $$a$$ that is coprime to $$n$$, there exists an 
exponent $$r, 0\le r<\varphi(n)$$ such that $$p^r\equiv a \pmod{n}$$, *i.e.*, $$p$$ is 
a primitive root of $$n$$ and $$\mathrm{gcd}(a,n) = 1$$. we call 
$$r = \mathrm{ind}_p a \pmod{m}$$ the **index** of $$a$$ with respect 
to the base $$p$$ modulo $$n$$. 

Primitive roots do not exist for all moduli, but only for moduli $$n$$ of the 
form $$n \in \{2,4,p^r,2p^r| \text{prime } p>2; r\in \mathbb{N}\}$$. These are 
the numbers $$n$$ with its order equals its exponent, $$\varphi(n) = \lambda(n)$$. 
where the multiplicative group is cyclic due to the existence of a primitive root.

### Deck Cycles with Perfect Shuffles

Now, let's look back our problem of how many times of perfect shuffle is required 
to restore a $$2n$$-deck to its original ordering. The generalized equation is: 

$$2^k \pmod{N} = 1, \quad\quad N=2n\pm 1$$

where $$N=2\cdot26-1=51$$ for **perfect out-shuffle**; $$N=2\cdot26+1=53$$ 
for **perfect in-shuffle**. 

For the case of **perfect in-shuffle**, since $$N=53$$ is a prime number, and $$2$$ 
is one of its primitive root, then we have $$k=\varphi(53)=53-1=52$$ by 
**Carmichael’s theorem**. 

For the case of **perfect out-shuffle**, since $$N=51=3\cdot17$$, then we have 
$$k=\lambda(51)=\mathrm{lcm}\Bigl(\lambda(3),\lambda(17)\Bigr)=\mathrm{lcm}(2,16)=16$$ by 
**Carmichael’s theorem**, again. However, since we know the order 
$$\varphi(53)=2\cdot16=32$$ does not equal the exponent, then there does not exist 
a primitive root modulo $$51$$. The condition "$$a^\lambda\equiv1\pmod{51}$$ holds 
for <font color=red>every integer</font> $$a$$ <font color=red>coprime</font> to $$51$$" 
of **Carmichael’s theorem** is too strict in this case and needs to be relaxed. 
We only need to satisfiy $$a^\lambda\equiv1\pmod{51}$$ holds for $$a=2$$! 
We already know that $$k<16$$, so we found that 
$$2^k\equiv1\pmod{51}$$ being cyclic when $$k=8$$ by enumerating: 

~~~ r
> 2^seq(1:16)%%51
 2  4  8 16 32 13 26  1  2  4  8 16 32 13 26  1
~~~

We also notice that **perfect out-shuffle** of $$52$$-deck is equivalent to 
**perfect in-shuffle** of $$50$$-deck, since $$2\cdot26-1=51=2\cdot25+1$$. 
In general, the cycle of out-shuffles needed for $$2n$$ cards is the same as the 
number of in-shuffles needed for $$2(n-1)$$ cards, effectively making an 
in-shuffle “one step” before an out shuffle.

An out-shuffle does not affect the top and bottom card of the deck, it only 
changes the position of the cards between them. Isolating the $$1$$st and 
$$2n$$th cards of the deck and performing **perfect in-shuffle**, we can easily 
see that all $$2(n-1)$$ cards position is identical to the middle portion of 
**perfect out-shuffle**:

$$s'(2, 3,\cdots, n - 1, n, n + 1,\cdots, 2n - 1) = (n + 1,2,n + 2,3,\cdots,2n-2,n-1,2n-1, n)$$

We conclude that every **perfect out-shuffle** is a **perfect in-shuffle** of 
the cards between the top and bottom cards. The table below tabulates the value
of $$k$$ for decks up to $$2n = 60$$ cards.

| $$2n$$ | $$k$$ | $$2n$$ | $$k$$ |
| :----: | :---: | :----: | :---: |
|	2	|	1	|	32	|	5	|
|	4	|	2	|	34	|	10	|
|	6	|	4	|	36	|	12	|
|	8	|	3	|	38	|	36	|
|	10	|	6	|	40	|	12	|
|	12	|	10	|	42	|	20	|
|	14	|	12	|	44	|	14	|
|	16	|	4	|	46	|	12	|
|	18	|	8	|	48	|	23	|
|	20	|	18	|	50	|	21	|
|	22	|	6	|	<font color=red>52</font>	|	<font color=red>8</font>	|
|	24	|	11	|	54	|	52	|
|	26	|	20	|	56	|	20	|
|	28	|	18	|	58	|	18	|
|	30	|	28	|	60	|	58	|

## Permutations by Cutting and Shuffling

If operations of both simple cut _**c**_ and perfect shuffle _**c**_ were combined, 
then how many possible permutations can be achieved? 

## Basic Terminology and Definition of Permutation Group

A **permutation group** is a group $$G$$ whose elements are permutations of a 
given set $$M$$ and whose group operation is the composition of permutations in 
$$G$$ (which are thought of as bijective functions from the set M to itself).
The group of **<font color=red>all</font>** permutations of a set $$M$$ is the 
**symmetric group** of $$M$$, $$\mathrm{Sym}(M)$$. The term permutation group 
thus means a subgroup of the symmetric group. If $$M = \{1, 2, \dots, 2n\}$$ 
then $$\mathrm{Sym}(M)$$ is usually denoted by $$S_{2n}$$, and may be called the 
symmetric group on $$2n$$ cards.

The **degree** of a permutation group over a finite set is the <font color=red>number 
of elements in the set</font>. The **order** (cardinality) of a group (of any type) 
is the number of elements in the group. *E.g.*, a $$2n$$-degree symmetric group 
$$S_{2n}$$ has the order of ($$2n$$)-factorial.

Permutations are also often written in **cycle notation** (cyclic form) so that 
given the set $$M = \{1, 2, 3, 4\}$$, a permutation $$g$$ of $$M$$ with $$g(1) = 2$$, 
$$g(2) = 4$$, $$g(4) = 1$$ and $$g(3) = 3$$ will be written as $$(1, 2, 4)(3)$$, 
or more commonly, $$(124)$$ since $$3$$ is left unchanged. 

A permutation group $$G$$ acting on a non-empty finite set $$M$$ is called 
**primitive** if $$G$$ acts transitively on $$M$$ and the only partitions 
the $$G$$-action preserves are the trivial partitions of either a single set 
or $$|M|$$ singleton sets. Otherwise, if $$G$$ is transitive and $$G$$ does 
preserve a nontrivial partition, $$G$$ is called **imprimitive**.

For example, the symmetric group $$S_4$$ acting on the set $$\{1, 2, 3, 4\}$$ 
and the permutation $$\sigma(1234)$$. The group generated by $$\sigma$$ is not 
primitive, since the nontrival partition $$\{1,3\}$$ and $$\{2,4\}$$ are preserved 
under $$\sigma$$, *i.e.*, $$\sigma(\{1,3\}) = \{2,4\}$$ and $$\sigma(\{2,4\}) = \{1,3\}$$. 

For another example, consider the symmetric group $$S_3$$ acting on the set 
$$\{1, 2, 3\}$$ and the permutation $$\sigma(123)$$. Both $$S_3$$ and the group 
generated by $$\sigma(123)$$ are primitive. We know 
$$S_3=\{e, (12), (13), (23), (123), (132)\}$$, the only partitions preserved 
after these groups act transitively on, are trival. 

### Orders of Permutation Groups Generated by Cuts and Shuffles

The **simple cut** _**c**_ places the top card of the deck on the bottom. The
powers $$c^i$$ of this operation yield all cuts of the deck. Clearly, **_c_** has 
order $$2n$$, since **_c_** is a "primitive" cyclic permutation on $$2n$$ objects. 

In 1961, Solomon W. Golomb has shown that the operations **_c_** and **_s_** together 
(cut and perfect in-shuffle) generate the entire symmetric group $$S_{2n}$$ of
permutations on the $$2n$$-cards (the operations **_c_** and **_s'_** also 
generate an entire symmetric group of permutations). 

For decks of size $$2n$$, S. W. Golomb has proved that the order of the product 
operation _**cs**_ assumes two cases: 

+ Case 1. If $$2n-1$$ is the power $$p^r$$ of a prime $$p$$, and $$2$$ is the 
primitive root modulo $$p^r$$, then the order of _**cs**_ is $$(k+1)\varphi(p^{r-1})$$.
*e.g.*, $$O_{cs}(54)=(52+1)\cdot1=53$$. 
+ Case 2. If $$2n-1$$ has the two or more distinct prime factors or, $$2n-1$$ is
the power of a prime, but $$2$$ is not primitive root modulo $$2n-1$$. then the 
order of _**cs**_ is $$k(k+1)$$. *e.g.*, $$O_{cs}(52)=8\cdot(8+1)=72$$.

where $$k$$ is the exponent of $$2$$ modulo $$2n-1$$, *i.e.*, $$2^k \pmod{2n-1} = 1$$, 
and $$\varphi$$ is Euler's function. 

This theorem provided by S. W. Golomb, expresses the equivalence between the operations 
$$c^is^j$$ and $$s_r$$. That is, <font color=red>the perfect shuffle and single-cut 
operations sufficiently iterated can produce complete randomness, for even-size decks</font>.

For decks of $$2n - 1$$ cards, the perfect shuffle **_s\*_** on an odd-sized deck, 
separates the bottom $$n$$ cards from the top $$n - 1$$ cards and interleaves 
the two sets, with the bottom card remaining on the bottom and the $$n$$th card 
emerging on the top. The operation **_s\*_** can be regarded as a mixture of 
perfect in-shuffle and perfect out-shuffle, and still has order of $$k$$ (the 
exponent of $$2$$ modulo $$2n-1$$. The simple-cut operation **_c\*_** on an 
odd-sized deck, has the order of $$2n-1$$ now. A theorem due to S. W. Golomb 
states that the operations **_c\*_** and **_s\*_** applied iteratively to 
a deck of $$2n — 1$$ cards generate a subgroup of the symmetric group $$S_{2n-1}$$ 
of order $$(2n-1)k\le(2n-1)(2n-2)$$. This subgroup is proper for $$n > 2$$. 
Therefore the operation $$c^is^j$$ can never be made equivalent to the random 
shuffle operation $$s_r$$, since <font color=red>not all permutations of 
odd-sized decks with more than three cards are obtained by the cutting and 
perfect shuffling operations, for odd-size decks</font>.

It is concluded that for decks of even size, combining cuts of shuffle is capable 
of introducing complete randomness; but for odd-sized decks, only a small 
fraction of the possible permutations of the deck can result. 

## Reference 

+ Richard A. Epstein, 2012. *The theory of gambling and statistical logic*. Academic Press.
+ Euler's totient function. [https://en.wikipedia.org/wiki/Euler's_totient_function](https://en.wikipedia.org/wiki/Euler's_totient_function){: target="_blank"}.
+ Fermat's little theorem. [https://en.wikipedia.org/wiki/Fermat's_little_theorem](https://en.wikipedia.org/wiki/Fermat's_little_theorem){: target="_blank"}.
