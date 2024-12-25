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










