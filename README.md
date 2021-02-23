# A Low Power, Compact Size, Supply Independent Bandgap Reference

## Abstract
In analog circuits we need a constant voltage which is independent of supply voltage as well as temperature. In this paper, we present a BGR (Bandgap Reference) for solving the above purpose. This bandgap reference circuit can be made using current mirrors and Op-amp. This circuit is implemented in 0.18um technology. We achieved a constant voltage of 1.2V and tempco of approximately 12ppm/0C. Temperature variations, we used from 0-850C. We here present the schematic and layout with pre and post layout simulations.

## Introduction
Voltage references have a major impact on the performance and accuracy of analog systems. They shouldn’t vary much with supply voltage and temperature. There are various ways of getting a constant voltage in power supplies or when the input voltage is higher than the output. Some of the methods of obtaining the constant voltage include a). using a Zener diode that breaks down at a known voltage when reverse biased, b) Using the threshold voltage of MOS, c)Cancelling the negative temperature dependence of pn junction (complementary to absolute temperature, CTAT) with positive temperature dependence (Proportional to absolute temperature PTAT). CTAT and PTAT provide more stable and efficient constant voltages. Thus, we have used this concept in our project.    
The bandgap reference circuit is obtained by the addition of CTAT and PTAT in the bandgap core. These are further implemented using pnp BJTs which act as diode, rnp1h (resistances in 0.18um CMOS process) and Mosfets. A startup circuit is also designed for the self-biased BGR. The OPAMP circuit is also implemented in this Bandgap reference. The whole circuit was then simulated using SPECTRE to obtain the desired waveforms. The layout was done and the post-layout simulation was carried out to tabulate the data obtained thereafter.

## Circuit Description
To generate current reference and voltage reference, different circuits were implemented and their tempco values were calculated to provide us a clear picture of current and voltage variations with respect to temperature. In simple current mirror, ideal current source is used. Tempco value of simple current mirror circuit is found to be 5.14ppm/0C. To implement this circuit practically, a resistance(100K) is connected at the drain of nmos, this circuit is known as current reference. The tempco value is found to be 404.51ppm/0C. Instead of using ideal resistor, rnp1h which is included in 0.18um technology is used. The tempco value of circuit with rnp1h is 4.014K ppm/0C. As temperature variations in resistor is higher, hence tempco values of these circuits are higher than simple current mirror. 

A. Creating CTAT and PTAT:  
According to diode voltage:  
<a href="https://www.codecogs.com/eqnedit.php?latex=I_{0}&space;=&space;I_{s}\cdot&space;e^{\frac{V_{D}}{V_{T}}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?I_{0}&space;=&space;I_{s}\cdot&space;e^{\frac{V_{D}}{V_{T}}}" title="I_{0} = I_{s}\cdot e^{\frac{V_{D}}{V_{T}}}" /></a>

When the temperature increases, voltage will decreaseat Vddue toincrease in Isthus creatingCTAT.In the equation below, Vd contains weak PTAT and strong CTAT.  


To create PTAT, we have to maintain equal voltage at Vd and Vso that differenceV-Vd1 equal to voltage drop across R1 is directly proportionalto temperature. The circuit shown in Figure 1 has been used to implement this.  


The addition of CTAT and PTAT shouldgive a constant reference voltage.Any combination of CTAT and PTAT will not give desirable Vref due to slope difference between CTAT and PTAT.For the CTAT and PTAT to exactly cancel each other, slope of PTAT is increased using a high resistance value i.e. R2.


B. Calculation Of R2
In figure2. R2 value is calculated at zero temperature co-efficient of Vref.  


For calculating VR2, R value has to be found out in the first place. Current(I0)flowing through the branch R1is 1uA.  


Thus, R1 value is calculated to be 36k ohms.  


After substituting the value of Vref from eqn(ii):  


(∂VD3)/∂T=-1.8mV/0C which is the slope value of CTAT curve. (∂VT)/∂T=85uV/0Cwhich is the slope value of PTAT. Substituting these in eqn(iv), we obtain R2=550kohms.  



Putting values of I0as 1uA, R2=550kohms and VD3as 0.7V, we calculate Vref to be 1.25V.


C. Start-Up Circuit

Bandgap reference is a self-biased circuit. So, it requires a start-up circuit. There are two states in which BGR works:- a) Normal operating region and b) Zero current state. Start-up circuit disturbs the zero current state to help it work in normal operating region. Suppose output of opamp is stuck at VDD potential. The two inputs to opamp arestuck at 0 volt. Thus, the source of M6 is at VDD and drain at 0V. Gates of M1 and M2 are also at VDD turning them off. So, 0A current flows through the branch. M7 and M8 are off. Gate of M6 is at 0V thus turning it on. Now, current starts flowing through M6. Gradually, gate potential of M3 and M4 start decreasing from VDD and the potential at V1 starts increasing. When the output of opamp decreases below Vtp, M1 and M2 turn on. So, M7 and M8 are turned on which creates a voltage drop across them so that it switches M6off. Thus, the startup circuit is disconnected when BGR enters normal operating region.

