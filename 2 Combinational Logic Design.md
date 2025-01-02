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






















