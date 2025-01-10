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
	![[Pasted image 20250106142535.png|260]]
* Involution (卷绕):
	![[Pasted image 20250106142720.png|300]]
* The complement theorem (补充定理):
	* A variable $AND$ its complement is 0.
	* A variable $OR$ its complement is 1.
	![[Pasted image 20250106142930.png|260]]

## 2.3.3 Theorems of Several Variables
![[Pasted image 20250106143044.png|1100]]
* Commutativity and associativity.
* The distributivity theorem.
* The covering, combining, and consensus theorems.
* De Morgan’s Theorem explains that the complement of the product of all the terms is equal to the sum of the complement of each term.
	* A NAND gate is equivalent to an OR gate with inverted inputs.
	* A NOR gate is equivalent to an AND gate with inverted inputs
		![[Pasted image 20250106144257.png|400]]
		* The inversion circle is called a bubble.
		* Imagine that “pushing” a bubble through the gate causes it to come out at the other side and flips the body of the gate from AND to OR or vice versa.

## Example 2.4 DERIVE THE PRODUCT-OF-SUMS FORM
Figure below shows the truth table for a Boolean function Y and its complement Y. Using De Morgan’s Theorem, derive the product-of-sums canonical form of $Y$ from the sum-of-products form of $\overline{Y}$.
![[Pasted image 20250106145615.png|250]]

**Solution**:
$\overline{Y}=\overline{A}\overline{B}+\overline{A}B$
$\overline{\overline{Y}}=\overline{\overline{A}\overline{B}+\overline{A}B}=(A+B)(A+\overline{B})=Y$'=

## 2.3.4 The Truth Behind It All
* In Boolean algebra, proofs of theorems with a finite number of variables are easy: just show that the theorem holds for all possible values of these variables. 
	* This method is called ==perfect induction== (完全归纳法) and can be done with a truth table.

## Example 2.5 PROVING THE CONSENSUS THEOREM USING PERFECT INDUCTION
Prove the consensus theorem, T11, from Table below.
![[Pasted image 20250107110936.png|860]]

Solution:
![[Pasted image 20250107111806.png|500]]


## 2.3.5 Simplifying Equations
* The theorems of Boolean algebra help us simplify Boolean equations.
* The basic principle of simplifying **sum-of-products** equations is to combine terms using the relationship $PA+P\overline{A}= P$.
* We define an equation in sum-of-products form to be ==minimized== if it uses the fewest possible **implicants** (蕴含项).
	* An implicant is called a ==prime implicant== if it cannot be combined with any other implicants in the equation to form a new implicant with fewer literals. 
	* The implicants in a minimal equation must all be prime implicants.
* Simplifying reduces the number of gates used to physically implement the function, thus making it smaller, cheaper, and possibly faster.

## Example 2.6 EQUATION MINIMIZATION
Minimize Equation 2.3: $\overline{A}\overline{B}\overline{C} +A\overline{B}\overline{C} + A\overline{B}C$.

**Solution**:
Idempotency theory: B + B = B
We get that: $\overline{A}\overline{B}\overline{C} +A\overline{B}\overline{C} + A\overline{B}C=\overline{A}\overline{B}\overline{C} +A\overline{B}\overline{C}+A\overline{B}\overline{C} + A\overline{B}C$
Combining theory: $B\cdot C+B\cdot \overline{C}=B$
We get that: $\overline{A}\overline{B}\overline{C} +A\overline{B}\overline{C} + A\overline{B}C=\overline{A}\overline{B}\overline{C} +A\overline{B}\overline{C}+A\overline{B}\overline{C} + A\overline{B}C=\overline{BC}+A\overline{B}$

# 2.4 FROM LOGIC TO GATES
* A **schematic** (示意图) is a diagram of a digital circuit showing the elements and the wires that connect them.
* Example - $Y =\overline{ABC} +  A\overline{BC} + A\overline{B}C$
	![[Pasted image 20250107135637.png|550]]
