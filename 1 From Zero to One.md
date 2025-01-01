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
* $Y = AB$, read “Y equals A and B”.

## 1.5.4 OR Gate
![[Pasted image 20241226095319.png|200]]

* $Y = A + B$ is pronounced “Y equals A or B”.

## 1.5.5 Other Two-Input Gates
![[Pasted image 20241226100155.png|200]]
* XOR operation is indicated by $\bigoplus$.
* An N-input XOR gate is sometimes called a **parity gate** and produces a TRUE output if an odd number of inputs are TRUE.

![[Pasted image 20241226100357.png|200]]
* NAND gate performs NOT AND.

![[Pasted image 20241226100428.png|200]]
* NOR gate performs NOT OR.

## 1.5.6 Multiple-Input Gates

# 1.6 BENEATH THE DIGITAL ABSTRACTION

## 1.6.1 Supply Voltage
* The lowest voltage in the system is 0 V, also called ground or GND. 
* The highest voltage in the system comes from the power supply and is usually called $V_{DD}$.

## 1.6.2 Logic Levels
![[Pasted image 20241226101700.png|800]]
* The mapping of a continuous variable onto a discrete binary variable is done by defining **logic levels**.
* The first gate is called the **driver** and the second gate is called the **receiver**.
	* The output of the driver is connected to the input of the receiver.
* The driver produces a $LOW (0)$ output in the range of 0 to $V_{OL}$ or a $HIGH (1)$ output in the range of $V_{OH}$ to $V_{DD}$.
	* If the receiver gets an input in the range of 0 to $V_{IL}$, it will consider the input to be $LOW$. 
	* If the receiver gets an input in the range of $V_{IH}$ to $V_{DD}$, it will consider the input to be $HIGH$. 
	* If the receiver’s input should fall in the forbidden zone between $V_{IL}$ and $V_{IH}$, the behavior of the gate is unpredictable. 
* $V_{OH}$, $V_{OL}$, $V_{IH}$, and $V_{IL}$ are called the output and input high and low logic levels.

## 1.6.3 Noise Margins
$NM_L= V_{IL} - V_{OL}$
$NM_H = V_{OH} - V_{IH}$
* The noise margin (NM) is the amount of noise that could be added to a worst-case output such that the signal can still be interpreted as a valid input.
![[Pasted image 20241226110959.png|700]]

### Example 1.18 CALCULATING NOISE MARGINS
Consider the inverter circuit of Figure below. $V_{O1}$ is the output voltage of inverter $I1$, and $V_{I2}$ is the input voltage of inverter $I2$. Both inverters have the following characteristics: $V_{DD} = 5V$, $V_{IL} = 1.35V$, $V_{IH} = 3.15V$, $V_{OL} = 0.33V$, and $V_{OH} = 3.84V$. What are the inverter low and high noise margins? Can the circuit tolerate $1V$ of noise between $V_{O1}$ and $V_{I2}$ ?
![[Pasted image 20241226111532.png|500]]

**Solution**:
$NM_L=V_{IL}-V_{OL}=1.35-0.33=1.02V$
$NM_H=V_{OH}-V_{IH}=3.84-3.15=0.69V$

When the output is LOW ($NM_L = 1.02V$), the circuit can tolerate $1V$ of noise. 
When the output is HIGH ($NM_H = 0.69V$), the circuit cannot tolerate $1V$ of noise. 

## 1.6.4 DC Transfer Characteristics (直流传输特性)
* The **DC transfer characteristics** of a gate describe the output voltage as a function of the input voltage when the input is changed slowly enough that the output can keep up.
* An ideal inverter（反相器） would have an abrupt switching threshold at $V_{DD}/2$.
	![[Pasted image 20241226161400.png|600]]
	* For $V(A) < V_{DD}/2$, $V(Y) = V_{DD}$. 
	* For $V(A) > V_{DD}/2$, $V(Y) = 0$. 
	* $V_{IH} = V_{IL} = V_{DD}/2$. 
	* $V_{OH} = V_{DD}$ and $V_{OL} = 0$.
