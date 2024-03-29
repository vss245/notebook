# What is mathematics?

- basic elements of math are antithetic to each other and pretty varied: logic, intuition, analysis, construction, generality, individuality
- history begins in the East in 2000 BC and then in ancient Greece
- 17th century brought about a revolution that moved from axiomatic certainty to differential and integral calculus
- 19th century - return of the classical ideal of precision and proof
- mathematics is not just a system of conclusions and postulates
- it’s important to remove metaphysics sometimes - the concepts may not have a meaning “in themselves”
  - in the 19th century, the idea that mechanical forces and movements of particles are things “in themselves” and electricity, light and magnetism should be reduced to them (just like heat)
- the only relevant assertions concerning mathematical objects do not refer to reality (we don’t need to discuss or concern ourselves with what points, lines and numbers actually are)

## Chapter 1: The natural numbers

### Introduction

- created by the human mind to count objects, but they have no reference to the characteristics of objects
- fundamental operations: addition and multiplication
- theory of natural numbers - arithmetic
  - fundamental laws: a+b=b+a, ab=ba, a(b+c)=ab+ac
- we can also imagine types of arithmetics where these laws will not hold (e.g. if a and b aren’t numbers but chemical substances)
- we can define inequality using amounts (e.g. representing integers as dots in a box)
- we can also introduce zero (an empty box)
- Integers can be expressed by using units, tens, hundreds places etc
  - $z = a*10^3+b*10^2+c*10+d$, resulting in integer abcd
- this represents a decimal system (divisions by 10 for every successive place), but other numbers greater than 1 would do the same thing, e.g. septimal:
  - $b_n*7^n+b_{n-1}*7^{n-1}+b{n-2}*7^{n-2}...+ b_1*7+b_0$
  - one hundred and nine would be 109 in decimal and $2*7^2+1*7+4$
  - rule for conversion: passing from base 10 to any other base B is to perform successive divisions by B, and the remainder will indicate the digits of the number in base B
- duodecimal system (base 12) has been proposed since 12 is divisible by many numbers - but we would need new symbols for 10 and 11 (since they are included in the base now)
  - if $\alpha$ is 10 and $\beta$ is 11, twelve would be 10, twenty two would be $1\alpha$, twenty three would be $1\beta$
- positional notation is very important
  - roman numbers: CXVIII = 100+10+5+1+1+1
  - but purely additive notation is inconvenient because new symbols will be needed for larger numbers
- other computation systems
  - language can indicate remains of other bases, e.g. 11/12 vs the “teen”/“zehn” suffix (indicates a duodecimal system) or “vingt” and “quatrevingt” in French for 20 and 80.
  - babylonian astronomers partially used a base 60 system (remaining in the division of hours and days)
- exercise:
  - “thirty” and “one-hundred thirty-three” in different bases: 
    - base 10: 30 and 133
    - base 5: 110 and 1013
      - example: divide 30 by 5, get 6 and remainder 0, which is the last digit. divide 6 by 5, get remainder 1, second to last digit. leftover dividend is 1, which is less than the base and it becomes the first digit = 110
    - base 7: 42 and 250
    - base 11: 28 and 111
    - base 12: 26 and B1
- smallest possible base: 2 (binary)

### Mathematical induction

- there are infinitely many integers (infinite set)
- empirical induction exists in the natural sciences: observations => general law (certainty depends on the number of observations and confirmations)
- mathematical induction: establishes the truth of a mathematical theorem for an infinite sequence of cases
  - e.g. the sum of all angles in a polygon of n+2 sides is n*180 degrees - to prove this for all n, proving it for 10 or 100 or 1000 is not enough
  - instead, we use a method of reasoning:
    - e.g. we know for n=1 the polygon is a triangle and the sum of its angles is 180, a quadrilateral is a sum of 2 triangles, pentagon is a triangle plus a quadrilateral etc
  - two basic assumptions:
    - there exists a method to show that if A(r) is true then A(r+1) is also true
    - A(1), the base statement, is known to be true
    - then, the proposition is proved
- example: arithmetical progression (the sum 1+2+3...+n is equal to n(n+1)/2)
  - prove the assertion: we observe that if r is an integer and A is known to be true (i.e. $1+2+3+...+r = r(r+1)/2$), then we can add (r+1) to every side, obtaining $1+2+3+..+r+(r+1)=r(r+1)/2+(r+1)$, which is equal to $r(r+1)+2(r+1)/2=(r+1)(r+2)/2$
  - A1 is obviously true 
  - => statement is proven
  - we can also show this by writing the sum in two forms:
    - $S_n = 1+2+...+(n-1)+n$
    - $S_n=n+(n-1)+...+2+1$
    - each pair in the same column yields n+1 and since we have n columns, 2S = n(n+1)
- we can treat the geometrical progression in a similar way
  - $G_n=a+aq+aq^2+...+aq^n=a\frac{1-q^{n+1}}{1-q}$
  - multiply both sides by q, getting $qG_n=aq+aq^2+...+aq^{n+1}$
  - subtract G - qGn:
    - $a - aq^{n+1}$
    - $(1-q)G_n=a(1-q^{n+1})$
    - $G_n = a\frac{1-q^{n+1}}{1-q}$
- sum of the first n squares
  - $1^2+2^2+3^2+...+n^2=\frac{n(n+1)(2n+1)}{6}$
  - observe that if the assertion $A_n$ is true for the case $n=r$, then
  - $1^2+2^2+3^2+...+r^2=\frac{r(r+1)(2r+1)}{6}$
  - we can add $(r+1)^2$ to both sides:
    - $\frac{r(r+1)(2r+1)}{6}+(r+1)^2=\frac{r(r+1)(2r+1)+6(r+1)^2}{6}=\frac{(r+1)[r(2r+1)+6(r+1)]}{6}=\frac{(r+1)(r+2)(2r+3)}{6}$, which is also equal to A(r+1)
    - A1 is obviously true (1^2 = 1(1+1)(2+1)/6)
- the proof does not examine how the original assertion came to be

### An important inequality

- $(1+p)^n \geq 1+np$ for every p > -1 and positive integer n
- if it’s true that $(1+p)^r \geq 1+rp$, then we can multiply both sides by 1+p and get $(1+p)^{r+1}\geq rp+p+rp^2$ or even dropping the last term, $(1+p)^{r+1}\geq (1+r)p + 1$ which is also equal for the initial assertion if n = 1+p

### The binomial theorem

- explicit expressions for binomial powers:
  - $(a+b)^1=a+b$
  - $(a+b)^2=a^2+2ab+b^2$
  - $(a+b)^3=a^3+3a^b+3ab^2+b^3$
  - there is a general law that we can establish for this

### Notes on induction

- Compared to empirical induction, in mathematical induction proving a handful of cases is not enough (the law would remain a hypothesis)
- conditions: a) for any positive integer r the truth of A(r+1) will follow from that of Ar, b) A(1) is known to be true
- we should also always make true that the conditions a and b are satisfied, otherwise fallacies may occur:
  - we can “prove” that any two positive integers are equal
    - define max(a,b) as a or b, whichever is greater
    - let An be the statement: if a and b are any two positive integers such that max(a,b)=n, then a=b
    - suppose Ar to be true, let a and b be integers such that max(a,b)=r+1 
    - consider alpha = a-1 and beta = b-1, then max(alpha, beta)=r
    - hence alpha=beta, a=b follows
    - a1 is true since if max(a,b)=1 then since we are only using positive integers, b is also 1
  - the base case is valid here, but when a = 1 and b = 1, alpha and beta reduce to 0

### Theory of numbers

- most statements in number theory are concerned not with individual numbers, but with groups: e.g. all even integers, all squares of integers and so on
- primes are an important class (divided only by 1 and themselves)
- every integer can be expressed as a product of primes
- there are infinitely many primes
  - indirect proof: start with the assumption that this is false (there is a finite number of primes n, p1 ... pn)
  - produce a contradiction: a number A which differs from any of the primes because it is larger than any of them but is not divisible by any of them (A = p1p2...pn+1 - product of all primes +1)
  - A is larger than any of the primes and must be a composite, but A divided by any primes will have a remainder of 1, so none of the primes are a divisor => the contrary of the assumption must be true
- every decomposition of primes is unique
- sieve of Erastothenes:
  - primes up to N - write down all integers less than N, remove multiples of 2, then multiples of 3 etc
- producing primes:
  - Fermat conjecture: $F(n)=2^{2^n}+1$ will yield prime numbers
    - but Euler discovered that $2^{2^5}+1=641*6700417$
    - it has not been proved that any of the Fermat numbers for n > 4 are prime
  - another expression: $f(n)=n^2-n+41$, which works up to n = 40
  - $f(n)=n^2-79n+1601$ gives primes for n up to 79
- it was simple to prove that there are infinitely many primes in the sequence of all integers, but harder for arithmetic progressions like a, a+d, a+2d, a+nd where a and d have no common factor
- Dirichlet has constructed the proof, but it is hard to understand
- prime number theorem:
  - attempts at finding the average distribution of primes
  - density of the primes can be computed empirically
    - $A_n$ is the number of primes among the integers up to n
    - $A_n/n$ gives the density or average distribution
  - defining the natural logarithm of an integer n:
    - take two perpendicular axes in a plane and consider the locus of all points in the plane the product of whose distances x and y from the axes is equal to 1 (xy = 1)
    - this will define a hyperbola and the area under it is the log n
  - $A_n/n$ is approximately equal to $1/\log(n)$ as observed by Gauss
  - the approximation improves at larger n
  -  the proof to this theorem was obtained almost a hundred years afterwards
- unsolved problems concerning prime numbers:
  - Goldbach conjecture: any even number except for 2 (because it’s a prime) can be represented as the sum of two primes - how to prove this?
  - primes also frequently occur in pairs: p and p+2 - it’s possible that there are infinite such pairs but there is no proof 

### Congruences

- let’s examine the remainders after dividing a number by 5:
  - 0 => 0, 1 => 1, 2 => 2, 3 => 3, 4 => 4, 5 => 0, 6 => 1 etc
  - they $\in 0, 1,2,3,4$
