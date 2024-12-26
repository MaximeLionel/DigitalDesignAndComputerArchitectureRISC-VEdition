* Starting at the beginning with 1’s and 0’s and leading through to the design of a microprocessor.
* Hardware description languages (HDLs) are at the center of modern digital design practices.

# 1.1 THE GAME PLAN
# 1.2 THE ART OF MANAGING COMPLEXITY
* You will need to learn to manage complexity to understand how to build a microprocessor without getting mired in a morass of detail.

## 1.2.1 Abstraction
* The critical technique for managing complexity is **abstraction**: hiding details when they are not important.
### Levels of abstraction for an electronic computing system
![[Pasted image 20241225141732.png|500]]
* Physics:
	* At the lowest level of abstraction is the physics, the motion of electrons (电子). 
	* The behavior of electrons is described by quantum mechanics （量子力学） and Maxwell’s equations （麦克斯韦方程组）.
* Devices:
	* Our system is constructed from electronic devices such as  transistors (or vacuum tubes, once upon a time). 
	* These devices have well-defined connection points called **terminals** and can be modeled by the relationship between voltage and current as measured at each terminal.
	* By abstracting to this device level, we can ignore the individual electrons.
* Analog circuits (模拟电路):
	* devices  are assembled to create components such as amplifiers. 
	* Analog circuits input and output a continuous range of voltages.
* Digital circuits - such as logic gates, restrict the voltages to discrete ranges, which we will use to indicate 0 and 1.
* Microarchitecture - links the logic and architecture levels of abstraction.
	* such as ALU, registers, cache, pipeline.
* Architecture - describes a computer from the programmer’s perspective. 
	* For example, the Intel x86 architecture used by microprocessors in most personal computers (PCs) is defined by a set of instructions and registers (memory for temporarily storing variables) that the programmer is allowed to use.
	* Microarchitecture  involves combining logic elements to execute the instructions defined by the architecture.
* Operating system - Moving into the software realm, the operating system handles low-level details, such as accessing a hard drive or managing memory.
* Applications.

## 1.2.2 Discipline

## 1.2.3 The Three -Y’s
* Hierarchy involves dividing a system into modules, then further subdividing each of these modules until the pieces are easy to understand.
* Modularity states that modules have well-defined functions and interfaces so that they connect easily without unanticipated side effects.
* Regularity seeks uniformity among modules. Common modules are reused many times, reducing the number of distinct modules that must be designed.

# 1.3 THE DIGITAL ABSTRACTION

# 1.4 NUMBER SYSTEMS
## 1.4.1 Decimal Numbers
## 1.4.2 Binary Numbers
![[Pasted image 20241225153232.png|600]]
![[Pasted image 20241225153308.png|800]]

## 1.4.3 Hexadecimal Numbers
![[Pasted image 20241225153417.png|700]]


## 1.4.4 Bytes, Nibbles, and All That Jazz
* A group of four bits, or half a byte, is called a **nibble**.
* Microprocessors handle data in chunks called **words**.
	* The size of a word depends on the architecture of the microprocessor.
	* In 2021, most computers had 64-bit processors, indicating that they operate on 64-bit words.
* Least and most significant bits and bytes:
	![[Pasted image 20241225154814.png|600]]
	* least significant bit (lsb) / most significant bit (msb) / least significant byte (LSB) / most significant byte (MSB).
* Some logics of powers of 10 and powers of 2:
	* the term **kilo** indicates $2^{10} \approx 10^3$.
	* the term **mega** indicates $2^{20} \approx 10^6$.
	* the term giga indicates $2^{30} ≈ 10^9$.
	* KB or KiB / MB or MiB / GB or GiB.
	* Kb or Kib / Mb or Mib / Gb or Gib.

### Example 1.6 ESTIMATING POWERS OF TWO
Find the approximate value of $2^{24}$ without using a calculator.

**Solution**:
$2^{24} = 2^{20} × 2^4$
$2^{20} \approx 1 million$ and $2^4 = 16$ 
So, $2^{24} \approx 16 million$.

## 1.4.5 Binary Addition
* Addition examples showing carries: (a) decimal (b) binary
	![[Pasted image 20241225161143.png|400]]

## 1.4.6 Signed Binary Numbers
* 2 most widely employed methods to represent signed binary numbers are called **sign/magnitude** and **two’s complement**.
### Sign/Magnitude Numbers
* Sign/magnitude numbers (符号数/幅值数) are intuitively appealing because they match our custom of writing negative numbers with a minus sign followed by the magnitude.
* An N-bit sign/magnitude number uses the most significant bit as the sign and the remaining N − 1 bits as the magnitude (absolute value).
* A sign bit of 0 indicates positive and a sign bit of 1 indicates negative.
* An N-bit sign/magnitude number spans the range $[−2^{N−1} + 1, 2^{N−1} − 1]$.
* Sign/magnitude numbers are slightly odd in that both +0 and −0 exist. Both indicate zero.

