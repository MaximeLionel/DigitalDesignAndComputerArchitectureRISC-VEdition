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
* Digital circuits - such as logic gates, restrict the voltages to discrete ranges, which we will use to 
indicate 0 and 1.