- we say that two integers a and b are congruent modulo 5 if they leave the same remainder on division by 5 (e.g. 2, 7, 12, 17, 22, -3, -8, -13)
- we write $a \equiv b $ (mod $d$)
- congruences frequently occur in life - hands of a clock show the hour mod 12 and mileage indicator shows miles mod 10000
- statements about modulo congruence: “a is congruent to b modulo d” is equal to “a = b + nd for some n” is equal to “d divides a-b”
- congruence with respect to the same modulo has many of the properties of ordinary equality (e.g. if $a \equiv b$ (mod d) then $b \equiv a$ (mod d) or if $a \equiv b$ (mod d) and $b \equiv c$ (mod d) then $a \equiv c$ (mod d)
  - also, if $a \equiv a'$ and $b \equiv b'$ (mod d), then $a\pm b\equiv b'\pm a'$ and $ab \equiv a'b'$ (mod d)
- this concept also has a geometrical interpretation
- multiplicative property:
  - we can find remainders left when successive powers of 10 are divided by a given number, e.g. $10 \equiv -1$ (mod 11), $10^2 \equiv 1$, $10^3 \equiv -1$ etc
  - from this we can show that any integer expressed in the decimal system has the same remainder on division by 11 as the alternating sum of its digits (e.g. 1 + 2 - 3 + 4 - 5)
  - we can find similar rules for divisibility by other numbers, e.g. for 3 or 9
    - since $10 \equiv 1$ (mod 3 or 9) and it doesn’t alternate, a number is only divisible by 3 or 9 if the regular sum of its digits is
- when we add and multiply congruences with a fixed modulo, we can replace the number by a number from the set {0, 1, 2, 3, 4} with which it is congruent (given tables in the book)
  - we can see that a product ab is congruent to 0 mod 5 only if $a | b \equiv 0$ (mod 5) but this only holds for prime modulo
  - e.g. for the congruence $ab \equiv 0$ (mod d) means that d divides ab and a prime d divides a product ab only if it divides a or b, so only if $a \equiv 0$ or $b \equiv 0$ (mod d)
  - if d is not a prime the law doesn’t hold, we can write d = r*s where neither r nor s are congruent with modulo d but $rs = d \equiv 0$ (mod d)

### Fermat’s little theorem

- Fermat’s discovered that if p is any prime which does not divide integer a, then $a^{p-1}\equiv 1$ (mod p) (the p-1st power of a leaves the remainder 1 upon division by p)
  - e.g. $10^6 \equiv 1\mod 7$
  - from YT videos: this theorem can be used for large exponents too to find remainders
  - to prove this theorem, we consider multiples of a (e.g. $m_1=a, m_1 = 2a, m_2 = 3a, ..., m_{p-1}=(p-1)a$)
  - this is the rearrangement of congruence classes 1, 2, 3, .. , p-1
    - these are not congruent to 0, because if $r * a \equiv 0 \mod p$ then that would mean that p divides r*a (doesn’t divide a by the theorem and can’t divide r because r < p)
    - these are also not congruent to each other: pick two values, $r*a$ and $s*a$ 0, where < r < p and 0 < s < p
    - we want to show that $r*a \not\equiv s* a \mod {p}$ 
      - let’s look at $r*a - s*a=a*(r-s)$
      - p doesn’t divide a by assumption and p also can’t divide r - s because it is less than p (r - s is bounded between -p and p so it is not a multiple of p)
  - therefore, $a*2a*..*(p-1)\equiv 1*2*3...*(p-1) \mod{p}$ which can be rewritten as $(p-1)!*a^{p-1}\equiv (p-1)! \mod{p}$
  - p does not divide (p-1)! so we can cancel it out of the cogruence and get $a^{p-1}\equiv 1 \mod{p}$ 
  - QED

### Quadratic residues

- not only is $a^{p-1}\equiv 1 \mod{p}$ but if p is a prime different from 2  (of the form p = 2p’+1) for some values of a, $a^{(p-1)/2}\equiv 1 \mod{p}$
- we can write this as $a^{p-1}-1 = a^{2p'} -1 = (a^{p'}-1)(a^{p'}+1)\equiv 0 \mod{p}$
- either $(a^{p'}-1)$ or  $(a^{p'}+1)$ must be divisible by p, so for any prime number p > 2 and any number a not divisible by p we will have $a^{(p-1)/2}\equiv 1 \mod{p}$ or $a^{(p-1)/2}\equiv -1 \mod{p}$
- suppose a is congruent modulo p to the square of some number x $a \equiv x^2 \mod{p}$
- then $a^{(p-1)/2}\equiv x^{p-1} \mod p$ which will be congruent to 1 mod p according to the theorem above
- a number $a$, not a multiple of $p$, which is congruent modulo $p$ to the square of some number is called a quadratic residue of p while a number $b$, not a multiple of $p$ which is not congruent to a square is called a quadratic non-residue
  - every quadratic residue satisfies $a^{(p-1)/2}\equiv 1$ while a non-residue satisfies $b^{(p-1)/2}\equiv -1 \mod{p}$
  - (so if a number $a$ (that is not equal to 2p or 3p etc) which has the same remainder as $x^2$ when it is divided by p will leave a remainder 1 when raised to (p-1)/2 divided by p)
- what is the distribution of quadratic residues?
  - choose p = 7
  - $0^2\equiv 0, 1^2 \equiv 1, 2^2 \equiv 4, 3^2 \equiv 2, 4^2 \equiv 2, 5^2 \equiv 4, 6^2 \equiv 1 \mod{p}$
  - quadratic residues of 7 are numbers congruent to 1, 2 or 4 while non-residues are congruent to 3, 5 or 6 (because 1, 2 and 4 are what you get when you divide squared numbers by 7 and take the remainder, but 3, 5 and 6 don’t occur there)
  - half the numbers from 1 to p-1 will be quadratic residues and half won’t

### Pythagorean numbers and Fermat’s last theorem

- a triangle with sides 3, 4, 5 is a right triangle
- what other right triangles have sides whose lengths are integral multiples of a unit length?
- Pythagorean theorem: $a^2+b^2=c^2$
  - if a, b and c form a Pythagorean number triple then we put $a/c=x$ and $b/c = y$, where x and y are rational numbers for which $x^2+y^2=1$, then 
  - $y^2 = (1-x)(1+x)$ =
  - = $y/(1+x)=(1-x)/y$ 
  - we can write the common value between these as t = u/v, so $y(1+x)=t$ and $(1-x)/y=t$
  - out of $y/(1+x) = t\to y = t(1+x)$ and $(1-x)/y=t \to (1-x)=ty$ by multiplying the first one by (1+x) and the second one by y
  - we can rewrite these as $x = 1-t^2/1+t^2$ and $y = 2t/y+t^2$ by rearranging stuff and plugging in
  - then, since t = u/v, x = a/c and y = b/c we can substitute:
    - $a/c = \frac{v^2-u^2}{v^2+u^2}$
    - $b/c=\frac{2uv}{u^2+v^2}$
    - we can obtain a, b and c from there
    - $a = (v^2-u^2)r$, $b = (2uv)r$, $c = (u^2+v^2)r$ for some factor r
  - for a primitive pythagorean triple (distinct and not just a factor scaling), we remove the factor r from the equations above
- This raises the question: can we find $a^3+b^3=c^3$ and so on for n>2?
  - Fermat’s theorem has been proven for n < 619 but not for all n

### The Euclidian Algorithm

- General theorem of division: if a is any integer and b is any integer greater than 0, then we can always find an integer q such that $a = bq+r$, where $0 \leq r <b$
- Proof: any integer a is either a multiple of b (a = bq), or lies between two successive multiples of b: $bq < a < b(q+1) = bq+b$
  - in the first case, r = 0, in the second $a - bq = r > 0$ and $a - bq = r < b$
- A method for finding the greatest common divisor:
  - let a and b be any two integers, not both equal to 0 and consider the set of all positive integers which divide both a and b, of which d is the largest (e.g. for a = 8 and b = 12, d = 4, written as (8,12)=4)
  - from any relation of the form a = bq+r => (a,b)=(b,r), since any number u that divides both a and b (a = su and b = tu) will also divide r, since $r = a - bq = su - qtu = u(s - qt)$, so every common divisor of a and b is a common divisor of b and r => greatest common divisor of a and b must be equal to the greatest common divisor of b and r
  - e.g. find the greatest common divisor of 1804 and 328:
    - 1804 = 5*328 + 164
    - (1804, 328) = (328, 164)
    - continue the process:
      - 328 = 2*164+0, so (328,164)=(164,0)=164 (which is the answer for 1804 and 328)
    - this will be completed after at most b steps
- Exercise: do the same for (187, 77) = 11, (105, 385) = 1, (245, 193) = 1
- Property of (a,b) - if d = (a,b), then positive or negative integers k and l can be found s.t. d = ka + lb
  - Consider a sequence of successive remainders: $r_1=a-q_1b$, where $r_1$ can be written as $k_1a+l_1b$ where $k = 1$, $l = -q_1$
  - then $r_2 = b - q_2r_1 = b-q_2(k_1a+l_1b)=(-q_2k_1)a+(1-q_2l_1)b=k_2a+l_2b$
  - we can repeat this until we arrive at ka+lb
  - e.g. (61,24)=1 => $-11*61+28*24$
- Application to the Fundamental Theorem of Arithmetic
  - (theorem: every integer greater than 1 can be factored into a product of primes in only one way)
  - first, prove a lemma and then deduce the theorem from it
  - Lemma: if a prime p divides a product $a*b$, then p must divide a or b
    - if a prime p does not divide a, then (a,p)=1, so we can find integers k and l such that 1 = ka + lp
    - multiply by b to get b = kab+lpb
    - if p divides ab, we can write ab = pr
    - b = kpr+lpb = p(kr+lb)
  - Suppose we have two decompositions of a positive integer N into primes: $N = p_1p_2...p_r=q_1q_2....q_k$
    - since p1 divides the left side, it must also divide the right and must divide one of the factors $q_k$ and since it is a prime, $p_1$ must be equal to $q_k$
    - we can similarly remove all p and qs from the equation pairwise and show that the two decompositions were identical

### Euler’s $\phi$ function

- two integers a and b are said to be relatively prime if their greatest common divisor is 1: (a,b)=1
- if a and b are relatively prime, we can write ka+lb=1
- for any positive integer n, let $\phi(n)$ denote the number of integers from 1 to n that are relatively prime to n
- $\phi(p)=p-1$ if p is a prime
  - if n is composite with a prime decomposition then $\phi(n)=n(1-1/p_1)*(1-1/p_2)...(1-1/p_r)$

### Continued fractions and diophantine equations

- The Euclidian algorithm can also help us represent the quotient of two integers as a composite fraction:
  - e.g. (840,611)=1
  - $840/611 = 1+229/611 = 1+ 1/[611/229]$
  - we can continue this algorithm by decomposing the resulting fraction
  - and can therefore represent the rational number 840/611 as a *continued fraction*:
    - $\frac{840}{611}=1+\frac{1}{2+\frac{1}{1+\frac{1}{2+\frac{1}{76}}}}$
- Continued fractions are important to Diophantine analysis
  - A Diophantine equation is an algebraic equation in one and more unknowns, simplest case ax + by = c
  - we can decompose this equation using the Euclidian algorithm, it has an integer solution if and only if c is a multiple of (a,b)

## Chapter 2: The number system of mathematics

- The number system has developed from only natural numbers to 0, negative integers, fractions and so on

### The rational numbers

- The integers are abstractions for counting objects, but we also need to measure quantities (e.g. length)
- We reduce the problem of measuring to the problem of counting by selecting a unit of measurement (e.g. kg or inch) and count the number of these
- But the number may not be round, so we introduce sub-units obtained by dividing the original unit into n parts
  - e.g. 1 meter = 100 centimeters
  - in mathematics, this is denoted by a fraction e.g. m/n (a rational number)
  - addition and multiplication of rational numbers obey the same laws as natural numbers do (commutative, associative, distributive laws)
- negative integers were introduced to remove subtraction restrictions
- fractional numbers remove division restrictions
- division by 0 is not permitted, but can sometimes be denoted by $\inf$
- rational operations (addition, subtraction, multiplication, division) can be perfomed freely in the domain of rational numbers - this closed domain is also called a field
- extending a domain by introducing new symbols in a way that the laws continue to hold is called generalization 
- rational numbers have a geometrical interpretation on the number axis
  - within each interval, no matter how small, there are rational points

### Irrational numbers, decimal fractions and limits

- if we want to compare two line segments a and b, we may find that $b = r*a$ (so both are integers), or that a can be divided into n pieces and that m of them are in b, $b = m/n*a$
  - when this holds, the two segments are *commensurable*, since they have a common measure a/n
  - e.g. if we choose [0, 1], then all rational points m/n will be commensurable with it
  - for all practical purposes, the rational numbers are sufficient and they densely cover the number line
  - but the Pythagoreans found that there are incommensurable segments of the number line (or irrational numbers)
- the diagonal of a square is incommensurable with its side
- Proof: side of a given square is unit length and the diagonal has length x
  - $x^2 = 2$
  - $x = \sqrt2$
  - if x were commensurable with 1, we could find two integers such that $x = p/q$ (*1) and p and q would have no common factors
  - $\sqrt2=\frac{p}{q}$, multiply by q and square both sides
  - $2q^2=p^2$
  - since 2 is a factor, p^2 must be even (any number *2 is even) and p itself must be even too (squares of odd numbers are odd)
  - $p = 2r$ (p is some even number that has 2 as a factor)
  - $4r^2=2q^2$ => $2r^2 = q^2$
  - since 2 is a factor, q must be even (same as above), but if p and q are both even, they must have a common factor of 2, so the equation $p^2=2q^2$ cannot hold (so $\sqrt2 \not= p/q$)
- the system of rational points does not cover all of the number axis
- prove that 3rd root of 2 is irrational:
  - if $2^{1/3}$ was rational, it could be expressed as p/q
  - $2^{1/3}=p/q$ multiply by q and cube
  - $2q^3=p^3$
  - $p^3$ must be even and so must p
  - $p = 2k$
  - $2q^3 = 8k^3$
  - $q^3 = 4k^3$
  - therefore q is also even and they must have a common factor of 2
- numbers that originate by subdivision of each unit into 10, then 100 etc
  - 0.12 = 1/10 + 2/100
- decimal fractions are of the form $f = z + a_110^{-1}+a_210^{-2}...$
  - this can be written in the form of ordinary fractions too
  - and can be reduced, e.g. $1/5 = 2/10 = 0.2$ 
- let us choose any point which does not correspond to a decimal fraction, e.g. $\sqrt2$
  - it cannot be fully expressed, but can be approximated by intervals, e.g. we can first find that it’s between 0.2 and 0.3, then between 0.230 and 0.231
  - some fractions extend indefinitely, e.g. 1/3 = 0.333 ...
  - $\sqrt2$ also leads to an indefinitely extended decimal fraction
    - but we don’t know how to derive the digits outside of explicit calculation
- so sometimes a rational number s is approximated by a sequence of other rational numbers, e.g. 0.3, 0.33, 0.333 ad so on
- we can divide the unit interval into two halves, then again, again and so on until the smallest interval is equal to $1/2^n$
  - $s_n = 1/2+1/4+1/8+1/16...+1/2^n$
  - the difference between s and the unit interval will tend to zero as n increases
  - the sum s approaches the limit 1 as n tends to infinity ($s_n \to 1$ as $n \to \infty$)
- if we consider a number q ($-1 < q < 1$), then successive powers of q will approach 0 as n increases
  - if q is negative, the sign will alternate
  - if |q|>1, then it will increase in magnitude without limit
  - proof of this assertion:
    - $(1+p)^n \geq 1+np$  for any positive integer n and p > -1
    - if q is a fixed number between 0 and 1, then q = 1/(1+p) where  p > 0 => $1/q^n = (1+p)^n \geq 1 + np > np$
- we can consider a geometrical series $s_n = 1+q+q^2+q^3...$ and we can express this in a concise form
  - $qs_n = q+q^2+q^3...q^{n+1}$
  - subtract the original form from this and this will cancel out all but the first and last terms:
    - $s_n - qs_n = 1 - q^{n+1}$
    - $s_n(1-q)=1-q^{n+1}$
    - $s_n = \frac{1-q^{n+1}}{1-q}$
    - so $s_n$ will tend towards this as $n \to \infty$
- Exercise: prove that $s_n = 1-q+q^2-q^3+q^4...q^n = 1/(1+q)$ if $|q|<1$
  - multiply each term by q
  - $qs_n = q - q^2 + q^3 ...q^{n+1}$
  - $qs_n + s_n = 1 + q^{n+1}$
  - $s_n(q+1)=1+q^{n+1}$
  - $s_n = \frac{1+q^{n+1}}{q+1}$
  - if |q| is less than 1, $q^{n+1}$ will tend to 0
  - => $s_n \to \frac{1}{1+q}$
- rational numbers p/q that are not finite decimal fractions can be expanded into infinite decimal fractions by long division (as long as there’s a non-zero remainder)
  - the decimal expression of any rational number is periodic (same digits repeat infinitely)
  - we can also show that all periodic decimals are rational numbers
- the continuum of numbers is the totality of infinite decimals
  - but this is attached to the decimal system and we can have a more broad definition
  - consider a sequence of intervals on the number axis with rational end points, each of which is contained in the preceding one such that the length of the nth interval tends to zero as n increases (sequence of nested intervals)
  - basic postulate: each sequence of nested intervals has precisely one point on the number axis that is contained in all of them
  - even an irrational point will be completely described by a sequence of nested rational intervals with lengths tending to zero
- the only relevant existence of mathematical objects lies in their mathematical properties and interconnections, there is no “thing in itself”
  - these irrational numbers also follow the laws of the field of the rational numbers (addition, multiplication etc)
- alternative way of defining irrational numbers:
  - Dedekind - preferred abstract ideas
  - suppose that we can divide the set of all rational numbers into classes A and B such that every element of B > every element of A (this is called a cut)
    - three possibilities exist: that there is a largest element of A (e.g. if $A \in \mathbb{Q} \leq 1$ (rational numbers < 1) and if $B \in \mathbb{Q} > 1)$, that there is a smallest element of B (e.g. if $A \in \mathbb{Q} < 1$ and $B \in \mathbb{Q} \geq 1$) and there is neither (if A has all negative rational numbers, 0 and all positive rational numbers of square less than 2 and B all the others)
  - the case in which A has a largest element and B has a smallest element is impossible because the rational number $(a^*+b^*)/2$ would be between these two and would be larger than a* and smaller than b*
  - the third case implies an irrational number

### Analytic geometry

- the number continuum is the basics of mathematics
  - we can associate each line segment with a real number (through its length)
  - but we can also refer every geometrical object and operation to the realm of numbers
- fundamental idea - coordinates (e.g. rectangular/Cartesian)
  - we have fixed perpendicular lines, the x- and y-axes (regarded as directed number axes)
  - the plane can be separated into counterclockwise quadrants:
    - <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Cartesian_coordinates_2D.svg/259px-Cartesian_coordinates_2D.svg.png" alt="img"  />
- we can plot various objects/functions on the coordinate plane
  - the distance between two points is given by the formula $d^2 = (x_1-x_2)^2 + (y_1-y_2)^2$, which follows from the Pythagorean theorem
  - equation for a circle with coordinates x = a, y = b
    - $(x-a)^2+(y-b)^2 = r^2$
    - Or, expanded: $x^2+y^2-2ax-2by=r^2-a^2-b^2$
  - equations of straight lines:
    - x-axis: y = 0
    - y-axis: x = 0
    - bisecting the angles between axes: x = y, x = -y
    - any straight line: ax + by = c
  - Ellipse: $\frac{x^2}{p^2}+\frac{y^2}{q^2}=1$
  - Hyperbola:  $\frac{x^2}{p^2}-\frac{y^2}{q^2}=1$
    - asymptotes at $qx \pm py=0$
    - equilateral hyperbola (area of the rectangle determined by P is equal to 1 for every point): $xy = c$
- intersections between lines:
  - determined by the solution to the simultaneous equations
    - $ax+by=c$ and $a'x+b'y=c'$

### Analysis of infinity

- sequence of positive integers 1,2,3... is an infinite set
- infinitiy is not an ordinary number!
- mathematical objects are usually studied as members of classes or aggregates containing infinitely many objects, e.g. integers, real numbers or triangles in a plane
- Georg Cantor - theory of sets
  - a set or aggregate: any collection of objects defined by some rule that specifies which objects belong to it
    - e.g. all positive integers, all periodic decimals, all real numbers
  - equivalence: if elements in two sets A and B may be paired with each other one-to-one, then it’s a *biunique* correspondence and the sets are equivalent
    - two sets will have biunique correspondence if they have the same number of elements (for finite sets) - basically counting is establishing equivalence of some set with real numbers 1,2,3,...,n
  - Idea: extend the concept of equivalence to infinite sets -> arithmetic of infinities
    - set of all real numbers and set of all points on a straight line are equivalent
    - even integers are a subset of all integers
    - integers are a subset of rational numbers
    - if a set is finite, it cannot be equivalent to one of its subsets (because a subset has at most n-1 elements)
      - but if a set is infinite, then it may be equivalent to a subset of itself (e.g. positive integers and even integers)
- Cantor discovered that the set of rational numbers (infinite set of integers as a subset) is equivalent to the set of integers
  - although we cannot arrange rational numbers in magnitude (there is an infinite amount of rational numbers between any two given ones), we can still arrange them in some sequence ($r_1,r_2,r_3...$) - this is called a denumeration of the set
  - denumerating rational numbers: we can write any rational number as a/b and can put them in an array, where a/b is in ath column and bth row. in this array we can draw a continuous line that goes through all of them
  - **but** the set of all real numbers is **not denumerable**, i.e. this is a “different” type of infinity
    - assume that all real numbers have been denumerated, and then show a number that has not been denumerated
    - arrange in a table and go down the table, constructing a new rational number
    - ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Diagonal_argument_01_svg.svg/177px-Diagonal_argument_01_svg.svg.png)
  - we can establish a biunique correspondence between any finite segment of the number line (straight or bent)
- the number of elements in a finite set A cannot equal the number of elements in a finite set B if A has more elements than B
  - but this does not hold for infinite sets, e.g. the set of all integers has more elements than the set of even integers, but these sets are equivalent
  - there are at least two different types of infinity, the denumerable infinity of the integers and the non-denumerable infinity of the real number continuum
  - if two sets are equivalent, they have the same cardinal number
- indirect proofs: to establish the truth of statement A, we assume that A’, the contrary of A, is true, then we show a contradiction to A’ and establish the truth of A
  - indirect proofs are *non-constructive*
  - there’s a difference between proving the existence of A by constructing an example and proving it by showing that if it didn’t exist, a contradictory result would be obtained
- unrestricted freedom in using the concept of set must lead to contradiction
  - a paradox by Russell: most sets do not contain themselves as elements (called ordinary), but some sets may contain themselves (e.g. a set S - contains elements of all sets definable by an English phrase of less than 20 words, called *extraordinary*)
  - set of all ordinary sets C - is it ordinary or extraordinary?
- field of mathematical logic - providing a logical basis for math without contradiction
  - many problems in this field are simple to state, but not simple to solve, e.g. hypothesis of the continuum (there is no set whose cardinal number is greater than the cardinal number of the set of integers but less than the set of real numbers)
  - what does mathematical existence mean? Hilbert asserts that it means freedom from contradiction
  - but even the most formalistic attempts or structures are partially based on intuition

### Complex numbers 

- all the new developments in math are products of a gradual and hesitant evolution
  - usually because a need arises for an extension
- complex numbers first became required for quadratic equations
  - e.g. $x^2=2$ has no solution in the rational numbers
  - $x^2 = -1$ has no real solution
    - we can just conclude that it’s not solvable, or extend our concept of numbers by introducing *imaginary* numbers
    - $i^2 = -1$
    - to extend the real numbers, we define a complex number $a+bi$, where a and b are any two real numbers and the commutative, associative and distributive laws hold for them (as well as subtraction and division, which means that they form a *field*)
    - the field of complex numbers includes the field of real numbers as a subfield
    - ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Complex_conjugate_picture.svg/300px-Complex_conjugate_picture.svg.png)
  - $0+bi$ is a pure imaginary number