#### Example 1.9 SIGN/MAGNITUDE NUMBERS
Write 5 and −5 as 4-bit sign/magnitude numbers.

Solution:
$5_{10}=0101_2$
$-5_{10}=1101_2$

### Two’s Complement Numbers
* Two’s complement numbers are identical to unsigned binary numbers except that the most significant bit position has a weight of $−2^{N−1}$ and $2^{N−1}$.
* Reversing the sign method:
	* inverting the bits in the number
	* adding 1 to the least significant bit position. 
* the range of an N-bit two’s complement number spans $[−2^{N−1}, 2^{N−1} − 1]$.
* The weird number - the most negative number $10…000^2 = −2^{N−1}$. 
	* Its two’s complement is found by inverting the bits (producing $01…111^2$) and adding 1, which produces $10…000^2$, the weird number, again. 
	* Hence, this negative number has no positive counterpart.

#### Example 1.10 TWO’S COMPLEMENT REPRESENTATION OF A NEGATIVE NUMBER
Find the representation of $−2_{10}$ as a 4-bit two’s complement number.

Solution:
$2_{10}=0010_2$
$-2_{10}=1101_2+1_2=1110_2$

#### Example 1.11 VALUE OF NEGATIVE TWO’S COMPLEMENT NUMBERS
Find the decimal value of the 4-bit two’s complement number 0x9 (i.e., 10012).

Solution:
To reverse the sign bit of $1001_2$:
* reversing all bits: $0110_2$
* adding 1 to lsb: $0111_2$
* transit to decimal: $0111_2 = 7_{10}$
Therefore, the decimal value of 0x9 is $-7_{10}$

* when adding N-bit numbers, the carry out of the Nth bit (i.e., the 
N + 1th result bit) is discarded.

#### Example 1.12 ADDING TWO’S COMPLEMENT NUMBERS
Compute (a) $−2_{10} + 1_{10}$ and (b) $−7_{10} + 7_{10}$ using two’s complement numbers.

Solution:
(a) $−2_{10} + 1_{10} = 1110_2 + 0001_2 = 1111_2 = −1_{10}$
(b) $−7_{10} + 7_{10} = 1001_2 + 0111_2 = 10000_2$. 
The 5th bit is discarded, leaving the correct 4-bit result $0000_2$.

* Subtraction is performed by taking the two’s complement of the second number, then adding.

#### Example 1.13 SUBTRACTING TWO’S COMPLEMENT NUMBERS
Compute (a) $5_{10} − 3_{10}$ and (b) $3_{10} − 5_{10}$ using 4-bit two’s complement numbers.

Solution: 
(a) 
$3_{10} = 0011_2$
$−3_{10} = 1101_2$ 
$5_{10} + (−3_{10}) = 0101_2 + 1101_2 = 0010_2 = 2_{10}$
Note that the carry out of the most significant position is discarded because the result is stored in four 
bits. 

(b) 
$−5_{10} = 1011_2$ 
$3_{10} + (−5_{10}) = 0011_2 + 1011_2 = 1110_2 = −2_{10}$

#### Example 1.14 ADDING TWO’S COMPLEMENT NUMBERS WITH OVERFLOW
Compute $4_{10} + 5_{10}$ using 4-bit two’s complement numbers. Does the result 
overflow?

Solution: 
$4_{10} + 5_{10} = 0100_2 + 0101_2 = 1001_2 = −7_{10}$
* The result overflows the range of 4-bit positive two’s complement numbers, producing an incorrect negative result. 
* If the computation had been done using 5 or more bits, the result $01001_2 = 9_{10}$ would have been correct.


* **Sign extension** - When a two’s complement number is extended to more bits, the sign bit must be copied into the most significant bit positions.

### Comparison of Number Systems
* The 3 most commonly used binary number systems: **unsigned**, **two’s complement**, and **sign/magnitude**.
* Range of N-bit numbers:
	![[Pasted image 20241225173557.png|600]]
* Number line and 4-bit binary encodings:
	![[Pasted image 20241225173641.png|1000]]
	* For sign/Magnitude, 0 is represented by both 0000 and 1000.

# 1.5 Logic Gates
* Logic gates are simple digital circuits that take one or more binary inputs and produce a binary output.
* A truth table lists inputs on the left and the corresponding output on the right.
* A Boolean equation is a mathematical expression using binary variables.
## 1.5.1 NOT Gate
![[Pasted image 20241226085614.png|200]]
* A NOT gate has one input, A, and one output, Y.
* $Y=\overline{A}$ is read “Y equals NOT A.” The NOT gate is also called an **inverter** (反相器).

## 1.5.2 Buffer
![[Pasted image 20241226090424.png|200]]
* The one-input logic gate above is called a **buffer**.
* The triangle symbol indicates a buffer. A circle on the output is called a bubble and indicates **inversion**:
	![[Pasted image 20241226095135.png|200]]

## 1.5.3 AND Gate
![[Pasted image 20241226095221.png|200]]
* Y = AB, read “Y equals 
A and B,” b






