* Rules:
	* Inputs are on the left (or top) side of a schematic.
	* Outputs are on the right (or bottom) side of a schematic.
	* Whenever possible, gates should flow from left to right.
	* Straight wires are better to use than wires with multiple corners.
	* Wires always connect at a T junction.
		![[Pasted image 20250107144010.png|250]]
	* A dot where wires cross indicates a connection between the wires.
		![[Pasted image 20250107144034.png|250]]
	* Wires crossing without a dot make no connection.
		![[Pasted image 20250107144058.png|250]]
* Any Boolean equation in sum-of-products form can be drawn as a schematic in a systematic way, which is called a **programmable logic array (PLA)**:
	1. Draw columns for the inputs. 
	2. Place inverters in adjacent columns to provide the complementary inputs if necessary. 
	3. Draw rows of AND gates for each of the minterms. 
	4. For each output, draw an OR gate connected to the minterms related to that output.
* The table below shows an implementation of the simplified equation we found using Boolean algebra - $Y=\overline{BC}+A\overline{B}$
	![[Pasted image 20250107154422.png|400]]
* Reduce the number of gates even further (albeit by a single inverter) by taking advantage of **inverting gates**.
	![[Pasted image 20250107154851.png|400]]
* Many circuits have multiple outputs, each of which computes a separate Boolean function of the inputs.

## Example 2.7 MULTIPLE-OUTPUT CIRCUITS
The dean, the department chair, the teaching assistant, and the dorm social chair each use the auditorium from time to time. Unfortunately, they occasionally conflict, leading to disasters such as the one that occurred when the dean’s fundraising meeting with crusty trustees happened at the same time as the dorm’s BTB1 party. Alyssa P. Hacker has been called in to design a room reservation system.

The system has 4 inputs, $A_3$, …, $A_0$, and 4 outputs, $Y_3$, …, $Y_0$. These signals can also be written as $A_{3:0}$ and $Y_{3:0}$. Each user asserts her input when she requests the auditorium for the next day. The system asserts at most one output, granting the auditorium to the highest priority user. The dean, who is paying for the system, demands highest priority (3). The department chair, teaching assistant, and dorm social chair have decreasing priority.

Write a truth table and Boolean equations for the system. Sketch a circuit that performs this function.

Solution:
Firstly, we write a truth table based on the requirements:
![[Pasted image 20250107172246.png|400]]
Secondly, draft the equation based on the truth table:
* $Y_3$ is TRUE whenever $A_3$ is asserted - $Y_3 = A_3$. 
* $Y_2$ is TRUE if $A_2$ is asserted and $A_3$ is not asserted - $Y_2=\overline{A_3}A_2$.
* $Y_1$ is TRUE if $A_1$ is asserted and neither $A_3$ or $A_2$ is asserted - $Y_1=\overline{A_3A_2}A_1$.
* $Y_0$ is TRUE if $A_0$ is asserted and neither $A_3$ or $A_2$ or $A_1$ is asserted - $Y_1=\overline{A_3A_2A_1}A_0$.

Thirdly, we draw the schematic below:
![[Pasted image 20250107173401.png|300]]


Also we can simplify the truth table bring in 'don't cares':
![[Pasted image 20250107173526.png|450]]

This function is called a **four-input priority circuit** (四输入优先级电路).

# 2.5 MULTILEVEL COMBINATIONAL LOGIC
* Logic in sum-of-products form is called **two-level logic** because it consists of literals connected to a level of AND gates connected to a level of OR gates.
* **Bubble pushing** is especially helpful in analyzing and designing multilevel circuits.

## 2.5.1 Hardware Reduction
* An N-input XOR produces a TRUE output when an odd number of inputs are TRUE.
* Example - a 3-input XOR:
	![[Pasted image 20250108092137.png|600]]
	* From the truth table, we read off a Boolean equation in sum-of-products form: $Y = \overline{AB}C+\overline{A}B\overline{C}+A\overline{BC}+ABC$ 
	* The 3-input XOR can be built out of a cascade of 2-input XORs: A ⊕ B ⊕ C = (A ⊕ B) ⊕ C
		![[Pasted image 20250108093106.png|250]]
