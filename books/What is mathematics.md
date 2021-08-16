## What is mathematics?

- basic elements are antithetic: logic, intuition, analysis, construction, generality, individuality
- history begins in the East in 2000 BC and then in ancient Greece
- 17th century brought about a revolution that moved from axiomatic certainty to differential and integral calculus
- 19th century - return of the classical ideal of precision and proof
- mathematics is not just a system of conclusions and postulates
- it’s important to remove metaphysics sometimes - the concepts may not have a meaning “in themselves”
  - in the 19th century, the idea that mechanical forces and movements of particles are things “in themselves” and electricity, light and magnetism should be reduced to them (just like heat)
- the only relevant assetions concerning mathematical objects do not refer to reality (we don’t need to discuss or concern ourselves with what points, lines and numbers actually are)

### Natural numbers

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

- most statements in number theory are concerned not with individual numbers, but with 



