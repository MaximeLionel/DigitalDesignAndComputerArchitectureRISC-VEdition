# 2.1 INTRODUCTION
* In digital electronics, a circuit is a network that processes discrete-valued (离散) variables.
* A circuit can be viewed as a black box with:
	![[Pasted image 20250102111020.png|400]]
	* one or more discrete-valued **input** terminals.
	* one or more discrete-valued **output** terminals.
	* a functional specification - the **relationship** between inputs and outputs.
	* a timing specification - the **delay** between inputs changing and outputs responding.
		* It consists of lower and upper bounds on the delay from input to output.
* Circuits are composed of **nodes** and **elements**. 
	* An element is itself a circuit with inputs, outputs, and a specification. 
	* A node is a wire, whose voltage conveys a discrete-valued variable.
		* Nodes are classified as **input, output, or internal**:
			* **Inputs** receive values from the external world. 
			* **Outputs** deliver values to the external world. 
			* **Wires** that are not inputs or outputs are called **internal nodes**.
* Example of elements of nodes:
	![[Pasted image 20250102112409.png|400]]
	* A circuit consists of:
		* 3 elements: E1, E2, and E3.
		* 6 nodes: nodes A, B, and C are inputs. Y and Z are outputs. n1 is an internal node between E1 and E3.
* Digital circuits are classified as **combinational** or **sequential**:
	* A combinational circuit’s outputs depend only on the current values of the inputs.
		* It combines the current input values to compute the output.
		* A combinational circuit is memoryless.
	* A sequential circuit’s outputs depend on both current and previous values of the inputs.
		* It depends on the input sequence.
		* A sequential circuit has memory.
* Example of a combinational circuit with 2 inputs and 1 output:
	![[Pasted image 20250102144731.png|250]]
	* The symbol `CL` inside the box indicates that it is implemented using only combinational logic.
	* Function F is specified to be OR: Y = F(A, B) = A + B.
	* In words, we say that the output Y is a function of the 2 inputs, A and B — namely, Y = A OR B.
* Example of 2 possible implementations for the combinational logic circuit:
	![[Pasted image 20250102145014.png|280]]
* Example of a combinational circuit with multiple outputs:
	![[Pasted image 20250102145113.png|280]]
	* This particular combinational circuit is called a **full adder**.
	* The 2 equations specify the function of the outputs, S and $C_{out}$, in terms of the inputs, A, B, and $C_{in}$.
* Slash notation for multiple signals:
	![[Pasted image 20250102150339.png|300]]
	* A single line with a slash through it and a number next to it to indicate a **bus**, a bundle of multiple signals. The number specifies how many signals are in the bus.
* A circuit is combinational if it consists of interconnected circuit elements such that:
	▸ Every circuit element is itself **combinational**.
	▸ Every node of the circuit is either designated as an **input** to the circuit or connects to exactly one **output** terminal of a circuit element.
	▸ The circuit contains **no cyclic paths**: every path through the circuit visits each circuit node at most once.
* The functional specification of a combinational circuit is usually expressed as a **truth table** or a **Boolean equation**.

## Example 2.1 COMBINATIONAL CIRCUITS
Which of the circuits below are combinational circuits according to the rules of combinational composition?
![[Pasted image 20250102151718.png|700]]

**Solution**:
a is a combinational circuit.
b is not, because of the cyclic path.
c is a combinational circuit.
d is not, because node n6 is not designated as exactly 1 output of the circuit, but 2.
e is a combinational circuit.
f is not, because of the cyclic path.

# 2.2 BOOLEAN EQUATIONS
## 2.2.1 Terminology
* The complement of a variable A is its inverse $\overline{A}$.
	* The variable or its complement is called a **literal**. 
	* For example, A, $\overline{A}$, B, and $\overline{B}$ are literals.
	* We call A the true form of the variable and $\overline{A}$ the complementary form.
* The $AND$ of one or more literals is called a **product** (积项) or an **implicant** (蕴含项).
	* $\overline{A}B$, $A\overline{BC}$, and $B$ are all implicants for a function of 3 variables.
* A **minterm** (最小项) is a product involving **all** of the inputs to the function.
	* $A\overline{BC}$ is a minterm for a function of the three variables A, B, and C but AB is not.
* The $OR$ of one or more literals is called a **sum** （和项）.
* A **maxterm** （最大项） is a sum involving all of the inputs to the function.
	* A + B + C is a maxterm for a function of the 3 variables A, B, and C.