* An 8-input XOR would require 128 ($2^{(8-1)}$) 8-input AND gates and one 128-input OR gate for a two-level sum-of-products implementation.
	* A much better option is to use a tree of 2-input XOR gates.
		![[Pasted image 20250108101211.png|300]]

## 2.5.2 Bubble Pushing
* Multilevel circuit using $NANDs$ and $NORs$:
	![[Pasted image 20250108101716.png|400]]
* Bubble pushing is a helpful way to redraw these circuits so that the bubbles cancel out and the function can be more easily determined.
	* Begin at the output of the circuit and work toward the inputs.
	* Push any bubbles on the final output back toward the inputs so that you can read an equation in terms of the output ($Y$) instead of the complement of the output ($\overline{Y}$).
	* Working backward, draw each gate in a form so that bubbles cancel. 
		* If the current gate has an input bubble, draw the preceding gate with an output bubble. 
		* If the current gate does not have an input bubble, draw the preceding gate without an output bubble.
* Example - bubble-pushed circuit.
		![[Pasted image 20250108101856.png|450]]
	a. Push the output bubble back to form an OR with inverted inputs.
	b. Working to the left, the rightmost gate has an input bubble that cancels with the output bubble of the middle NAND gate, so no change is necessary.
	c. The middle gate has no input bubble, so we transform the leftmost gate to have no output bubble.
* Now, all of the bubbles in the circuit cancel except at the inputs, so the function can be read by inspection in terms of ANDs and ORs of true or complementary inputs: $Y =\overline{AB}C+\overline{D}$.

## Example 2.8 BUBBLE PUSHING FOR CMOS LOGIC
Most designers think in terms of AND and OR gates, but suppose you would like to implement the circuit in figure below in CMOS logic, which favors NAND and NOR gates. Use bubble pushing to convert the circuit to NANDs, NORs, and inverters.
![[Pasted image 20250108111336.png|300]]

**Solution**:
![[Pasted image 20250108111456.png|900]]

# 2.6 X’S AND Z’S, OH MY
* Boolean algebra is limited to 0’s and 1’s. However, real circuits can also have illegal and floating values, represented symbolically by X and Z.
## 2.6.1 Illegal Value: X
* The symbol X indicates that the circuit node has an **unknown or illegal** value.
	* This commonly happens if it is being driven to both 0 and 1 at the same time.
* Example:
	![[Pasted image 20250108144139.png|200]]

	* Node Y is driven both HIGH and LOW, which is called **contention**.