* A real inverter changes more gradually between the extremes.
	![[Pasted image 20241226162515.png|600]]
	* When the input voltage $V(A)$ is 0, the output voltage $V(Y) = V_{DD}$. 
	* When $V(A) = V_{DD}$, $V(Y) = 0$.
	* However, the transition between these endpoints is smooth and may not be centered at exactly $V_{DD}/2$.
	* **Unity gain points** - a reasonable place to choose the logic levels is where the slope of the transfer characteristic $dV(Y)/dV(A) = −1$.
	* Choosing logic levels at the unity gain points usually **maximizes the noise margins**. 
		* If $V_{IL}$ were reduced, $V_{OH}$ would only increase by a small amount. 
		* If $V_{IL}$ were increased, $V_{OH}$ would drop precipitously.

## 1.6.5 The Static Discipline
* To avoid inputs falling into the forbidden zone, digital logic gates are designed to conform to the static discipline.
	* The static discipline requires that, given logically valid inputs, every circuit element will produce logically valid outputs.
* Logic levels of 5V and 3.3V logic families:
	![[Pasted image 20241226173004.png|700]]
### Example 1.19 LOGIC FAMILY COMPATIBILITY
Which of the logic families in Table above can communicate with each other reliably?

Solution:
![[Pasted image 20241226223914.png|600]]


# Exercises
## Exercise 1.4 
An analog voltage is in the range of 0–5V. If it can be measured with an accuracy of ±50mV, at most how many bits of information does it convey?

**Solution**:
5 V = 5000 mV
(5000 mV + 50 mV) / 50 mV = 101
$\log_2 101 = 6.7\approx7$
So it needs 7 bits of information.

## Exercise 1.5 
A classroom has an old clock on the wall whose minute hand broke off.
(a) If you can read the hour hand to the nearest 15 minutes, how many bits of information does the clock convey about the time?
(b) If you know whether it is before or after noon, how many additional bits of information do you know about the time?

**Solution**:
(a)
12 hours / 15 minutes = 48
$log_2 48 = 5.6 \approx 6$

(b)
1 more bit to split 1 day into 2 halves indicating before or after noon.

## Exercise 1.6 
The Babylonians developed the sexagesimal (base 60) number system about 4000 years ago. How many bits of information is conveyed with one sexagesimal digit? How do you write the number $4000_{10}$ in sexagesimal?

**Solution**:
$log_2 60=5.9\approx 6$ bits
6 bits is required for one sexagesimal digit.

Bit 0: $4000 \mod 60 = 40$
Bit 1: $(4000-40)/60=66$, $66\mod60=6$
Bit 2: $6\mod60=6$

So the $4000_{10}$ in sexagesimal is (6,6,40).

## Exercise 1.7 
How many different numbers can be represented with 16 bits?

**Solution**:
$2^{16}=65536$

## Exercise 1.8 
What is the largest unsigned 32-bit binary number?

**Solution**:
$2^{32}-1=4294967295$

## Exercise 1.9 
What is the largest 16-bit binary number that can be represented with
(a) unsigned numbers?
(b) two’s complement numbers?
(c) sign/magnitude numbers?

**Solution**:
(a) $2^{16}-1=65535$
(b) $2^{15}-1=32767$
(c) $2^{15}-1=32767$

## Exercise 1.10 
What is the largest 32-bit binary number that can be represented with
(a) unsigned numbers?
(b) two’s complement numbers?
(c) sign/magnitude numbers?

**Solution**:
(a) $2^{32}-1=4294967295$
(b) $2^{31}-1=2147483647$
(c) $2^{31}-1=2147483647$

## Exercise 1.11 
What is the smallest (most negative) 16-bit binary number that can be represented with
(a) unsigned numbers?
(b) two’s complement numbers?
(c) sign/magnitude numbers?

**Solution**:
(a) 0
(b) $-2^{15}=-32768$
(c) $-2^{15}+1=-32767$

## Exercise 1.12 
What is the smallest (most negative) 32-bit binary number that can be represented with
(a) unsigned numbers?
(b) two’s complement numbers?
(c) sign/magnitude numbers?

**Solution**:
(a) 0
(b) $-2^{31}=-2147483648$
(c) $-2^{31}+1=-2147483647$