* The order of operations is important when interpreting Boolean equations.
	* In Boolean equations, $NOT$ has the highest precedence followed by $AND$, then $OR$.
	* Example: $\overline{A}B+BC\overline{D} = ((\overline{A})B)+(BC(\overline{D}))$

## 2.2.2 Sum-of-Products Form
* A truth table of $N$ inputs contains $2^N$ rows, one for each possible value of the inputs. 
	* Each row in a truth table is associated with a minterm that is TRUE for that row.
	* Example:
		![[Pasted image 20250102170021.png|350]]

* We can write a Boolean equation for any truth table by summing each of the minterms for which the output, Y, is TRUE.
	* Example 0:
		![[Pasted image 20250103155137.png|400]]
		* Only 1 row (or minterm) for which the output Y is TRUE, shown circled in blue. Thus, $Y = \overline{A}B$.
	* Example 1:
		![[Pasted image 20250103155837.png|400]]
		* A truth table with more than one row in which the output is TRUE. Taking the sum of each of the circled minterms gives $Y =\overline{A}B + AB$.
		* This is called the **sum-of-products (SOP)** canonical form of a function because it is the sum (OR) of products (ANDs forming minterms).
		* The sum-of-products canonical form can also be written in sigma notation using the summation symbol: $F(A,B)=\sum{(m_1,m_3)}$ or $F(A,B)=\sum{(1,3)}$.
	* Example 2:
		![[Pasted image 20250103164626.png|300]]
		* This is a random three-input truth table. 
		* The sum-of-products form of the logic function is: $Y=\overline{A}\overline{B}\overline{C}+A\overline{B}\overline{C}+A\overline{B}C$ or $Y=\sum{(0,4,5)}$

## Example 2.2 SUM-OF-PRODUCTS (SOP) FORM
Ben Bitdiddle is having a picnic. He won’t enjoy it if it rains or if there are ants. Design a circuit that will output TRUE only if Ben enjoys the picnic.

**Solution**:
Inputs:
* A - ants exist.
* R - rainy day.
Output:
* E - Ben enjoys the picnic.

Equations:
$E=\overline{A}\overline{R}$ or $E=\sum{(0)}$
and
$E=\overline{A+B}$
![[Pasted image 20250103164535.png|300]]

## 2.2.3 Product-of-Sums Form
* An alternative way of expressing Boolean functions is the **product-ofsums (POS)** canonical form.
	* Each row of a truth table corresponds to a maxterm that is FALSE for that row.
* The product-of-sums canonical form can be written in pi notation using the product symbol, $\prod$.
* Sum-of-products produces a shorter equation when the output is TRUE on only a few rows of a truth table; product-of-sums is simpler when the output is FALSE on only a few rows of a truth table.

## Example 2.3 PRODUCT-OF-SUMS (POS) FORM
Write an equation in product-of-sums form for the truth table in Figure below.
![[Pasted image 20250103234517.png|400]]

**Solution**:
$Y=(A+B)(\overline{A}+B)=\prod{(M_0,M_2)}=\prod{(0,2)}$

# 2.3 BOOLEAN ALGEBRA (布尔代数)
* You can use **Boolean algebra** to simplify Boolean equations.
	* Variables have only two possible values: 0 or 1.
* Boolean algebra is based on a set of axioms (公理) that we assume are correct.
* Axioms (公理) and theorems (定理) of Boolean algebra obey the principle of duality (对偶性).
	* The prime symbol (′) to denote the dual of a statement.

## 2.3.1 Axioms
![[Pasted image 20250106140442.png|700]]

## 2.3.2 Theorems of One Variable
![[Pasted image 20250106141428.png|700]]
* identity theorem (同一定理):
	![[Pasted image 20250106141536.png|260]]
* null element theorem (零元素定理):
	* 0 is the null element for the AND operation.
	* 1 is the null element for the OR operation.
		![[Pasted image 20250106141802.png|260]]
		* If one input of an AND gate is 0, we can replace the AND gate with a wire that is tied LOW (to 0). 
		* If one input of an OR gate is 1, we can replace the OR gate with a wire that is tied HIGH (to 1).
* Idempotency (幂等定理):
	* A variable $AND$ itself is equal to just itself.
	* A variable $OR$ itself is equal to itself.