* X values are also sometimes used by circuit simulators to indicate an **uninitialized value**.
* To clarify:
	* When X appears in a truth table, it indicates that the value of the variable in the truth table is unimportant (can be either 0 or 1, don't cares). 
	* When X appears in a circuit, it means that the circuit node has an unknown or illegal value.

## 2.6.2 Floating Value: Z
* The symbol Z indicates that a node is being driven **neither HIGH nor LOW**.
	* The node is said to be floating, high impedance, or high Z.
* A floating node might be 0, might be 1, or might be at some voltage in between, depending on the history of the system. 
* One common way to produce a floating node is to forget to connect a voltage to a circuit input or to assume that an unconnected input is the same as an input with the value of 0.
* Tristate buffer:
	* 3 output states - input A, output Y, and enable E.
	* 3 possible output states - HIGH (1), LOW (0), and floating (Z).
	* When the enable is TRUE, the tristate buffer acts as a simple buffer, transferring the input value to the output. 
	* When the enable is FALSE, the output is allowed to float (Z).
	* Active high enable - when the enable is HIGH (1), the buffer is enabled.
		![[Pasted image 20250109092931.png|200]]
	* Active low enable - When the enable is LOW (0), the buffer is enabled. 
		![[Pasted image 20250109093008.png|200]]
* Tristate buffers are commonly used on busses that connect multiple chips.
	* Example - 
		![[Pasted image 20250109094111.png|450]]
		* A microprocessor, a video controller, and an Ethernet controller might all need to communicate with the memory system in a personal computer. 
		* Each chip can connect to a shared memory bus using tristate buffers.
		* Only one chip at a time is allowed to assert its enable signal to drive a value onto the bus.

# 2.7 KARNAUGH MAPS
* Karnaugh maps (K-maps) are a graphical method for simplifying Boolean equations.
* K-maps work well for problems with up to 4 variables.
* The figure below shows the truth table and K-map for a 3-input function.
	![[Pasted image 20250109095156.png|800]]
	* Each square, or minterm, differs from an adjacent square by a change in a single variable. 
	* The adjacent squares share all the same literals except one, which appears in true form in one square and in complementary form in the other.
		* For example, the squares representing the minterms $\overline{ABC}$ and $\overline{AB}C$ are adjacent and differ only in the variable C.
	* A and B combinations in the top row are in a peculiar order: ==00, 01, 11, 10==. This order is called ==a Gray code==.
	* The K-map also “wraps around.” (环绕的) The squares on the far right are effectively adjacent to the squares on the far left in that they differ only in one variable, A.

## 2.7.1 Circular Thinking
* K-maps help us do this simplification graphically by circling 1’s in adjacent squares.
	![[Pasted image 20250109165554.png|300]]
* For each circle, we write the corresponding implicant.
* Variables whose true and complementary forms are both in the circle are excluded from the implicant - $\overline{ABC}+\overline{AB}C=\overline{AB}$.
	* The variable C has both its true form (1) and its complementary form (0) in the circle.
	* In other words, Y is TRUE when A = B = 0, independent of C.
	* So, the implicant is $\overline{AB}$.

## 2.7.2 Logic Minimization with K-Maps
* For Logic Minimization with K-Maps, each circle should be as large as possible. Then, read off the implicants that were circled.
* Each circle on the K-map represents an implicant. The largest possible circles are prime implicants.
* Rules for finding a minimized equation from a K-map：
	* Use the fewest circles necessary to cover all the 1’s.
	* All the squares in each circle must contain 1’s.
	* Each circle must span a rectangular block that is a power of 2 (i.e., 1, 2, or 4) squares in each direction.
	* Each circle should be as large as possible.
	* A circle may wrap around the edges of the K-map.
	* A 1 in a K-map may be circled multiple times if doing so allows fewer circles to be used.

## Example 2.9 MINIMIZATION OF A THREE-VARIABLE FUNCTION USING A K-MAP
Suppose we have the function Y = F(A, B, C) with the K-map shown in Figure below. Minimize the equation using the K-map.
![[Pasted image 20250110102259.png|400]]


**Solution**:
![[Pasted image 20250110105516.png|400]]

## Example 2.10 SEVEN-SEGMENT DISPLAY DECODER
A seven-segment display decoder takes a 4-bit data input $D_{3:0}$ and produces seven outputs to control light-emitting diodes to display a digit from 0 to 9. The seven outputs are often called segments a through g, or $S_a$–$S_g$, as defined in Figure below. The digits are shown in Figure below. Write a truth table for the outputs, and use K-maps to find Boolean equations for outputs $S_a$ and $S_b$. Assume that illegal input values (10–15) produce a blank readout.
![[Pasted image 20250110110248.png|300]]
![[Pasted image 20250110110327.png|800]]

**Solution**:
Truth table:
![[Pasted image 20250110110651.png|700]]

K-map of $S_a$:
![[Pasted image 20250110110741.png|500]]

## 2.7.3 Don’t Cares
* “don’t care” entries for truth table inputs are to:
	* reduce the number of rows in the table when some variables do not affect the output.
	* be indicated by the symbol X, which means that the entry can be either 0 or 1.
* In a K-map, X’s allow for even more logic minimization. 
	* If Xs help cover the 1’s with fewer or larger circles, they can be circled.
	* If Xs are not helpful, they do not have to be circled.

## Example 2.11 SEVEN-SEGMENT DISPLAY DECODER WITH DON’T CARES
Repeat Example 2.10 if we don’t care about the output values for illegal input values of 10 to 15.

**Solution**:
![[Pasted image 20250110112445.png|400]]

# 2.8
* a full adder:




