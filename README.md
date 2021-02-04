# A Low Power, Compact Size, Supply Independent Bandgap Reference

## Abstract
In analog circuits we need a constant voltage which is independent of supply voltage as well as temperature. In this paper, we present a BGR (Bandgap Reference) for solving the above purpose. This bandgap reference circuit can be made using current mirrors and Op-amp. This circuit is implemented in 0.18um technology. We achieved a constant voltage of 1.2V and tempco of approximately 12ppm/0C. Temperature variations, we used from 0-850C. We here present the schematic and layout with pre and post layout simulations.

## Introduction
Voltage references have a major impact on the performance and accuracy of analog systems. They shouldn’t vary much with supply voltage and temperature. There are various ways of getting a constant voltage in power supplies or when the input voltage is higher than the output. Some of the methods of obtaining the constant voltage include a). using a Zener diode that breaks down at a known voltage when reverse biased, b) Using the threshold voltage of MOS, c)Cancelling the negative temperature dependence of pn junction (complementary to absolute temperature, CTAT) with positive temperature dependence (Proportional to absolute temperature PTAT). CTAT and PTAT provide more stable and efficient constant voltages. Thus, we have used this concept in our project.    
The bandgap reference circuit is obtained by the addition of CTAT and PTAT in the bandgap core. These are further implemented using pnp BJTs which act as diode, rnp1h (resistances in 0.18um CMOS process) and Mosfets. A startup circuit is also designed for the self-biased BGR. The OPAMP circuit is also implemented in this Bandgap reference. The whole circuit was then simulated using SPECTRE to obtain the desired waveforms. The layout was done and the post-layout simulation was carried out to tabulate the data obtained thereafter.

## Circuit Description
To generate current reference and voltage reference, different circuits were implemented and their tempco values were calculated to provide us a clear picture of current and voltage variations with respect to temperature. In simple current mirror, ideal current source is used. Tempco value of simple current mirror circuit is found to be 5.14ppm/0C. To implement this circuit practically, a resistance(100K) is connected at the drain of nmos, this circuit is known as current reference. The tempco value is found to be 404.51ppm/0C. Instead of using ideal resistor, rnp1h which is included in 0.18um technology is used. The tempco value of circuit with rnp1h is 4.014K ppm/0C. As temperature variations in resistor is higher, hence tempco values of these circuits are higher than simple current mirror. 

A. Creating CTAT and PTAT: 

