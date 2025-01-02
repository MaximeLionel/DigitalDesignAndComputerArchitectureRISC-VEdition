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




