- Exercise:
  - express $\frac{(1+i)(2+i)(3+i)}{1-i}$ as a + bi = -5+5i
- we have extended the field of real numbers to a field of a+bi, where $x^2=-1$ has two solutions $x=i$ and $x=-i$
  - now every quadratic equation has a solution (real or complex)
- Geometric interpretation:
  - at first, imaginary numbers weren’t very intuitive or obvious
  - we represent a complex number $z = x+yi$ by the point in the plane with coordinates x,y (where the real part is the x coordinate and the imaginary part is the y coordinate)
  - distance from the point z to the origin is $p^2 = x^2+y^2 = (x+yi)(x-yi)=z*\bar z$
    - this distance is called the modulus $|z| = \sqrt{x^2+y^2}$
    - the modulus of the product if two complex numbers is equal to the product of their moduli
      - $|z_1*z_2|=|z_1|*|z_2|$
  - the sum of two complex numbers (e.g. two points / vectors in the complex plane) is $z_1+z_2 = (x_1+x_2)+(y_1+y_2)i$
    - we can also deduce that the modulus of the sum of two complex numbers is less than or equal to their moduli 
    - $|z_1+z_2|\leq|z_1|+|z_2|$
      - because the length of any side of a triangle cannot exceed the sum of the lengths of the other two sides
  - the angle between the x-axis and the line from the origin to Z is called $\phi$, the angle of z
    - the angle is not uniquely determined since we can add or subtract any multiple of 360 degrees (e.g. $\phi, \phi\pm360^\circ,\phi\pm720^\circ$)
    - since we have the modulus and the angle, we can write the number as $z = x+yi = p(\cos\phi+i\sin\phi)$
    - because $x = p\cos\phi$ and $y = p\sin\phi$
  - this is useful when we’re multiplying numbers, because using some fundamental theorems we can deduce that $zz' = pp'[\cos(\phi+\phi')+i\sin(\phi+\phi')]$ 
    - we add the angles, so this has something to do with rotation
    - this is important when z = z’, because $z^2 = p^2(\cos2\phi+i\sin2\phi)$, if we multiply again we get $z^3 = p^3(\cos3\phi+i\sin3\phi)$
    - or, generally, $z^n = p^n(\cos n\phi+i\sin n\phi)$ for any integer n
    - if z is a point on the unit circle, then p = 1 and $(\cos \phi + i\sin\phi)^n=\cos n\phi+i\sin n\phi$
- nth root = number b such that $b^n=a$
  - the number 1 has two square roots (-1 and 1), but only one cube root and four fourth roots (1, -1, i, -i)
    - $i^4=1$ because we have $i^2=-1$ and $(i^2)^2=1$
  - there may be more third roots of 1: 3 in total
    - if we draw a regular n-sided polygon, the vertices will represent the n nth roots of 1
    - from the formula above, $(\alpha^2)^n = \cos(n*720^\circ/n)+i\sin(n*720^\circ/n)=1+0i=1$
    - if n is even, then one of the vertices will lie at the point -1
  - the equation satisfied by the nth roots of n is $x^n-1=0$
  - but we can reduce it: $x^n-1=(x-1)(x^{n-1}+x^{n-2}+...+1)$
- **nth roots of 1 will be vertices of an n-shaped polygon in the complex plane!!**
- ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/4/40/One5Root.svg/480px-One5Root.svg.png)
- the equation that is satisfied by the roots is called the cyclotomic equation (circle-dividing)
  - the complex cube roots of 1: 
    - 1) $\alpha = \cos120^\circ+i\sin120^\circ = 1/2(-1+i\sqrt3)$
      2) $\alpha^2 = \cos240^\circ+i\sin240^\circ = 1/2(-1-i\sqrt3)$
    - are roots of the equation $x^2+x+1=0$
  - the fifth roots of 1 will satisfy the equstion $x^4+x^3+x^2+x+1=0$
- fundamental theorem of algebra: every algebraic equation of any degree n with real or complex coefficients has solutions in the field of complex numbers
  - proven in the 16th century for degrees 3 and 4, degree 5 shown by Gauss
  - every polynomial of degree n can be factored into the product of factors ($f(x)=x^n+a_{n-1}x^{n-1}..=(x-\alpha_1)(x-\alpha_2)$) where alphas will be the complex numbers and the roots of the equation  $f(x)=0$

### Algebraic and transcedental numbers

- definition: an algebraic number is any number x that satisfies an equation of the form $a_nx^n+a_{n-1}x^{n-1}+...+a_1x+a_0=0$ where $n \geq 1, a_n \not=0$
  - e.g. $\sqrt2$ is an algebraic number
  - not every real number is algebraic (Cantor proved that the set of algebraic numbers is denumerable, whereas the set of all real numbers is non-denumerable)
  - a method for enumerating: each equation of the form above can be assigned a ‘height’ ($h = |a_n|+|a_{n-1}|+...+|a_1|+|a_0|+n$), and any fixed value of h has a finite number of equations for this height
  - we can arrange all the algebraic numbers in a sequence starting with those of height 1, then 2 etc
- non-algebraic numbers are transcedental
  - a proof of their existence was given by J. Liouville, which also permits the construction of examples of such numbers
  - he showed that irrational algebraic numbers are those which cannot be approximated by rational numbers with a very high degree of accuracy unless the denominators of the approximating fractions are quite large
    - suppose z satisfies an algebraic equation $f(x)=a_0+a_1x+a_2x^2..=0$, but not an equation of lower degree
    - then z is an algebraic number of degree n (e.g. $\sqrt2$ is an algebraic number of degree 2)
    - an algebraic number of degree n > 1 cannot be rational, since a rational number $z = p/q$ satisfies the equation $qx-p=0$ of degree 1
    - each irrational number z can be approximated by a rational number
    - Liouville’s theorem assers that for any algebraic number of degree n>1 such an approximation must be less accurate than $1/q^{n+1}$
- Hilbert problems: a set of 30 problems postulated in 1900, each of which was easy to formulate but has not been solved
  - one of the problems was to prove that $2^\sqrt2$ is a transcedental number

### Algebra of sets

- the concept of a class or set is fundamental to mathematics
  - a set is defined by any property or attribute $\mathfrak{A}$ which each object must possess to be in the set
  - e.g. if we consider the integers and the property is being a prime, the set is the set of all primes
- sets may be combined by certain operations to form other sets (algebra of sets)
- $I$ denotes a fixed set of objects of ny nature and $A,B,C..$ will denote subsets of $I$
  - also included is the empty set $O$ which contains no elements
  - this is done to preserve the rule that a subset A corresponds to each property $\mathfrak{A}$, but if $\mathfrak{A}$ is some universally valid property (e.g. $x=x$), the corresponding subset of I will be I, but if $\mathfrak{A}$ is contradictory ($x \not=x$), then the subset will be empty
- the set A is a subset of B if there is no object in A that’s not also in B ($A \sub B$)
  - if $A \subset B$ and $B \subset A$, then they are equal
  - if A has 1,2,3 and B has 2,3,4, then neither are subsets of each other
  - $O \subset A$ for any set A
- operations on sets have many algebraic properties, e.g. they can be added or multiplied (intersection of sets)
  - these are commutative, associative and distributive
  - except for $A + A = A$, $AA = A$ and $A + BC = (A+B)(A+C)$
    - one of the consequences is that the binomial theorem for sets is simpler, $(A+B)^n = A+B$
