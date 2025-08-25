% More on Finite Automata and Regular Languages
% Alyssa Lytle
% August 26, 2025

<!-- pandoc -t slidy -s notes/02-fa-prac.md -o slides/02-finite-automata-practice.html --webtex -->

# Finite Automata and Regular Languages Practice

## Gumball Machine Problem
    Design a DFA that represents a gumball machine with the following properties:

    * It takes nickels and dimes as inputs
    * If it receives 15 cents total, it dispenses a gumball
    * If it receives more than 15 cents, it dispenses a gumball and change


    Think of an "accept" state as one where a gumball is dispensed.

    (It's ok if your solution doesn't look quite like your neighbor's! There are multiple correct answers! We're going to compare!)

## Gumball Machine Solutions

## More notation

Let's talk more about our transition function $\delta$...

We've so far discussed $\delta$ in terms of

- $\delta: Q \times \Sigma \to Q$

In other words $\delta$ is handling state transitions given a single input from $\Sigma$.

What if we wanted to discuss *strings* of input?

## Extending the Transition Function to Strings

$$\Hat{\delta}: Q \times \Sigma^* \to Q$$

### Formal Definition

Let $w$ be a string of the form $xa$; 

That is $w= xa$, where $x$ is a string and $a$ is a symbol.

Then 

$$\Hat{\delta}(q,w) = \delta(\Hat{\delta}(q,x),a)$$


## Practice [^hopcroft]

Let us design a DFA to accept the language:

$$ L = \{w | w \textrm{ is of even length and begins with } 01 \}$$

## Practice

Let us design a DFA to accept the language:

$$ L = \{w | w \textrm{ is of even length and begins with } 01 \}$$

What we need to track:

* Whether it starts with 01
* Whether the input length is even

## Practice

Show $\Hat{\delta}(q_0, 011101) = q_2$

## Proving Properties About Automata [^sipser] [^kozen]

### Want to Prove (WTP):

Assume $A$ and $B$ are regular languages. Then $A \cap B$ is also regular.

## Proving Properties About Automata 

### Want to Prove (WTP):

Assume $A$ and $B$ are regular languages. Then $A \cap B$ is also regular.

If $A$ and $B$ are regular, then there exist automata

$M_1 = (Q_1, \Sigma, \delta_1, s_1, F_1)$

$M_2 = (Q_2, \Sigma, \delta_2, s_2, F_2)$

With $L(M_1) = A$ and $L(M_2) = B$.

To prove $A \cap B$ is regular, we need to build an automaton for it!



## Proving Properties Cont.

* $L(M_1) = A$ and $L(M_2) = B$.
* $M_1 = (Q_1, \Sigma, \delta_1, s_1, F_1)$
* $M_2 = (Q_2, \Sigma, \delta_2, s_2, F_2)$


Let $M_3 = (Q_3, \Sigma, \delta_3, s_3, F_3)$

with 

## Proving Properties Cont.

Given: 

For all $x \in \Sigma^*$, $\Hat{\delta_3}((p,q),x) = (\Hat{\delta_1}(p,x),\Hat{\delta_2}(q,x))$.

## Proving Properties Cont.

### WTP $L(M_3) = L(M_1) \cap L(M_2)$

* $L(M_1) = A$ and $L(M_2) = B$.
* $M_1 = (Q_1, \Sigma, \delta_1, s_1, F_1)$
* $M_2 = (Q_2, \Sigma, \delta_2, s_2, F_2)$
* $\Hat{\delta_3}((p,q),x) = (\Hat{\delta_1}(p,x),\Hat{\delta_2}(q,x))$.


## Resources

[^hopcroft]: - Hopcroft, John E., Rajeev Motwani, and Jeffrey D. Ullman. "Introduction to automata theory, languages, and computation." Acm Sigact News 32.1 (2001): 60-65.

[^kozen]: - Kozen, Dexter C. Automata and computability. Springer Science & Business Media, 2007.

[^sipser]: - Sipser, Michael. "Introduction to the Theory of Computation." ACM Sigact News 27.1 (1996): 27-29