D. OPAMP  

Operational Amplifier used in this circuit is basically a single stage differential amplifier. Its main functionis to drive the bandgap core. It is designed in such a way that its output is insensitive to variation in supply whichhelps to establish asupply independentreference voltage.It can be seen fromfigure3 that Mo3, Mo4 and Mo5, Mo6 are differential pairs.These are the node transistors and we have taken m=4 for matching purpose. Only two transistors could have been used but that would increase the length which would be difficult for matching in layout. The current mirror formed by Mo1 and Mo2 supplies the differential pair with bias current.Another important aspect of OPAMP design is to produce a current which is insensitive to variation of VDD (supply voltage).This is accomplished by driving the amplifier with its own output current. This is done by mirroring Mo7 and Mo8 where Mo7 is the tail transistor. This makes the output current of operational amplifier almost constant with respect to voltage.

Table 1 lists the opamp components and their parameters:




E. Bandgap Core  
Bandgap core consists of 4 pmos transistors (M2, M3, M4, M5), 3 diodes (D1, D2, D3), one mos capacitor M9 and two resistors Rand R2.As voltage drop across resistor R is PTAT in nature, so current through the resistor is also a PTAT. Gates of all the transistors (M2, M3, M4, M5) are shorted making Vgs equal, hence same drain to source current flows through all these transistors. This PTAT current generates PTAT voltage across resistor R2.The value of resistance R2 is adjusted such that slope of PTAT cancels the slope of CTATto give a constant reference voltage.A capacitor M9 also referred as compensating capacitor is included in the negative feedback path of opamp.This is area efficient and its density is 8 times higher than MIM capacitor.Its function is to stabilize the negative feedback otherwise it will oscillate and become unstable.
Table 1 lists the device components and parameters:


III. ANALYSIS OF SIMULATION RESULT  

All the simulations were done using SPECTRE tool. The models of the device were used based on XFAB Technology. 0.18 micron process has been used in the design.

A. Variation of reference voltage with respect to temperature  
In figure 4, reference voltage is approximately 1.173V at room temperature. Reference voltage varies very little from 0º to 85ºC and remains almost constant from 10º to 50ºC. Total variation ofreference voltage is about 0.85mv which is 0.072% of reference voltage. 


B.Variation Of Reference Voltage With Respect To VDD  
As supply voltage VDD changes from 1.8V to 1.9V, the change in reference voltage is about 0.55mVfrom 1.17305V to 1.1736V, which is 0.55%with respect to change in VDD.  


C.Bandgap Reference Settling Time  
Transient simulation analyses in Figure 6 shows the settling time of BGR output. It is found that the circuit acquired 38.929μs to produce stable output when the supply voltage ramping up from 200.0184us to 238.9475us.



D. Bandgap ReferenceDatasheet


IV. LAYOUT

The layout was designed with help of the “Layout XL” based on Cadence Virtuoso. The layout of BGR as shown in figure 7 was completed with zero Design Rule Check (DRC) and Layout Versus Schematic (LVS) errors using Cadence Assura. The post layout simulation results including the parasitic extraction were verified. The layout also consists of common centroid technique for matching purpose and including dummies. The total area of the chip was .The layout consists of Bandgap core consisting of BJTs, resistors and Mosfets, start-up circuit and OPAMP consisting of Mosfets only.  

V.CONCLUSION  

A simple bandgap reference circuit in 0.18 micron CMOS process has been designed. The Bandgap Reference testbench was simulated using SPECTRE. In this circuit, the reference voltageis found to be 1.173V. The operational amplifier used in the circuit is a singlestage differential amplifierhaving gain around 45db. The variation of reference voltage is about 0.072%with respect to supply voltage.  

VI.REFERENCES  
[1] B. Razavi, “Design of Analog CMOS Integrated Circuits” Tata Mcgrow-Hill Edition, 2002, ch. 11.  
[2] Adel S. Sedra, Kenneth C. Smith, “Microelectronic Circuits (4th ed.)” Oxford University Press, 2007, ch. 8, p. 852.  
[3] Md. Shafiullah, “Design of a Simple CMOS Bandgap Reference”, IEEE 2010  
[4] Kang S., Leblebici Y.,“CMOS Digital Integrated Circuits: Analysis and Design”, 2ndEd., 2003  
[5] Tony Chan Carusone, David A. Johns, and Kenneth A. Martin. Analog Integrated Circuit Design.Wiley,2ndedition,2012  
[6] Dan CleinCMOS IC Layout: Concepts, Methodologies and Tools. Newnes, 2000.  
[7] Anant Agarwal and Jeffrey Lang. Foundations of Analogand Digital Electronic Circuits. Elsevier, July2005