- complement - the opposite of a set, e.g. all objects that are not in set A ($A+A'=I$)
- ![img](https://miro.medium.com/max/551/1*0-uuOWttzdqiZdzr6p4G4A.png)
- applications in logic:
  - these rules can be translated to logic:
    - both A and B = AB
    - either A or B = A+B
    - not A = A’
    - neither A nor B = (A+B)’
    - not both A and B = A’ + B’
    - some A are B = $AB \not= O$
    - no A are B = $AB = O$
    - no A = $A = O $
  - all the theorems and statements can be deduced from the following:
    - $A + B = B + A$
    - $(A+B)+C = A + (B+C)$
    - $(A'+B')'+(A'+B)'=A$
  - systems that satisfy these laws are studied in Boolean algebra
- applications in probability:
  - if all outcomes of an experiement are I and A is a subset of I, then the probability that the outcome will be in A is $p(A)=n(A)/n(I)$ where n is the number of elements
  - we can use the formula to calculate different probabilities: $p(A+B)=p(A)+p(B)-p(AB)$

## Chapter 3: Geometrical constructions and the algebra of number fields

### Introduction

- construction problems are popular in geometry

- e.g. bisect a line segment, inscribe a hexagon in a circle etc

- a famous problem - contact problem of Apollonius, three arbitrary circles are given and a fourth circle tangent to all three is required
  - even if one of the given circles has radius zero (is a point) or infinity (is a straight line)
- constructing a regular polygon of n sides is also an important problem  - we know how to do this for n = 3, 4, 5, 6
  - for n = 7, it’s impossible
- other classical problems: trisecting an arbitrary angle, doubling a cube and squaring a circle
- how do we prove that some problems are unsolvable?
- solving equations of degree 5 and above led to a new way of thinking
  - equations of degree 3 or 4 can be solved by a method similar to that for solving quadratic equations (solutions/roots can be written as algebraic expressions obtained from the coefficients, e.g. as in the quadratic formula, particularly using only +,-,*,/ and roots
  - but extending this for roots >= 5 proved impossible
    - Gauss has shown that the solution exists, but the problem was figuring out whether it could be found by means of rational operations and radicals alone
- proving the impossibility of certain geometrical constructions is an example of this trend
- the question to start with: how can all constructive problems be completely characterized?
- Gauss investigated the ability to construct polygons with prime number of sides (p-gon)
  - a p-gon is constructible if and only if p is a Fermat number ($p = 2^{2n}+1$)
  - the problem is not drawing a figure, it’s being able to find it theoretically using only a ruler and a compass (e.g. there are other ways to solve this and if we allow other tools, e.g. a right angle etc the problems may also be easily solvable)

### Fundamental geometrical constructions

- any geometrical construction problem has the form: a set of line segments is given and one or more other segments are sought
  - e.g. required segments may be sides of a triangle or radii of circles
  - the geometrical construction becomes an algebraic problem: we must find an equation between the required quantity x and the given quantities, then we must solve the equation and determine whether this solution can be obtained by processes that correspond to ruler and compass constructions
  - the principle of analytic geometry (characterization of geometrical objects by real numbers) provides the foundation
- some of the simplest algebraic operations correspond to elementary geometrical constructions
  - e.g. if we are given line segments a and b, we can construct a+b, a-b, ra, a/b and ab
    - we can use rules of triangles etc
- from any given segments measured by real numbers we can construct any quantity that is expressible in terms of a, b, c
  - the totality of quantities that can be obtained in this way is **a number field** - a set of number s.t. any rational operations applied to two or more members of the set yield a member of the set
  - but there is a construction that carries us beyond the field - square root of a (we can mark off a segment a (OA) and a unit segment (AB) and draw a circle with OB as diameter, then we make a perpendicular to OB through A which will meet the circle in C, x = AC = $\sqrt a$)

### Regular polygons

- we can also consider polygon construction problems:
  - decagon (10-gon) - a side of x and an angle of 36 degrees - the other two angles will be 72 ((180-36)/2) and we can divide the radius by constructing this triangle - the big triangle will be similar to the smaller one, so $1/x = x/(1-x) \to x^2/(1-x)=1 \to x^2 = 1-x \to x^2 + x - 1 = 0$, the solution to which is equal to $(\sqrt5-1)/2$
  - since the solution can be expressed algebraically, it can be constructed geometrically - we mark off x ten times
  - ![img](https://qph.fs.quoracdn.net/main-qimg-08354dcbf941182fe8651996a8806fdb)

### Apollonius’ problem:

- we can construct equations for the three given circles 
- to make a new circle tangent, we observe that the distance between the centers of two tangent circles is equal to the sum or difference of the radii (depending if they touch from inside or outside)
- if $x_1,y_1,r_1$ denote given circle 1 and so on and $x,y,r$ denote our required circle, the equations are of the following form:
  - $(x-x_1)^2 + (y-y_1)^2 - (r \pm r_1) = 0$
- we can get a linear equation in x, y, r from subtracting the equation for circle 2 from 1 or 3 from 1
- then we solve and get a quadratic equation in r (which can be solved by rational operations and the extraction of a square root)
- => we can do this by ruler and compass alone
- there can be 8 solutions (8 combinations of + and - signs)
- ![img](https://mathworld.wolfram.com/images/eps-gif/ApolloniusCircles8_950.gif)

### Constructible numbers and number fields

- every construction has the following possible steps: connecting two points, finding the point of intersection of two lines, drawing a circle with a given radius about a point, finding the points of intersection of a circle with another circle or a line
- sometimes we draw arbitrary elements - e.g. midpoints can be found by drawing two equal circles of arbitrary radius from each point of a line and then the segment will be at the intersection
- we assume that we only get unit length 1 at the outset
  - therefore, we can construct by ruler and compass all numbers that can be obtained from unity by +,-,*,/ (all numbers r/s)
  - the system or rational numbers is closed with respect to the rational operations (a field)
- starting from the unit, we can construct the whole rational number field - and also $\sqrt2$, from where we can obtain all numbers of the form $a+b\sqrt2$
  - these numbers also form a field (a subfield of the rational field)
  - let’s call this new field $F_1$ - we established that every number in it is constructible, but we may now extract the square root from it, e.g. $\sqrt k = \sqrt{a+b\sqrt2}$
    - and the field consisting of $p+q\sqrt k$, same as how we did from $\sqrt2$
- if we are able to construct all the numbers of some number field F, we can never go beyond the field by ruler alone (only by using the compass)
  - conversely, with a compass we may only obtain numbers of the form $p+q\sqrt k$ fur to the formula for the circle

- **all constructible numbers are algebraic** - numbers of field $F_1$ are roots of quadratic equations and so on

### The three greek problems

- doubling the cube: if we have a cube with edge of unit length, the volume will be the cubic unit - if we want to find the edge x of a cube with twice the volume, it will have to satisfy $x^3 - 2 = 0$
  - since the third root of 2 is an irrational number, we cannot obtain it by construction
- the other problems also depend on cubic equations
  - $z^3+az^2+bz+c=0$
  - $x_1+x_2+x^3 = -a$ (a fundamental property, obtained by factoring)
  - if a cubic equation with rational coefficients has no rational root, then none of its roots is constructible starting from the rational field
- trisecting the angle: consider an angle $\theta$ given by its cosine $\cos\theta=g$, then we need to find $x = \cos(\theta/3)$
  - $\cos(\theta)=4\cos(\theta/3)-3\cos(\theta/3)$
  - or the equation $4z^3-3z-g=0$
    - this equation has no rational root
- side x of a regular heptagon inscribed in the unit circle
  - vertices are given by $z^7-1=0$
  - one root is z = 1, others are given by factoring
    - $\frac{z^7-1}{z-1}=z^6+z^5+z^4...+1=0$
    - if we divide this by $z^3$, we get $z^3+1/z^3+z^2+1/z^2...$
    - then we can combine like terms $(z+1/z)^3-3(z+1/z)+(z+1/z)^2...$
    - if we denote $y = z+1/z$, then the equation is $y^3+y^2-2y-1=0$
    - if we use the formula $z = \cos\phi+i\sin\phi$ and $1/z = \cos\phi - i\sin\phi$ we know that $y = 2\cos\phi$
    - if we prove that y is not constructible, we will show that z and the heptagon are not constructible
    - the equation with y has no rational roots
- squaring the circle:
  - a circle with radius r has the area $\pi r^2$, so we have to be able to construct a segment of length $r\sqrt{\pi}$
  - $\pi$ is not constructible

### Geometrical transformations and inversion

- now, let’s look at transformations - this isn’t just restricted to construction problems, but also affects everything in geometry
  - one type of transformation: inversion of the plane in a circle (generalization of reflection)
  - transformation or mapping of a plane onto itself means a rule that assigns to every point P of the plane another point P’, called the *image* under the transformation (P is called the antedecent)
    - e.g. reflection: a point on one side of a line L has as its image the point P’ on the other side, with L being perpendicular to PP’
  - other examples of transformations are rotations of the plane about a point O, translations (moving every point a distance d in a given direction) and other rigid motions (combinations of rotations and translations)
- inverstions with respect to circles are also known as circular reflections (representing the approximate relation between original and image in reflection by a circular mirror)
  - ![img](https://mathworld.wolfram.com/images/eps-gif/InversePoints_701.gif)
  - let C be a given circle with center O and radius r
  - the image of a point P is defined to be the point P’ lying on the line OP on the same side of O as P s.t. $OP*OP'=r^2$
    - these inversions are interchangeable
  - there is no image for the center O - if a point approaches O, the image will recede farther, so O corresponds to infinity under inversion
  - this inversion maps points on the outside of a circle to inside a circle and vice versa
    - points on the circle remain fixed
- after an inversion, a line through O stays through O, a line not through O becomes a circle through O, a circle through O becomes a line not through O and a circle not through O stays a circle not through O
- the point P’ inverse to a given point P with respect to a circle C may be constructed using a compass alone
  - if we know how to to this, we can now bisect a segment and find the center of a circle

### Construction with other tools

- we can double the cube with a right angle ruler
- Mascheroni discovered that if you can make a construction using a straight-edge and compass, you can make it using only a compass

- if we can draw the hyperbolas $xy=k$ and parabolas $y=ax^2+bx+c$, then we can solve any problem that leads to a cubic equation of the form $ax^3+bx^2+cx=k$
- cycloids - one type of curve drawn by a simple instrument, described by a fixed point on a circumference of a circle rolling around (looks like a series of arches)
  - we can obtain a figure by allowing a circle to roll on another circle or choose different points
- the simplest instrument for tracing curves is linkages (a set of rigid rods) - e.g. a compass has two rods with one linkage

### Applications of inversions:

- inversion in a circle changes the appearance of geometrical figures but not all their properties, some remain invariant under the transformation (e.g. angle between two lines or curves)
  - tangent circles are transformed into parallel lines
- repeated reflections: if four walls of a rectangular room are covered with ideal non-absorbing mirrors, a lighted point would have infinitely many images
  - these can be described if the mirrors are located in triangles
  - if we stand between two concentric circular mirrors, we would see an infinite number of other circles concentric with them

## Chapter 4: Projective geometry, axiomatics, non-Euclidean geometries

### Classification of geometrical properties

- geometry deals with properties of figures in the plane or in space
- we can introduce a classification based on the method for deriving theorems - *synthetic* (axiomatic method, geometrical foundations separated from algebra/numbers) vs *analytic* (numerical coordinates and algebra) procedures
- there are other distinctions:
  - theorems of elementary geometry concern magnitudes (lengths, angles, areas)
  - two figures are equivalent from this point of view if they are congruent (e.g. one can be obtained from the other without changing magnitudes)
  - are congruence and similarity essential or are properties preserved even with other transformations?
  - imagine drawing a circle with perpendicular diameters and compressing it - circle becomes an ellipse, lines are no longer right angles, but the center will still bisect diameters
- given any class of transformations (rigid motions, compressions, inversions), we can ask what properties will be unchanged under those

### Projective transformations

- inspired by problems of perspective - image made by a painter is a projection of the original onto a canvas with the eye being the center
- why do we still recognize objects? some properties must be invariant under projection

- we will define the group (this means that the successive application of two transformations from this group will again be a transformation from this group) of projective transformations
  - we have planes $\pi$ and $\pi'$ and we can project one onto the other from a center O (such that any point P on the first plane will be a point P’ on the second plane and both will lie on a straight line through O) or a parallel projection, s.t. all projecting lines are parallel
  - any such mapping is called a projective transformation
    - and projective geometry deals with those, whereas metric geometry deals with magnitudes etc
- some projective properties: a point projects into a point, a straight line is projected into a straight line
  - a point and a line are incident if the point is on the line
  - if three or more points are collinear (incident with some straight line), their images will also be collinear
  - if three or more straight lines are concurrent (incident with a point), their images will also be concurrent
- measures of length and angle and their ratios are altered by projection
- triangle theorem of Desargues - if two triangles ABC and A’B’C’ are situated in a plane so that the straight lines joining corresponding vertices are concurrent in point O then the corresponding sides will intersect in three collinear points (this also works for triangles in two different planes)

### Cross-ratio

- if three points lie on a straight line, a projection will change the distances AB and BC and the ratio AB/BC
- ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Projection_geometry.svg/240px-Projection_geometry.svg.png)
- but for four points, the cross ratio ($\frac{CA}{CB}/\frac{DA}{DB}$) will remain invariant
  - the order of points is important

- we can apply this to the complete quadrilateral - a figure that has four lines no three of which are concurrent

### Parallelism and infinity

- some lines in the constructions are supposed to intersect and the construction will fail if they are parallel
  - how do we extend our basic concepts?
  - if a straight line that intersects another line is slowly moved towards being parallel, the point of intersection will recede to infinity
    - so the two lines intersect at a “point at infinity” - what exactly does this mean? we should be able to operate with points at infinity just like with regular points
- even the ordinary points and lines are not well defined, but we don’t need precise definitions, just valid rules to operate with those
  - a point is not a thing in itself, but it’s described by the statemens by which it is related to other objects
  - points, lines etc are all abstractions of their physical counterparts, e.g. we can probably actually draw many lines through a single pair of physical points because those points have a thickness, but the axiom referring to abstract objects states that there’s just one line
- ordinary geometry of points and lines is complicated by the fact that a pair of parallel lines do not intersect in a point
  - so to remove this, we should enlarge the concept of a point (just like how we enlarged the concept of a number to account for division and subtraction)
  - therefore, we agree to add to the ordinary points on each line a single ideal point (which belongs to all of the lines parallel to the given line) - similar to a vanishing point
  - we could add two points, one for each direction, but we want to preserve the law that we can only draw one line through any two points - if a line contained two points at infinity in common with every parallel line, then multiple lines would pass through the same two points
  - we also add a single ideal line that contains all the ideal points
- therefore, **parallel projection simply means projection from a point at infinity**

### Analytic representation

- early projective geometry relied a lot on geometrical representations, but algebraic formulation is unavoidable
  - we can base everything on the number concept
  - the coordinates of a geometrical object are any set of numbers which characterize it uniquely
  - e.g. a line is $ax+by+c=0$
  - we have equations for a circle, an ellipse etc
- in ordinary analytic geometry, the rectangular coordinates of a point are signed distances of the point from the axes, but this breaks down for the points at infinity
  - if we imagine a plane $\pi$ that lies 1 unit above the x,y-plane in the z-direction, any point on this plane will have coordinates (X,Y,1)
  - thsi way we can include points at infinity into the representation as (x,y,0)
  - ![img](http://media5.datahacker.rs/2019/07/123-1024x686.png)

### Conics and quadric surfaces

- projective geometry includes conic sections and their generalizations
- an ellipse is the locus of all points P in the plane with fixed distance from two foci F1 and F2 (if foci are the same, the figure is a circle)
- hyperbola - locus of all points for which the value of the difference of the distances from fixed points is a constant
- parabola - locus of all points for which the distance to a fixed point F is equal to the distance to a given line L
-  ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Conic_Sections.svg/240px-Conic_Sections.svg.png)
- these curves can be expressed using the second degree in coordinates x,y 

- any curve defined analytically by an equation of the second degree is either one of the three conics, a straight line, a pair of straight lines, a point or imaginary
- conic sections are also projections of a circle on a plane
  - but circle is also a metric concept
  - a circle has a property that a given arc describes the same angle at every point O in the circle
  - a cross-ratio of points A,B,C,D on a circle will depend on the arcs CA, CB, DA, DB and if we project the circle to any conic K, the four points will be on K. the equality of angles will be destroyed by projection, but the cross ratio will hold
- a pencil of lines is the set of all straight lines in a plane that pass through a given point O
- a surface is defined by any three lines in space
  - a hyperboloid is made up of two different families of straight lines
  - ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Hyperboloid1.png/249px-Hyperboloid1.png)

### Axiomatics and non-Euclidean geometry

- the axiomatic method in mathematics goes back to Euclid
- to prove a theorem in a deductive system is to show that the theorem is a necessary logical consequence of some previously proved propositions
  - this is infinite regression unless we stop at some point, and we stop at axioms that we accept are true with no proof
  - the postulates must be consistent and complete, but also independent
    - there are different views on the foundation of mathematics, some consider mathematical entities as objects in the realm of “pure intuition”, independent of the mind (Kantian), while others (formalists) don’t think that mathematical objects have an intuitive reality or that axioms express truths concerning pure intuition, they are only concerned with logical reasoning based on the postulates
      - but with the second view we have to prove that the axioms cannot lead to a contradiction since now they’re arbitrary creations of human minds
  - it’s possible that proofs of consistency and completeness are not possible within strictly closed systems of concepts (Gödel)
- constructive thinking guided by intuition is the true source of mathematical dynamics
  - axiomatic form is the ideal but hardly the essence of mathematics
- geometry has been the prototype of an axiomatized discipline
  - but the postulates of Euclid must be modified and completed if all of elementary geometry is to be deduced from them
- the totality of axioms of geometry provides the implicit definition of “undefined” objects like line, point etc
- one Euclidean axiom is that you can only draw one line parallel to a given line that’s through a given point
  - is this verifiable?
  - trying to assume the contrary as proof led to non-Euclidean geometry
- it’s possible to construct a system of geometrical statements dealing with points, lines etc by deduction from a set of axioms in which the parallel postulate has been replaced by a contrary one
  - simplest such model is Klein’s model
    - the plane consists only of the points interior to the circle (and chords of the circle are non-Euclidian straight lines)
    - it’s as consistent as the classic Euclidean geometry
- in Euclidean geometry, the sum of angles in a triangle is 180 and in non-Euclidian, it’s less - Gauss showed that in reality, the sum of angles in a triangle is also 180, therefore E geometry is preferrable for describing reality
- discovering NE geometry mean that our knowledge of physical reality must not be fitted to Euclid’s axioms
- we can consider any geometry that has a set of consistent axioms about points, straight lines and so on
  - this will be useful to a physicist only if these axioms correspond to the physical behavior of things in the real world
  - consider the statement “light travels in a straight line” - if this is regarded as the physical definition of “straight line”, then we should choose our axioms to reflect the behavior of light rays
  - image a world composed on the interior of a circle C, such that the velocity of light at any point inside the circle is equal to the distance of that point from the circumference 
    - in this circle, rays of light will be circular arcs with ends perpendicular to the circumference (“straight lines” will be circular arcs)
- assumption in E geometry (also in hyperbolic) - the line is infinite
  - can we have closed straight lines?
  - Riemann considered one such geometry
    - imagine a 2D world placed on the surface of a sphere, where a “straight line” circumscribes the sphere
    - all straight lines intersect
    - we can generalize this - consider a world consisting of a curved surface in space and define a straight line as the curve of shortest length joining the points
    - points will have two classes: they will either be on the part that’s like a sphere or on the saddle-shaped part (on both sides of the plane)
    - i.e. the curvature of the space changes the local geometry

### Geometry in more than three dimensions

- our real space has 3 dimensions, the plane has two and the line has 1
- but it can be convenient to discuss higher dimensions
- e.g. solving three simultaneous equations for three unknowns x, y, z is finding the point of intersection in three dimensional space (or n-dimensional space for n unknowns)
- a point in n-dimensional space is an ordered set - even though we can’t visualize it, we can operate on it

- we can reduce from n to n-1 dimensions through mathematical induction
  - e.g. a triangle ABC => segments AB, BC and CA with coordinated ends
  - a surface of a cube can be reduced to a system of six plane squares
- from a structural point of view, the simplest figures in dimensions 0-3 are the point, the segment, the triangle and the tetrahedron
  - judging by the number of vertices and segments

## Chapter 5: Topology

### Introduction

- topology is the analysis of geometric figures subject to deformations
- earliest discovery - Descartes’/Euler’s formula relating the number of vertices, edges and faces in a polyhedron (a solid whose surface has multiple polygon faces)
  - $V-E+F=2$
  - a simple polyhedron has no holes in it (can be deformed to a sphere)
  - we can also show that there are no more than 5 regular polyhedra
- this formula is concerned only with the numbers of edges, faces and vertices and therefore is also valid for deformed polyhedra (e.g. if they were made of rubber and stretched but not torn)
- elementary geometry deals with magnitudes (lengths, angles) and projective geometry deals with concepts (point, line, incidence)
  - rigid motions and projections are special cases of topological transformations
  - a topological transformation from A to A’ is given by a correspondence $p \leftrightarrow p'$ which is biunique and continuous in both directions
- any property of A that holds for every figure into which A may be transformed is called a topological property
  - e.g. a sphere and a cube are topologically equivalent, a donut and a sphere aren’t
- if a circle lying within a domain can be shrunk to a single point, then it is simply connected
  - e.g. a figure consisting of space between two concentric circles are doubly connected, but if we cut a straight line perpendicular to the circle, it will become simply connected
- a simple closed curve C in the plane divides the plane into 2 parts - inside and outside
  - some curves are not very simple, and the proof of this theorem was pretty hard

### The four color problem

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a6/4CT_Non-Counterexample_1.svg/150px-4CT_Non-Counterexample_1.svg.png)

- how do we color a map to give different colors to any two countries that have a boundary in common?
  - it has been shown that any map, no matter how many regions or in what configuration it contains, can be colored using only four colors
  - (adjacent regions are only considered adjacent if they share the whole boundary, not part of it since if they’re only partially touching, they can’t be confused for each other)
- a general proof is unavailable, but it has been proven that five colors are sufficient and it is conjectured that so will be four

### Dimensions

- the concept of dimension is easy in simple geometric figures
  - but it can be hard: what dimension should be assigned to the point set R consisting of all points with rational coordinates? it can be one-dimensional like the line, but also can be zero
  - cantor set - removed middle 1/3 from each line, what is the dimension? it should be 1-dimensional but it has no complete interval
  - an empty set containing no points has dimension -1

### Fixed point theorem

- consider a circular disk in the plane and suppose that the points of this disk are subjected to any continuous transformation (each point stays in the circle but in a different position)
- theorem: each such transformation leaves at least one point fixed
  - intuitive proof - it is impossible to transform continuously a circular disk into its circumference alone so that each point of the circumference remains fixed
- it also holds for a triangular or square region or any other surface that’s the image of a disk

### Knots

- a knot is formed by looping and interlacing a piece of string and joining the ends together
- how do we distinguish a knotted closed curve from an unknotted curve such as a circle?
  - actually hard to answer, even for simple knots!

- many topological facts arise in the study of two-dimensional surfaces
  - genus of a surface is the largest number of non-intersecting simple closed curves that can be drawn on the surface without separating it
  - e.g. the genus of a sphere is 0, a torus is 1
- an ordinary surface has two sides - but some have one side, e.g. a Moebius strip
  - another example is the Klein bottle (has no inside or outside)

## Chapter 6: Functions and limits

### Introduction

- the main body of modern mathematics is centered around the function and the limit
- an expression such as $x^2+3x-3$ has no definite value until we assign x, it is a function of x ($f(x)$)
- the number of primes less than n is a function $\pi(n)$, the area of a triangle is a function of the lengths of its sides etc
- periodic phenomena (motion of tides, vibrations) are governed by trigonometric functions sin(x) and cos(x)
- mathematical objects can be chosen from a set S of objects - this object is a variable within the range or domain S
  - S can be integers, but also not numbers, e.g. the set of all circles in the plane or a population of people
  -  the most important case of a numerical variable is that in which the domain S is $a \leq x \leq b$ of the real number axis, then x is a continuous variable in the interval
  - if each value of a variable X is associated with a definite value of another variable U, then U is a function of X
    - if X ranges over a set S, then U will range over a set T
- $u = x^2$ ranges over the whole set of real numbers, but $u = 1/x$ ranges over the set of real numbers except for 0
- $U = f(X)$, U is the dependent variable and X is the independent variable
  - sometimes there is the same value of U for all values of X, so the set T has only one element
- the function allows us to characterize motion: if a moving particle is at a point in space defined by x, y, z and t is the time, then $x = f(t), y = g(t), z= h(t)$
  - e.g. a particle falling down $x = 0, y = 0, z = -1/2gt^2$
  - if a particle rotates uniformly on a circle, $x = cos(wt), y = sin(wt)$, where w is the angular velocity
- simplest type of functions of one variable: 
  - polynomials
  - rational functions
  - trigonometric functions

### Radian measure 

- angles are measured in units obtained by dividing a right angle into a number of equal parts - e.g. 90 units for “degrees”
  - but for theoretical purposes, a radian is better
  - describe a unit circle about a vertex of an angle, the angle will cut out an arc s on the circumference and the length of the arc is the radian measure of the angle 
    - the total circumference of a circle of radius 1 is $2\pi$, so 360 degrees is 2pi
    - $\pi y=180x$
    - e.g. 90 degrees = $\pi90=180x, x=\pi/2$
    - the radian measure is also equal to twice the area of the sector cut out by the angle

### Graphs

- character of a function is often most clearly shown by a graph
  - <img src="http://img.sparknotes.com/figures/A/ad79275cb59e569b790cb945a4ffc553/triggraphs.gif" alt="img" style="zoom:67%;" />

### Introducing new functions

- introducing new functions by making inverse functions
  - if we have a known function $F(X)$, we may try to solve $U = F(X)$ for x, so $X = G(U)$ where G will be the inverse function of F
  - this will have a unique result if the function F(X) defines a biunique mapping of the domain of X onto that of U
    - e.g. if X is any triangle on a plane and F(X) is the perimeter, there are many different triangles with the same perimeter, so there will not be a unique inverse function
    - but $m=2n$, where n ranges over all integers and m over the set T of even integers, the inverse function will be $n=m/2$
    - another example: $u = x^3$, the inverse function is $x = ^3\sqrt u$
    - but in the case of $u = x^2$, u can be x or -x, so each positive value of u will have two antecedents (but if we restrict $\sqrt u$ to positive numbers whose square is u, then the inverse function $x = \sqrt u$ will exist)
- the uniqueness of the inverse can be seen from a graph - if each value of y has only one value of x, then there is a unique inverse (no parallel to the x-axis intersects the graph in more than 1 point)
  - this is the case if $u = f(x)$ is monotone (steadily increasing or decreasing)
- another method for creating new functions if compounding of functions, e.g.
  - $z = g(x)=1+x^2$ and $u = h(z)=\sqrt z$
  - $h(g(x))=\sqrt{1+x^2}$

### Functions of several variables

- functions can be in several variables and not just x 
  - if the independent variable P is a point in the plane with coordinates (x,y) and each point P has a corresponding number u, then $u = f(x,y)$
  - e.g. the area of a triangle is a function of its three sides
  - a two-variable function can be represented in three dimensions with x, y and u as coordinates
  - e.g. $\sqrt{1-x^2-y^2}=u$ is a spherical surface with the equation $u^2+x^+y^2=1$
    - we can draw these in 3d or we can draw contour plots or level curves
  - in the case of functions of several variables, inverse functions don’t exist
- a correspondence between the points of 1 line l and another line l’ is a function of their coordinates along the line $x'=f(x)$
  - the simplest example is a transformation by projection, which is generally characterized by $f(x)=(ax+b)/(cx+d)$ where a,b,c,d are constants
  - mapping in two dimensions from a plane with x,y coordinates to a plane with x’,y’ coordinates requires two functions of two variables ($x'=f(x,y)$ and $y'=g(x,y)$)

### Continuity

- a function is continuous if its graph is an uninterrupted curve
- some functions tend to infinity when x approaches zero, like $1/x$
- it may be possible to make the function continuous by redefining the value at the discontinuity (e.g. u = x/x is equal to 0 when x isn’t 0, but we can agree that u = 1 also corresponds to x = 0)
  - this is a removable discontinuity, if it’s can’t be removed it is essential

- continuity of functions is based on limits
  - sequences of numbers have limits, e.g. $a_n=1/n$ tends to 0 as n tends to infinity
  - a geometric representation can be obtained if we represent the terms of the sequence by their corresponding points on the number axis - they will cluster around 0
  - we can choose an interval I on the number axis centered around 0 with $2\epsilon$ width
    - if $\epsilon$ = 1/10, then the first few terms will be outside I, but mostly in
    - even if we choose $\epsilon$ = 1/1000, only the first thousand terms will be outside I
    - no matter how small $\epsilon$ is, we can find an integer N so that $1/N < \epsilon$
  - our intuition tells us that a limit is a result of motion - e.g. we move through the integers and observe the behavior of a sequence
    - but to get a precise definition, we reverse the order of steps - we look at what we have to do if we want to check the statement $a_n \to a$
      - we must choose an arbitrarily small margin around a and then determine whether we can meet this condition by making n sufficiently large (where margin is $\epsilon$ and large n is N)
    - e.g. in the sequence $a_n = \frac{n}{n+1}$, the limit is 1 - if you choose an interval with 1 at the center and for which $\epsilon$ = 1/10, then N = 10 for 0 < 1/n+1 < 1/10 when n >= 10
- some sequences can have the same value for every term, e.g. $a_1=a_2=...=a_n=0$ and the limit is also 0
- a sequence with a limit is convergent and a sequence without a limit is divergent (also if it tends to infinity)
  - it’s not a good idea to just substitute infinity for n when trying to define the limit since infinity is not a number
- sequences can be monotonically increasing or decreasing, but also oscillating
  - any monotone increasing sequence that has an upper bound must converge to a limit

### The number $e$

- Euler’s number $e$ is important in math
  - factorial: $n! = 1*2*3*4...*n$
  - consider the sequence $a_n = 1+1/1!+1/2!+...+1/n!$
    - the sequence is monotone increasing
    - values of $a_n$ are bounded above 3 (because $1/s!=1/2*1/3...1/s<1/2*1/2...*1/2=1/2^{s-1}$ and $a_n < 1+1+1/2+1/2^2+1/2^3...+1/2^{n-1}=1+2(1-(1/2)^n)<3$)
  - the limit of $a_n$ is called $e$
    - $e = 1+1/1!+1/2!+1/3!+...+1/n!$
    - $e \approx 2.7182818$
  - the number e is irrational

### The number $\pi$

- the number $\pi$ describes the length of the circumference of a circle of unit radius
  - this length can be defined as the limit of a sequence of lengths of regular polygons with increasing number of sides
  - $\pi$ is a transcedental number and hence irrational
  - $\pi$ has no useful decimal expansion, but other expansions exist, e.g. $\pi/4=1-1/3+1/5-1/7+...$ ($(-1)^n\frac{1}{2n+1}$)

### Continued fractions

- every rational number can be written in this form by means of the Euclidean algorithm, but for irrational numbers the fraction does not stop
- some irrational numbers have interesting infinite continued fractions, e.g.
  - $\sqrt2=1+\frac{1}{2+\frac{1}{2+\frac{1}{2+\frac{1}{...}}}}$ 
  - positive roots of any quadratic equations like $x^2 = ax+1$ or $x = a+1/x$ have the expansion
    - $x=a+\frac{1}{a+\frac{1}{a+\frac{1}{a+\frac{1}{...}}}}$
  - the real roots of quadratic equations with integral coefficients have periodic continued fraction developments
- there are similar expansions for e and pi

- functions also have limits, e.g. $f(x)$ has a limit a as $x$ tends to $x_1$
  - e.g. a function $(x+x^3)/x$ is defined for all x except for x = 0
  - from a graph, we can see than as x approaches 0, f(x) approaches 1
  - explicit formula for the difference between f(x) and 1:
    - $f(x)-1=\frac{x+x^3}{x}-1=\frac{x^3}{x}$
    - we can confine x to a sufficiently small neighborhood of 0
    - if $\epsilon$ is any positive number, then the difference between $f(x)$ and 1 will be smaller than $\epsilon$ if the distance of x from 0 is less than $\delta$, which is $\sqrt \epsilon$
- the epsilon/delta definition of a limit is very important to calculus (derivatives and integrals), but there have been difficulties along the way
  - in the 17th and 18th century, mathematicians accepted that x can steadily change and move towards a limiting value, but it was hard to attach a precise mathematical meaning to the idea that f(x) tends to a fixed value
  - the points on a line form a dense set and there is no “next” point after a given point has been reached
  - Zeno’s paradoxes indicate a discrepancy between the intuitive idea and the mathematical language designed to describe it in logical terms
  - Cauchy realized that any reference to a prior intuitive idea must be omitted
  - the epsilon/beta defition does not include motion, although it doesn’t mean we have to completely discard the intuition

### Limit of $\frac{\sin x}{x}$

- $\sin x/x$ is defined for all x except for 0 (where it becomes 0/0)
  - we can compute its value for small values of x and see that the limit as x approaches 0 is 1
  - we have the unit circle definition of trigonometric functions
  - <img src="https://www.onlinemathlearning.com/image-files/unit-circle-trigonometry.png" alt="img" style="zoom:75%;" /> 
  - if x is the radian measure of theta, then 0 < x < pi/2 the area of the triangle will be $1/2*1*\sin x$, the area of a circular sector will be $1/2*x$
    - $\sin x<x<1$
    - $1<x/\sin x<1/\cos x$
    - $\cos x<\sin x/x<1$
    - $1-\cos x < x^2$ or $1-x^2<\cos x$
    - so $1-x^2<\frac{\sin x}{x}<1$
      - we can make this less than any number $\epsilon$ by choosing |x|<delta
- If x is sufficiently large, 1/x tends to 0
  - the function has the limit a as x tends to infinity if no matter how small, we can find K such that $|x|>K$ and $|f(x)-a|<\epsilon$
- the function is continuous if we can find a number delta such that $|x-x_1|<\delta$ and $|f(x)-f(x_1)|<\epsilon$

### Fundamental theorems on continuous functions

- Bolzano’s theorem - a continuous function of a variable x which is positive for some value of x and negative for some other value of x in a closed interval $a \leq x \leq b$ must have value zero for some intermediate value of x
- Weierstrass’ theorem - if a function is continuous in an interval I ($a \leq x \leq b$) including the end points a and b, then there must exist at least one point in I where f(x) attains its largest value M and another point where it attains its least value m

- Bolzano’s theorem has geometrical applications
  - if A and B are any two areas in a plane, then there exists a straight line in the plane which bisects A and B simultaneously
- more limits:
  - $\lim q^n = \infty$
  - $\lim ^n\sqrt{p} = 1$
  - discontinuous functions have different limits on different segments

## Chapter 7: Minima and maxima

### Introduction

- a straight segment is the shortest connection between its endpoints
- an arc of a great circle (largest circle on the sphere) is the shortest curve joining two points on a sphere, circles and spheres enclose the largest area/volume
- one significant discovery was by Heron:
  - a light ray from a point P meeting a plane mirror L in a point R is reflected in the direction of a point Q such that PR and QR form equal angles with the mirror
  - if R’ is any other point on the mirror, PR’+R’Q is larger than PR+RQ - the path of light is the shortest possible path from P to Q by way of the mirror
- maxima and minima problems have a large practical importance
  - and they are integrated in science as well

### Elementary geometry

- given two segments a and b, find the triangle of maximum area having a and b as sides - right triangle is the solution (area of the triangle is $A = 1/2*ah$ which is at maximum when h is largest and that occurs when h coincides with b)
- Heron’s theorem: given a line L and two points P and Q on the same side of L, for what point R on L is PR+RQ the shortest path? We reflect P in L as in a mirror, obtaining the point P’ such that L perpendicularly bisects PP’ and P’Q will intersect L at R
- this problem can be generalized to include several lines

- we can apply this to triangle problems, e.g. given the area and one side c, determine the one for which the sum of the other sides is smallest
- we can also connect this problem to other geometrical theorems
  - if R is the point on L s.t. PR+RQ is a minimum, then PR and PQ make equal angles with L and the minimum total distance is 2a
  - if p and q are distances from any point on the plane to P and Q and if we consider all points for which p+q = 2a, this locus will be an ellipse and L will be tangent to it at R
  - if we have two points P and Q on opposite sides of L, then how do we find R such that |p-q| is a maximum? here we also reflect P in L, getting P’ and since R’, Q and P’ form a triangle, |p-q| will never be bigger than P’Q (the difference between two sides of a triangle is never greater than the third side)
    - the point R is the intersection of L with the line through P\' and Q
  - if P and Q are on the same side, we solve a minimum problem, but if they are on opposite sides, we solve a maximum problem - in the first case, distances and their sum become larger without bound so there is no maximum value, but in the second case, we can have a minimum but we have to find the maximum
- this can also be applied to finding the shortest and the longest distance from a point P to a given curve C

### A general principle underlying extreme value problems

- we denote the point R by $(x,y)$, P by $(x_1,y_1)$ and Q by $(x_2,y_2)$, then $p = \sqrt{(x-x_1)^2+(y-y_1)^2}$ and $q = \sqrt{(x-x_2)^2+(y-y_2)^2}$ (so p is the distance between R and P and q is the distance between R and Q) and the problem is to find the extreme values of the function $f(x,y)=p+q$
- this function is continuous everywhere in the plane, but the point with coordinates x and y is restricted to the given curve C (e.g. $x^2+y^2-1=0$)
- the problem is then to find the extreme values of $f(x,y)$ given that $g(x,y)=0$
- there is a family of curves $f(x,y)=c$
  - as c changes, the curve will move through the plane and one curve of the family will pass through the minimum and maximum, respectively

### Stationary points and the differential calculus

- the elementary methods described above are more simple and direct than those of calculus
- differential calculus was strongly influenced by individual maximum and minimum problems 
- extrema are connected to calculus
  - the derivative $f'(x)$ is the slope of the tangent line to the curve $f(x)$ at the point $(x,y)$
  - ![img](https://www.mathsisfun.com/calculus/images/function-min-max.svg)
  - at the maximum or minimum points the tangent must be horizontal, so the slope will be equal to 0 and $f'(x)=0$ for the extreme values of $f(x)$
  - maxima and minima can be relative or absolute (a.k.a. local or global)
  - some points can be neither a maximum nor a minimum even if the derivative is equal to 0
  - these points are called stationary points
  - higher derivatives will completely characterize these points

### Minima and maxima of functions of several variables

- sometimes problems of min and max cannot be expressed in terms of $f(x)$, e.g. finding the extrema of a function $z = f(x,y)$ of two variables
- we can represent $f(x,y)$ by the height z of a surface above the x,y-plane
  - if it were a landscape, a maximum will be a mountain top and a minimum will be the bottom of a lake 
  - mountain passes will also have horizontal tangents (saddle points)
- we can also represent it by drawing contour lines and a max/min will be surrounded by close contour lines, saddle points will have crossed lines

### Topology

- stationary points are connected to topology
- imagine a mountain landscape on a ring-shaped island B with boundaries C and C’
- if the altitude is $u = f(x,y)$ which is 0 on the boundaries and >0 on the surface, then there must be at least one mountain pass (saddle point) where the lines will be crossed
- for a domain bounded by p curves there must exist at least $p-1$ stationary points

### Distance from a point to a surface

- for the distance between a point P and a closed curve there are at least two stationary values (a minimum and a maximum) - same if we extend it to 3 dimensions (since a surface is topologically equivalent to a sphere)
- but if we have a surface of a higher genus, like a torus, we will have different types of extrema (maxima of minima and minima or maxima)

### Schwarz’s triangle problem

- Hermann Schwarz posited the following problem: given an acute angled triangle, inscribe it in another triangle with the least possible perimeter (inscribed means that a vertex will be on each side of the original triangle)
- there is exactly one such triangle and its vertices are foot-points of the altitudes of the given triangle
- the minimum property of the altitude triangle is proven as follows:
  - at each vertex P, Q, R the two sides of the altitude triangle make equal angles with the side of the original triangle - this angle is equal to the angle at the opposite vertex of the original triangle
  - we can use the resulting quadrilaterals (formed with a point O that is the intersection of the lines from each of the big vertices) to prove equivalence of angles
  - reflection property: the reflection of one side of the small triangle in the bigger triangle’s side is a continuation of another side of the small triangle
  - to prove the minimum property, we can consider other inscribed triangles and reflect the whole figure
  - we can show that the perimeter of the altitude triangle is the shortest possible for any inscribed triangle
- another proof exists, based on the equal angle property
- if the angles are obtuse (>90 degrees), then the altitude triangle can no longer be strictly inscribed in the triangle and will not give the minimum perimeter
- if the triangle represents a chamber with reflecting walls, then the altitude triangle is the only triangular light path possible in the chamber

### Reflection and ergodic motion

- a major problem in dynamics and optics is to describe the trajectory of a particle in space or of a light ray for an unlimited length of time
- if a trajectory will fill the space everywhere with an approximately equal distribution, such a trajectory is called ergodic
  - the assumption that such a trajectory exists is the foundation for statistical methods in modern dynamics and atomic theorey
  - but there are not many rigorous proofs of its existence
- motion within a plane curve C if C is a perfect mirror (reflects the free particle at the same angle at which it hits the boundary)
- if we have an elliptical table with the foci $F_1$ and $F_2$, the tangent to an ellipse will make equal angles with the lines joining the point of tangency to the two foci and every trajectory through a focus will be reflected through the other focus
  - ![img](https://www.softschools.com/math/calculus/images/finding_the_foci_of_an_ellipse_img_2.png)
  - the trajectory after n reflections will tens to the major axis $F_1F_2$
  - if the initial ray does not go through a focus, then all the rays will go between the foci and be tangent to a hyperbola that has $F_1$ and $F_2$ as foci
  - if the initial ray does not separate $F_1$ and $F_2$, none of the reflected rays will

### Steiner’s problem

- the villages A, B and C are to be joined by a system of roads of minimum total length
  - A, B and C are points in a plane and a point P is sought such that a+b+c (distances to P) will be a minimum
  - the answer is that if the triangle formed by the three points has angles less than 120 degrees, then P is the point from which all three sides subtends an angle of 120 (e.g. angle opposite from side AB is 120)
  - but if one of the angles of ABC is 120, then P will be at the point where this vertex is
- the alternatives: either P coincides with one of the vertices or it’s different
  - if it coincides, P must be the vertex of the largest angle of ABC (e.g. C, since CA+CB is less than any other sum of two sides)
  - in the other cases, we let K be the circle with radius c around C - then P must be the point on K such that PA+PB is minimized
  - if A and B are outside of the circle, then PA anf PB must form equal angles with K and with the radius PC, which is perpendicular to K
  - if they are inside the circle, e.g. A is inside the circle, then P coincides with A

### Street network problem

- we can generalize the problem above to n given points, where we ask for the point P the distance to which from every other point is a minimum
  - e.g. for a quadrilateral formed by 4 points, P will be at the intersection of the diagonals
- we can also generalize it to a “street network” of shortest total length (a connected system of straight line segments of shortest total length such that any two of the given points canbe joined by a polygon consisting of segments of the system)
  - in the case of n given points, there will be at most n-2 multiple intersections at each of which three segments meet at angles of 120

### Extrema and inequalities

- inequalities are very important in higher mathematics
- the solution of a maximum problem always leads, in principle, to an inequality which expresses the fact that the variable quantity that is considered is $\leq$ to the maximum value in the solution
- arithmetical and geometrical mean:
  - among all rectangles with a prescribed perimeter, find one with the largest area
  - the solution is a square:
    - let 2a be the prescribed perimeter, so the fixed sum of the adjacent edges will be x+y and xy is to be maximized
    - the mean of x and y is $m=(x+y)/2$
    - we also introduce $d=(x-y)/2$, such that $x = m+d$, $y = m-d$
    - $xy = (x+y)^2/4-d^2$
    - this is greater than 0 except when d = 0, we get $\sqrt{xy}\leq \frac{x+y}{2}$ (square root of xy is the geometric mean of x and y)
    - since x + y is fixed, area xy is at maximum when x = y
- we can derive this inequality geometrically by considering the fixed straight line $x+y=2m$ in the plane and a family of curves ($xy =c$,hyperbolas)
  - the curve with the greatest value of c that has a point in common with the straight line at x = y = m, so $c = m^2$
- this inequality can be generalized to any number of positive quantities
  - $m = \frac{x_1+x_2+...+x_n}{n}$
  - $g = \sqrt{x_1x_2...x_n}$
  - $g \leq m$ and m = g only if all x’s are identical
- this can be proven in a similar way to previous problems: partition a given quantity C into n positive parts $x_n$ such that the product of them will be as large as possible
  - we assume that a maximum exists and is obtained when $x_1 = a_1$ and so on 
  - we have to prove that $a_1=a_2=a_3..$
  -  suppose this is not true and $a_1 \not=a_2$
  - consider the quantities $x_1=s, x_2=s, x_3=a_3$ and so on, where $s = (a_1+a_2)/2$, so replace the quantities by another set in which the first two are changed and made equal and the whole sum stays the same
  - we can write that $a_1 = s+d$ and $a_2=s-d$, where $d = (a_1-a_2)/2$
  - the new product (with the changed values) is $P'=s^2*a_3...a_n$ and the old product is $(s^2-d^2)*a_3...a_n$, so unless d = 0, $P < P'$, so d = 0 and the two values are equal
  - we can continue this proof for all a’s and show that they are equal (and g = m in this case)

### Method of least squares

- the arithmetical mean of n numbers has an important minimum proerty
- let $u$ be an unknown quantity that we want to determine as accurately as possible with some instrument
- we make n readings which yield slightly different results due to experimental error
  - which value is the most trustworthy? we usually select the arithmetical mean $m$
  - let $u$ be any possible value for the measured quantity, then the differences of u from x’s are the deviations from different readings
  - we can assume that the optimal value for $u$ will be one for which the total deviation is as small as possible
  - we take the squares of the deviations (as customary and started with Gauss) and choose the optimal value that value for which the sum of squares of the deviations is as small as possible
  - this optimal value is exactly the arithmetic mean m
    - we can write $(u-x_i)=(m-x_i)+(u-m)$
    - $(u-x_i)^2 = (m-x_i)^2+(u-m)^2+2(m-x_i)(u-m)$
    - if we add all these for different i’s, the last terms will add up to $2(u-m)(nm-x_1-...-x_n)$ which is zero because m is the sum of x’s divided by n, so we will retain only the quadratic terms 
- this method can be applied in more complicated cases, like finding an optimal line through points
  - $y = ax+b$ and we want to find the coefficients a and b
  - the distance in the y direction from the line to the point $x_i,y_i$ is given by $y_i-(ax_i+b)$ and the square of this distance is $(y_i-ax_i-b)^2$, so we want to find a and b such that the sum of these distances for all points is minimized

### Existence of extrema and Dirichlet’s principle

- sometimes the solution is directly demonstrated to give a better result (e.g. the triangle problem)
  - but sometimes we have to assume that a solution is found and examine this assumption and draw conclusions from it
  - the second method involves an assumption that a solution exists
- until the late 19th century, the logical point of this assumption was not really examined
- Riemann’s thesis on the theory of functions of a complex variable had a logical “hole” in it - the question of the existence of a minimum
  - much of the theory was based on “Dirichlet’s principle”
  - image that part of a plane or any surface is covered with foil and that a current is set up in the layers of the foil by connecting it to a battery
  - we know the physical result, but what about the mathematical problem?
  - the physical phenomenon can be described as a boundary value problem of a partial differential equation 
  - the problem is assumed to be solvable because it is assumed to be equivalent to a physical phenomenon, but this is not proven by an argument
  - Riemann showed that the problem is equivalent to a minimum proboem (a quantity expressing the energy of the electric flow is minimized by the actual flow in comparison to the other flows possible)
  - then he stated “Dirichlet’s principle” that such a minimum problem has a solution
- this problem was only solved decades later
- examples:
  - we mark two points A and B at a distance d on a straight line L and ask for the polygon of shortest length that starts at A in a direction perpendicualr to L and ends at B
  - any path will have a length greater than d (AB), since it is the shortest distance between the points
  - if we vary the height of a point at which we start above A, we can obtain a path as different from d as we like - if a shortest admissible path exists, it must be equal to d
  - but AB is equal to d and this path does not start perpendicular to L, so this minimum problem has no solution
- a general form:
  - consider a class of objects (curves or surfaces) to each of which we attach a certain number as a function (e.g. length or area)
  - if there is a finite number of objects in the class, there must be a maximum and a minimum
  - but if there are infinitely many objects in the class, there doesn’t need to be a largest or a smallest number

### Elementary extremum problems

- a compact set is closed and bounded, e.g. a line segment with a closed interval, a rectangle or a finite set of points
- the competing values in the elementary problems can be regarded as the values of a function in a domain that’s either compact or can be made so
  - e.g. if we have closed curves, we can find points that have the least possible distance from each other, but if they are infinite, there may not be a solution
- in higher cases, we may have difficulties - e.g. the domain of the independent variable is not compact or the function is not continuous

### The isoperimetric problem

- the circle encloses the largest area among all closed curves (“obvious” fact that was hard to prove)
- assume that a solution exists and then suppose the curve C is the prescribed one with the length L and maximum area
  - we can show that C must be convex (the straight segment joining any points of C must be inside or on C) - if it’s concave, we can connect two points with a line outside of C that will describe a larger area
  - we can choose two points dividing the solution curve into arcs of equal length - then the line AB must divide it into two equal parts
    - sub-problem - find the arc of length L/2 with endpoints on A and B encloses a maximum area
    - we can show that every inscribed angle in this arc will be a right angle, therefore it is a semicircle (if they were not 90 degrees, we could find a larger inscribed triangle)

### Extremum problems with boundary conditions

- domain of the variable in these problems can be restricted by boundary conditions
- Weierstrass showed that in a compact domain a continuous function will have a largest and a smallest value, but that does not exclude the possibility of it being at the boundary (e.g. u = x restricted by 0 and 1, largest and smallest values are at endpoints)
  - but these will not be represented by a summit or a depression in the curve
- we can show a connection between the three street problem and the largest curve problem - if we shrink A, it can break up into 3 arcs and then shrink to the streets

### Calculus of variations

- brachistochrone problem
  - imagine a particle constrained to slide without friction along a certain curve joining a point A to a lower point B
  - along which curve will the time required for descent be least?
  - this problem is different from previously known ones, because earlier differential calculus problems had the quantity to be minimized depend only on one or more numerical variables, but here the time to descend depends on the whole curve
  - the solution turned out to be the cycloid (curve described by a point on a rolling circle)
    - this curve has popped up in other problems too, e.g. pendulums
- there were many ways to solve this problem, but many of them were specific to the problem
  - Euler and Lagrange evolved more general methods for solving extremum problems in which the independent element was a curve, a function or a system of functions
  - this method was called the calculus of variations
- this branch of mathematics has many applications in physics - natural phenomena follow some pattern of maxima and minima (e.g. the reflection of a light ray follows a minimum principle, refraction of a light ray is determined by two straight segments with an angle $\alpha$ and $\alpha'$, with conditions $\sin\alpha/\sin\alpha'=v/w$)
  - Fermat proved that this path is such that the time taken by a light ray is a minimum
  - he also generalized the statement of this law so as to include curved surfaces of discontinuity between media
    - in these systems, the light still follows a path along which the time taken is minimized
  - he also considered any optical system in which the velocity of light varies in a prescribed way (e.g. the atmosphere): you can divide the continuous heterogeneous medium into thin slabs with approximately constant velocity of light and imagined this medium replaced by one with constant velocity - then you can apply the principle going from each slab to the next
    - the thickness of the slabs can tend to 0 and so the following principle is established: in an inhomogeneous medium, a light ray follows a path along which the time taken is a minimum with respect to all paths joining the two points
- minimum principles are dominant in other branches of physics, e.g. a stable equilibrium of a mechanical system is attained if the system is arranged in such a way that its “potential energy” is a minimum 
  - laws of motion also use maximum and minimum principles
- Bernoulli’s solution to the brachistochrone problem: start with the fact that a mass point falling from rest at A along any curve C will have at any point P a velocity proportional to $\sqrt h$, where h is the vertical distance from A to P, dissect the space into many horizontal slabs and assume constant velocity in each slab
  - according to the refraction law, the motion must minimize the travel time, so we apply the refraction law and find the angle between the segments - if the thickness of slabs tends to 0, $\sin \alpha/\sqrt h$ is constant and the curve is a cycloid

### Geodesics on a sphere

- a geodesic is a shortest path between two points on a surface
  - on a sphere, this is an arc of great circles
- if P and Q are two points on a sphere, c is the shortest path connecting them - what is the longer arc c’ of the same great circle? c’ solves a maxi-minimum problem

### Experimental solutions of minimum problems

- sometimes variational problems cannot be solved explicitly through formulas or geometric constructions
- but it can be enough to prove that a solution under certain conditions exists and then investigate properties of this solution
- if a proof is hard, it can be useful to physically emulate the conditions of the problem (the existence of a physical phenomenon will represent the solution of the mathematical problem)
  - this will not be a mathematical proof, but can help solve a problem
- a problem: find the surface of the smallest area bounded by a given closed contour in space
  - mathematically, this problem is connected with PDE solutions
  - Euler showed that all non-plane minimal surfaces must be saddle-shaped and the mean curvature must be zero
  - if we dip a closed contour made of wire into a liquid of low surface tension and then take it out, a film in the form of a minimal surface of least area will span the contour
    - experiments have been conducted with more complicated topological surfaces, e.g. one-sided surfaces or of a genus different from 0
      - these sometimes show surprising discontinuities with continuous changes to the shape
- other mathematical problems also have experimental solutions
  - Steiner’s problem can be solved with soap surfaces too

## Chapter 8: The Calculus

### Introduction

- the invention of calculus is sometimes ascribed only to Newton and Leibniz, but they were, of course, only part of the history
- two central problems:
  - the problem of tangents - find tangent lines to a given curve
  - the problem of quadrature - find the area within a given curve
- Newton and Leibniz’s contribution to these problems was to recognize the connection between them
- calculus started with intuitive language, but has been developed into a rigorous discipline

### The integral

- we choose a square with unit sides as the unit of area
- we can calculate the area of a rectangle easily - if p and q are the sides, then pq is the area
- the area of a triangle is equal to half the area of a rectangle with the same base b and altitude h ($1/2 bh$)
  - any plane domain bounded by polygonal lines can be decomposed into triangles and its area can be computed with them
- what about an area bounded by curves?
  - naive approach: curvilinear areas are given entities so we can compute their area
  - we can inscribe in the domain an approximating domain with a polygonal boundary and a well-defined area and so exhaust the whole area
  - this approach worked but was specific for given curves
- the basic concept of the calculus is the integral
  - expression of the area under a curve by means of a limit
  - e.g. if we have a continuous function like $y = x^2$ or $y=1+\cos x$, then we consider the domain that’s bounded by the x-axis, the perpendiculars to the x-axis and the curve
  - in general, we cannot decompose it into rectangles and immediately explicitly calculate it
  - but we can subdivide the interval into small sub-intervals and replace ech strip of the domain by a rectangle
  - the accuracy will increase the more rectangles we have
  - if we form a sequence of rectangular approximations to the area under the curve such that the width of the widest rectangle tends to 0, then the sequence will approach the limit A
  - the area A of the domain is the integral of the function from a to b
    - $A = \int_a^bf(x)dx$
    - the integral symbol and “dx” were introduced by Leibniz
- let’s subdivide the interval from a to b into n small sub-intervals and assume they have equal width $(b-a)/n$
  - the difference between consecutive x-values, i.e. their length is $\Delta x$
  - the sum of the area of these rectangles is $S_n=\sum_{j=1}^nf(x_i)*\Delta x$
  - the limit of this sum as n increases (as the amount of these rectangles goes up is the integral over f(x))
    - dx was called “infinitesimaly small”, but this isn’t really a rigorous mathematical definition
- the curve f(x) may lay below the x axis too and the procedure will also remain meaningful
  - b can be less than a, so that $\Delta x$ is a negative number
    - $\int_a^bf(x)dx=-\int_b^af(x)dx$
- the value of the integral remains the same even if we don’t have equidistant points!

### Pre-calculus stage

- does this algorithm hold for concrete cases?
  - Archimedes performed the integration of a parabolic segment using a device
  - same for other functions later
- start with a constant $y = f(x)$, like $f(x)=2$, then the integral of 2 over a to b is $2(b-a)$
  - compare to the definition as a limit: substitute $f(x_i)=2$ for all the values, we get $2\sum_{j=1}^n\Delta x=2(b-a)$
- the integration of $f(x)=x$ is equally simple
  - $\int_a^bxdx$ is the area of a trapezoid which is $(b^2-a^2)/2$
- $x^2$ is less trivial
  - choose the lower limit a, then $\Delta x = b/n$
  - $x_j = j*\Delta x$ 
  - and $f(x_j) = j^2(\Delta x)^2$, so $S_n = (1^2+2^2+...+n^2)(\Delta x)^2$
  - since we know that the first parenthesis adds up to $\frac{n(n+1)(2n+1)}{6}$ and delta x is  b/n, then $S_n = b^3/n^3 * (1+1/n)(2+1/n)$
  - since 1/n will tend to 0 with increasing n, the result will be $b^3/6*1*2=b^3/3$

### Rules for integral calculus

- an important step in the development of calculus occurred when general rules were formulated
  - the integral of the sum of two functions is equal to the sum of the integrals ($\int f(x)+g(x)dx = \int f(x)dx + \int g(x)dx$)
  - the integral of a constant times a function is that constant times the integral ($\int cf(x)dx = c\int f(x)$)
- e.g. to integrate a polynomial, we can take the constants out and split it into integrals of each part of the sum

- if we use a name other than x, nothing changes
  - also if we make some changes in the coordinate system, e.g. moving it to the right 
- some important inequalities:
  - if $b>a$ and the values of $f(x)$ are smaller than those of $g(x)$, then $\int_a^bf(x)dx\leq\int_a^bg(x)dx$

### The derivative

- this concept was only formulated around the 17th century
- Fermat was interested in determining the maxima and minima of a function
- we use the tangent to characterize extrema of a function
  - the direction of the curve at x is given by the slope of the tangent line at x
  - slope is $\Delta y/\Delta x$ ($\tan \theta$ if $\theta$ is between the line and the x-axis)
- since we cannot calculate the slope just from 1 point, we use a limiting procedure where we consider another point near the original one and calculate the slope of the line between P and P’
  - we let P’ move along the curve towards P
  - slope is the limit of $\Delta y/\Delta x$ as both values approach 0
- notations for derivative:
  - $f'(x)$
  - $Df(x)$
  - $\frac{dy}{dx}$
- a negative derivative means a descending curve, a positive one means ascending curve and a derivative of 0 means a horizontal line (e.g. at min, max or saddle point)
- the simplest non-trivial example is $x^2$
  - the derivative is $\frac{f(x_1)-f(x)}{x_1-x}=\frac{x^2_1-x^2}{x_1-x}=\frac{(x_1-x)(x_1+x)}{x_1-x}=x_1+x$
  - plug in x = x, and get $2x$
- the general formula will be $f'(x^n)=nx^{n-1}$
- we can obtain similar formula for other functions:
  - $f'(1/x)=-1/x^2$
  - $f'(\sqrt x)=1/2\sqrt x$

### Trigonometrical functions

- the question of differentiating trig functions is important
  - to differentiate sin, we set $x_1-x=h$, so $x_1=x+h$ and $f(x_1)=sin(x+h)$, which we can also expand as $\sin x \cos h + \cos x \sin h$
  - so if we use the difference between y over the difference between x formula, we get $\cos x(\sin h/h)+\sin x(\cos h-1/h)$
  - using limits, we find that the first parenthesis tends to 1 and the second one tends to 0, so that the whole formula approaches the cosine of x
- $f'(\sin x)=\cos x$
- $f'(\cos x)=-\sin x$

### Continuity

- the differentiability of a function implies continuity - if we can assume that the limit exists, the function is continuous

### Velocity and acceleration

- derivative doesn’t just concern slopes - the concept is related to the rate of change over time
- if a particle moves along a straight line, its motion is described by $x = f(t)$, where uniform motion will be described by a linear equation $x = a+bt$
- motion in a plane will be described by two functions, $x = f(t), y= g(t)$
  - $x=a+bt,y=c+dt$
  - the coefficients of t will be the two components of velocity
  - we can eliminate t from the equations to get a parabola (trajectory): $(x-a)d+(y-c)b=0$
- we can also model the movement of a particle in the x,y-plane under the influence of gravity, where $y = c+dt - 1/2gt^2$ where g is the acceleration due to gravity
  - we can similarly get the trajectory by eliminating t
- if a particle moves along a given curve, its motion is the arc from a fixed initial point along the curve
- if the motion is uniform, we can get the velocity by taking two values of time and measuring the position, then dividing distance by time 
  - but this will give us velocity during an interval and not instantaneous velocity, so we must let t tend to 0
  - velocity is the derivative of distance 
  - acceleration is the derivative of velocity (how velocity changes)

### Geometrical meaning of $f’'(x)$

- the second derivative expresses the rate of change of the slope of the curve (i.e. indicates which way the curve is bent)
- if the second derivative is positive, that means the slope increases with x and it is concave upward
- similarly, if the second derivative is negative, then it is concave downward
- concavity changes at inflection points (wherever the second derivative is 0)

### Maxima and minima

- algorithm:
  - find the formula for the first derivative 
  - find where it is equal to 0
  - find the second derivative formula
  - find if it is positive or negative for the potential minimum/maximum values

### Differentiation rules

- some general rules have been derived
- sum rule $k(x)=af(x)+bg(x)$, $k'(x)=af'(x)+bg'(x)$
- product rule $p(x)=f(x)g(x)$, $p'(x)=f'(x)g(x)+f(x)g'(x)$
- quotient rule $q(x)=f(x)/g(x)$, $q'(x)=\frac{g(x)f'(x)-f(x)g'(x)}{(g(x))^2}$
  - assume $g(x)\not=0$
- derivatives of inverse functions are reciprocal
- if functions are compound, e.g. $z=g(y),y=f(x),k(x)=g(f(x))$, then $k'(x)=g'(y)f'(x)$

### Leibniz’s notation

- the field was dominated by the concepts of “infinitely small quantities” etc
- the philosophical attitude of the time and the nature of the human mind dictated questions like “what are integrals and derivatives in themselves outside of limiting processes?”
  - abandoning this attitude can be useful
- the symbols d in the derivative and integral are considered as symbols for a passage to the limit

### Fundamental theorem of calculus

- the notion of integration and differentiation have been developed before Newton and Leibniz, but the connection between the two has not been revealed for some time
- in fact, the derivative and the integral are inverse to one another, like addition and subtraction
- consider the integral of a function $f(x)$ from a fixed lower limit to the variable upper limit u
  - $F(x)=\int_a^xf(u)du$
  - the derivative of this integral is equal to the value of f(u) at the point x
  - $F'(x)=f(x)$
- the process of integration is undone by the process of differentiation
- imagine F(x) as an area, then use the analytical process of differentiation:
  - the different $F(x_1)-F(x)$ is the area between these two locations, which lies between $(x_1-x)m$ and $(x_1-x)M$, where m and M are the greatest and least values of the function (areas of rectangles)
  - $m \leq \frac{F(x_1)-F(x)}{x_1-x}\leq M$
  - Let $x_1$ approach x so that both m and M approach the height of the function $f(x)$, then $F'(x)=\lim \frac{F(x_1)-F(x)}{x_1-x}=f(x)$
  - rate of change of the area under the curve as x increases is equal to the height of the curve at the point x
- function $G(x)$ for which $G'(x)=f(x)$ is a “primitive function” of f(x)
  - the theorem then goes like this: $F(x)$, which is the integral of $f(u)$ with a fixed lower limit and variable upper limit x (indefinite integral) is a primitive function of f(x)
  - it is A primitive function since we can add any constant and the result will be the same, since the derivative of a constant is 0
- since F(x) is the integral of f(u) between a and x, F(x) is a primitive function of f(x), and $F(x)=G(x)+c$ where c is a constant
  - $\int_a^bf(u)du=G(b)-G(a)$

### Applications

- the scope of the fundamental theorem is huge, but we can give some indication of its use
- if we want to find the integral of $x^n$, we can proceed as follows:
  - the derivative of $x^n$ is $nx^{n-1}$, so the derivative of $x^{n+1}/{n+1}$ will be $x^n$, therefore we can plug in our boundaries and find the area under this curve
  - this is quicker than finding the limit of a sum as defined above
- we can define rules for integrals same as we defined them for derivatives and use the formula
  - the integral of $\sin x$ is $-\cos x$
  - the integral of $\cos x$ is $\sin x$
- an interesting result can be obtained from the formula of the derivative of the inverse tangent, $f'(\tan^{-1}x)=1/(1+x^2)$
  - $\int_0^b1/(1+x^2)dx=\tan^{-1}b$
  - if b = 1, then $tan^{-1}(1)=\pi/4$, so $\pi/4=\int_0^11/(1+x^2)dx$
  - this result leads us to the formula for an alternating series for pi from Leibniz

### Exponential function and the logarithm

- calculus provides a much better basis for the logarithm and exponential functions
  - the usual definition starts with the integral powers $a^n$ of a positive number $a$, then defines $a^{1/n}$ as the nth root of a, then the logarithm of y to the base a $x = \log_ay$ is defined as the inverse of $y = a^x$
- the natural logarithm is defined as the area under the curve $y = 1/u$ from 1 to x
- properties of logarithms:
  - $\log a+\log b = \log ab$
    - we can derive this property using calculus
    - consider a function $k(x)=\log(ax)=\log w = F(w)$ where w is ax
    - $k'(x)=F'(w)f'(x)=a/w=a/ax=1/x$, so $\log(ax)=F(x)+c$
    - we determine c by substituting for x 
    - $F(1)=\log 1 = 0$, so k(1) = c and c = log(a), so $\log(ax)=log(a)+log(x)$
  - $\log 1/x =-\log x$
  - $\log x^r = r\log x$
- since log is a continuous monotone function, there must be some number greater than 1 for which we have log(x) = 1 (this number is $e$)
- we can consider the exponential function (inverse of log), $x = \exp(y)$
  - $\exp(a)*\exp(b)=\exp(a+b)$
  - $a = e^{\log a}$

### Differentiating exponential functions

- the natural exponential function is identical with its derivative $\exp'(y)=dx/dy=1/dy/dx=1/1/x=x=\exp(y)$
- if we differentiate a compound function $f(x)=e^{ax}$, $f'(x)=af(x)$
- $f(x)=a^x,f'(x)=a^x\log a$
- we can also find these explicit formulas as limits by writing them out
  - this also shows us the series for e: $e = 1+1/1!+1/2!+1/3!..$

### Differential equations

- the main role of exponential and trigonometric functions is mathematical analysis and the application to physical problems
- these functions solve the simplest differential equations
- a differential equation has a function as its unknown, e.g. if $u = f(x), u' = f'(x)$, then the equation is $u'=u+\sin(xu)$
- a differential equation may also involve the second derivative or even higher ones
- solving a differential equation is a generalization of finding the primitive function of a given function $u'=g(x)$, e.g. if $u'=x^2$, then $u = x^3/3+c$

### Exponential functions, radioactivity, compound interest

- the differential equation $u'=u$ has the solution $u=e^x$
- the function $u=ce^{kx}$ is the solution to an equation $u'=ku$
- if $x=h(u)$ is the inverse function of $u=f(x)$, then $h'=1/u'=1/ku$
  - $\log u/k$ is a primitive function of 1/ku, so if $h(u)=\log u/k+b$, then $\log u = kx - bk$, $u = e^{kx}e^{-bk}$ or $ce^{kx}$ since the second part is a constant
- the differential equation $u'=u$ governs physical processes in which a quantity u of some substance is a function of the time t and the quantity u is changign at the rate proportional to the instantaneous value of u (e.g. a lot of u changes fast)
  - if we know the initial amount at time 0, we can find the constant by setting t = 0
  - this equation will describe radioactive disintegration
    - $u = u_0e^{kt}$, where $s = t_2-t_1$ is called the half-life
- the phenomenon of compund interest is appoximately exponential: e.g. at3% interest, $u_t=u_0(1+0.03)^t$
  - the exponent is nt where n is the nth part of a year

### Other examples

- the exponential function often occurs in other combinations, e.g. $u = e^{-kx^2}$ which is the solution to $u'=-2kxu$, defines the normal frequency distribution
- the trig functions satisfy differential equations:
  - $u'=-\sin t=-v$
  - $v' = \cos t = u$
  - we can differentiate this again and find
    - $u''=-v'=-u$
    - $v''-u'=-v$
    - both functions u and v of t are solutions to $z''+z=0$ which is a second-order DE
    - this equation with a constant $z''+k^2z=0$ occurs in the study of vibrations
    - this case assumes to resistance, but if we add another term we can add it: $z''+rz'+k^2z=0$
    - these damped vibrations are expressed by the formula $e^{-yt/2}\cos \omega t, e^{-yt/2}\sin \omega t, \omega = \sqrt{k^2-(r/2)^2}$

### Newton’s law of dynamics

- Newton considered the motion of a particle with mass m and space coordinates x(t), y(t) and z(t), so the components of acceleration are second derivatives of those
  - he found that the quantities mx’’, my’’ and mz’’ are components of the force acting on the particle
  - we can combine the formulas for the field of forces with the general law of dynamics (expression of force in terms of motion) and solve the resulting equation
- we can show a simpler illustration with vibrations:
  - assume we have a particle moving along x-axis tied to the origin by an elastic force
  - if we remove the particle from the equilibrium position, the force will pull it back with an intensity proportional to the extension x ($-k^2x$)
  - we also assume friction slows the motion, which is proportional to x’ (the velocity)
  - the total force at any moment is given by $-k^2x-rx'$
  - according to the general principle, $mx''+rx'+k^2x=0$

### Differentiability

- some functions are not differentiable at certain points, e.g. functions that have a corner like $y = x+|x|$ 
- another example would be $y = x\sin(1/x)$
  - this function oscillates infinitely often near x = 0
- differentiability implies continuity, but not the other way around!
- the situation is similar with integrals
  - instead of considering the area under the curve as an obviously existing quantity which can be expressed by the limit of a sum, we define the integral by the limit of a sum
  - the existence of the limit requires analytical proof
- differentiability is a restrictive condition, but the actual process is straightforward
- every continuous function has an integral, but finding it is a difficult task

### Other applications

- the integral can be interpreted in mechanics as expressing the concept of work
- suppose a mass moves along the x-axis under the influence of a force
- this mass is concentrated at the point with coordinate x and force is a function of the position
- if the force is constant, the work is given by (b-a)f
- if the intensity varies with x, the work done is the integral of f(x) from a to b

### Orders of magnitude

- we often encounter sequences $a_n$ which tend to infinity, while other sequences tend to infinity “faster”
- we can make this concept precise by saying that $b_n$ has a higher order of magnitude if the ratio $a_n/b_n$ tends to 0 as n increases
- in many applications it’s important to know the order of magnitude for n! for large values of n
  - we can study the logarithm of n! ($P=\log2+\log3+\log4+...+\log n$)
  - the asymptotic value is given by $n\log(n)$
  - $\int_1^n\log x dx=n\log n-n+1$

### Infinite series and products

- expressing a quantity as an infinite series is a symbol for the statement that s is the limit as n increases of the sequence of partial sums
- some series are functions of the form $b_i=c_ix^i$ with a constant c - these are power series (limits of polynomials representing $S_n=c_0+c_1x+c_2x^2+...c_nx^n$
- an expansion of a function in a power series is an approximation of a function with polynomials
  - we can expand many functions like log, tan etc with polynomials
  - these expansions are special cases of the general formula of Taylor, who aimed at expanding any function in the form of a power eries by finding a law that expresses the coefficients c in therms of the function and its derivatives 

### Euler’s formula

-  one of the most interesting results from Euler is a connection between complex numbers, sine/cosine and exponential functions
- we can start with De Moivre’s formula: $(\cos n\phi+i\sin n\phi)= (\cos \phi+i\sin \phi)^n$
- we can substitute $\phi=x/n$, $(\cos (x/n)+i\sin (x/n))^n$
- if x is given, cos(x/n) will approach 1 for large n and sin(x/n) is asymptotically equal to x/n, so $\cos x +i\sin x=\lim(1+ix/n)^n$ as n tends to infinity
  - the formula for e is very similar = $e^z = lim(1+z/n)^n$ as n tends to infinity
  - so $\cos x + i \sin x = e^{ix}$

### The harmonic series and the zeta function

- a harmonic series is the sum of 1/n for all n
- does this series converge?
- the terms of the series approach 0 as we go, but the series does not converge
- but the series $1+1/2^s+1/3^s+1/4^s...$ can be shown to converge for any value of s over 1
  - $\zeta(s)=lim(1+1/2^s+1/3^s...)$ as n tends to infinity
  - the zeta function is related to prime numbers
  - let p = 2,3,5,7 be any prime, then for s >= 1 $0 < 1/p^s < 1$
  - $1/(1-1/p^s)=1+1/p^s+1/p^{2s}+1/p^{3s}...$
  - if we imagine multiplying the equations for all the primes, we will get
    - one one side, $(1/(1-1/2^s))*(1/(1-1/3^s))...=lim[1/(1-1/p^s)]$
    - and on the other side we get the zeta function (every integer can be expressed by the product of the powers of distinct primes)
    - so the zeta function can be represented by the product
    - the zeta series for 1 diverges to infinity and so we can show that there are infinitely many primes

### Chapter 9: A brief rundown of “recent” developments 

- one of Hilbert’s 23 problems is finding a general algorithm for testing a solution to a Diophantine equation (a polynomial with integer solutions)
  - it has been shown that no such decision algorithm exists
  - a byproduct of this proof was a 23-variable polynomial whose positive values are primes
- Goldbach’s conjecture - every even number greater than 2 is a sum of two primes (the conjecture is that there exist infinitely many primes for which p+2 is also prime)
  - it has been shown using complex analysis and analytic number theory that every sufficiently large odd number is a sum of three primes
  - other methods have improved on this solution
- Riemann hypothesis concerns the zeta function when the variable is complex (if $\zeta(s)=0$ and s is not real, then $s = 1/2+iy$ for some real 1 - e.g. the zeta function has zeros only at complex numbers )
  - some work has been done with the assumption that this hypothesis is true (which could expose a contradiction)
  - the zeros of the zeta function can help define the distribution of prime numbers 
- Fermat’s last theorem $x^n+y^n=z^n$
  - Fermat conjectured that this equation has no non-zero integer solutions for n>= 3
  - the 1994 proof by Wiles is hard, but the general outline is as follows: 
    - the proof relies on elliptic curves, defined by equations like $y^2=ax^3+bx^2+cx+d$
    - the equation can be rewritten as $(x/z)^n+(y/z)^n=1$ so the point with coordinates (x/z,y/z) lies on the Fermat curve $X^n+Y^n=1$
    - the theorem is then the assertion that no rational point can lie on the Fermat curve then n >= 3
    - Frey introduced a curve $y^2=x(x+A^n)(x-B^n)$ which exists only if the theorem is false
    - the way to prove that it cannot exist is to assume that it does and deduce a contradiction 
    - Ribet & Frey showed that the Frey’s curve cannot exist if a big unsolved problem in number theory is true (Taniyama’s conjecture)
      - there is a relationship between the Pythagorean equation $a^2+b^2=c^2$, the unit circle and sin and cos (e.g. Pythagorean equation can be rewritten as (a/c)^2+(b/c)^2=1 which implies that the point (x/c,y/c) lies on the unit circle and $cos^2(\theta)+\sin^2(\theta)=1$ - solving the Pythagorean equastion in integers is equivalent to finding an angle $\theta$ such that both cos and sin of theta are rational numbers (equal to a/c and b/c))
      - the Taniyama conjecture says that a similar kind of idea can be applied to any elliptic curve, but with different functions for sin and cos
    - Wiles realized that Frey’s approach can be used with a particular class of elliptic curves
    - he proved a particular case of the Taniyama conjecture, showing that if M and N are nonzero distinct relatively prime integers such that MN(M-N) is divisible by 16 (this condition makes it semistable), then we can parametrize the elliptic curve $y^2=x(x+M)(x+N)$ by modular functions 
    - if we apply this theorem to Frey’s curve ($M = A^n, N = -B^n$), then $MN(M-N) = -A^nB^nC^n$ and we have to show that it is a multiple of 16
    - at least 1 of A,B,C must be even and we assume n>= 5 -     we show that this is true and the quantity above is a multiple of 16
    - but Ribet has shown that the Taniyama’s conjecture implies that the Frey’s curve cannot be parametrized by modular functions, which is a contradiction so Fermat’s Last Theorem is true
- The Continuum hypothesis states that the cardinal number of the set of all real numbers is the smallest infinite cardinal greater than that of the integers
  - this hypothesis has been shown to be  undecidable
  - the axiomatic method specifies a mathematical object by stating a system of axioms that it satisfies
  - the truth of this hypothesis depends upon the axioms that are chosen for set theorey
- Four color theorem
  - has been proven by checking a lot of cases via computer, but no pencil and paper proof exists
  - the proof of the Five Color Theorem relies on the existence of a “minimal criminal”, e.g. if the 4 color theorem is false, there must be a map that requires 5 colors
    - we can restrict the structure of these criminals and show that they do not exist
  - since then there were many other developments
- Hausdorff dimension and fractals
  - Hausdorff has invented a new definition of dimension, which was forgotten until it was applied to the theory of fractals
  - The Mandelbrot set consists of all complex numbers c such that the sequence $c,c^2+c,(c^2+c)^+c..$ does not tend to infinity
  - the Hausdorff-Besicovitch dimension of a set (a fractal dimension) is a precise quantity that does not need to be an integer
  - we can think of a simpler version of a dimension - a scaling dimension - e.g. 2 copies of a line segment are required to make a segment twice the size, 4 copies of a square are needed to make one twice the size, in general it requires $2^d$ copies of a d-dimensional hypercube to make one twice the size and it requires $c = a^d$ copes to make one a times the size
  - $\log c = d \log a$
  - $d = \log c/\log a$
  - the scaling dimension of the Cantor set is 0.63...
  - the Sierpinski triangle can be doubled in size by assembling 3 copes, so $d = \log 3/\log 2=1.58$
- Knots
  - a link is a set of one or more closed loops in 3D space
  - the individual loops are called the components of the link
  - if there is only one loop, the link is called a knot
  - the central problem in link theory is to find ways to tell whether or not two given links or knots are topologically equivalent 
  - the way to achieve this is to find topological invariants (numbers or objects that do not change when the link is deformed)







