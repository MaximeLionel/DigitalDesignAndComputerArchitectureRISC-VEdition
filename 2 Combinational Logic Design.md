# 2.1 INTRODUCTION
* In digital electronics, a circuit is a network that processes discrete-valued (离散) variables.
* A circuit can be viewed as a black box with:
	![[Pasted image 20250102111020.png|400]]
	* one or more discrete-valued **input** terminals.
	* one or more discrete-valued **output** terminals.
	* a functional specification - the **relationship** between inputs and outputs.
	* a timing specification - the **delay** between inputs changing and outputs responding.
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
		* combines the current input values to compute the output.
	*  A sequential circuit’s outputs depend on both current and previous values of the inputs.
		* depends on the input sequence