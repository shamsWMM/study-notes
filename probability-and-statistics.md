# 1. Introduction to Probability
$P(A) = \frac{\text{number of ways A can happen}}{\text{number of things that can happen}}$

Example 1.1: If I flip a fair coin twice (independent flips), find the probability of $A$, if $A$ is: \
a. The event where at least one heads occurs. \
b. The event where no heads occurs.

Solution: $\Omega = \{hh, ht, th, tt\}$ \
a. $A = \{hh, ht, th\}, \quad P(A) = \frac{3}{4} = 0.75$ \
b. $A = \{tt\}, \quad P(A) = \frac{1}{4} = 0.25$

Example 1.2: If I roll two fair dice, find the probability of , if  is the event where at least one of the dice is 5.
Solution: $\Omega = \{11, 12, 13, \ldots, 66\}$
$A = \{15, 25, \ldots, 51, 52, \ldots, 56, 65\}, \quad P(A) = \frac{11}{36} = 0.30\overline{5}$ \
Another way to look at this: \
$P(A) = P(\text{first roll equals 5}) + P(\text{first roll is not 5})\cdot P(\text{second roll equals 5})$ 

# 2. Counting Probabilities with Combinatorics and the Factorial
Example 2.1: # of sequences of 10 coin flips \
$[2]  [2]  [2]  \ldots  [2], number = 2^{10}$  (with replacement, order matters)

Example 2.2: How many 5 card runs can I deal off the top of a 52 card deck?

$[52] [51] [50] [49] [48],\  number = 52 \cdot 51 \cdot 50 \cdot 49 \cdot 48 = \frac{52!}{47!}$ (without replacement, order matters)

For $n$ choices, sampling $r$, example 2.1 becomes $n^r$, and example 2.2 becomes $\frac{n!}{(n-r)!}$

If order doesn't matter for example 2.2, (not a run/sequence) $number  = \frac{n!}{r!(n-r)!} = {n \choose r} = n\mathcal{C}r$

# 3. Set Theory in Probability
A sample space, $\Omega$, is the set of all possible outcomes of a random experiment.
A specific element, $\omega$, is one outcome (realisation) of the experiment.

Example 3.1: 3 coin flips $\Omega = \{hhh, hht, hth, htt, thh, tht, tth, ttt\}$ \
First flip is a head: $A = \{hhh, hht, hth, htt\}$ \
Second flip is a tail $B = \{hth, htt, tth, ttt\}$ \
$A \cup B = \{hth, htt, hht, hhh, tth, ttt\}$ \
$A \cap B = \{hth, htt\}$ \
$A^{c} \cap B = \{thh, tht, tth, ttt\}$ \

The probability is a map from subsets of $\Omega$ to $ [0,1] \in \mathbb{R}$ \
$P(\Omega) = 1$ \
If $A \subset \Omega$ then $P(A) \geq 0$ \
If A and B are disjoint, i.e. $A \cap B = \emptyset$, then $P(A \cup B)=P(A) + P(B)$

# 4. The Birthday Problem
$P(A)= 1 - P(A')$

Problem: if there are $n$ people in a room, how large does $n$ need to be for at least 50% chance that at least two people share the same birthday?

There are $\frac{n(n-1)}{2}$ comparisons of two people that can be made. ${n \choose 2} = \frac{n!}{2!(n-2)!}$ \
$P(a\text{t least 2 share a birthday}) = 1 - P(\text{no shares})$

$P(\text{no shares}) = \frac{365}{365} \frac{364}{365} \frac{363}{365} \ldots \frac{365 - n + 1}{365}= \frac{365!}{(365-n)! \cdot365^n}$