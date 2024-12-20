# MiniWhip_Antenna

<p align="center">
<img src="./img/AssmbledMiniwhip.jpg" width="400" height="500"/>
</p>

I have built the MiniWhip antenna with intend to use it in my hunt for VLF stations especially the SAQ and DCF-77. Already during first tests I found this antenna to be quite fascinating. Below I will provide you with detailed description how to build robust enclousure for your MiniWhip using off the shelf products, I will also describe how this antenna works - in my opinion :).

In this project I used Mini-Whip module purchased for radiohobby.pl [1]. 

Big credit to Roelof Bakker, PA0RDT [3], the original designer of Miniwhip Antenna and Pieter-Tjerk de Boer, PA3FWM [4], who put a comprehensive description of this antenna type.


## Theory of Operation

Miniwhip antenna's come in different flavours. The one from radiohobby.pl [1] is based on the following schematics:

<p align="center">
<img src="./img/schemat_mini_whip_s.jpg" width="500" height="400"/>
</p>

The right hand side of the schematics shows bias-T circuit allowing to provide DC power over coax, which is connected to the antenna.
On the left hand side you can see antenna plate (small pcb plate), connected to two stage impedance transformer including JFET transistor Q1 and npn transistor Q2 and bias-T circuit separating DC power from HF signal provided to the receiver over coax. 

The first stage of the impedance matching circuit is based on JFET due to its very high input impedance, which makes this type of transistor ideal for working with high impedance signal sources.

Q1 works in drain follower configuration and Q2 in the emitter follower setup. This means that there is no voltage gain (amplification) introduced by those elements. In fact measurement conducted using functional generator connected to the gate of Q1 and oscilloscope attached to both gate of Q1 and emitter of Q2 shows about 0.6 voltage attenuation!

<p align="center">
<img src="./img/MeasurementSetup.jpg" width="500" height="400"/>
<img src="./meas/77kHz_InBlue-30dBm_OutRxC4Yellow.png" width="500" height="400"/>
</p>

Blue trace on the above picture shows voltage signal level in the point A at the schematics, while voltage signal at point B is drawn in yellow.

The key to understand the how Mini-Whip works is to realize that very high input impedance of the antenna plate (especially for LF and VLF) is transformed by transistor stages Q1 and Q2 to coax level impedance of 50 ohm, which leads to the power gain, which can be calculated as follows:

$Urms = Uamp / \sqrt{2} = Upp / (2*\sqrt{2})$

$P = Urms^2 / Z = Upp^2 / (8*Z)$

consequently, we can express power levels at points A and B as:

$Pa = Uppa^2 / (8*Za)$

and 

$Pb = Uppb^2 / (8*Zb)$

Power gain expressed in decibels can be calculated as:

$G = 10*\log{Pb/Pa}$

$G= 10*log{((\frac{Uppb}{Uppa})^2 * \frac{Za}{Zb})}$

Where:
- G: Power amplification of impedance transformer stage.
- Uppb: Impedance transformer output peak-to-peak voltage.
- Uppa: Impedance transformer input peak-to-peak voltage.
- Zb: Impedance of coax and receiver connected to transformer output.
- Za: Impedance of antenna plate connected to transformer input.

In case of our particular implementation we can calculate:

$Za = 1 / (2* Pi * f * Cant)$

where:
    f = 77.5kHz (DCF-77 transmitter frequency - any HF frequency can be used here)
    Cant = 1pF

this gives:

$Za = 1 / (6.28 * 77.5 * 10^3 * 1 * 10 ^-12) = 2,0545 * 10^6 = 2.1Mohm$

$Zb = 50ohm$

From voltage measurements presented earlier we can also calculate:

$Uppb / Uppa = 26.4mV / 42.8mV = 0.61$

Now, we have all data to calculate power amplification $G$ using formula derivied earlier:

$G = \log{(0.61^2 * (2.1 * 10^6 / 50))} = 10 * /log{(0.3721 * 0.042 * 10^6)} = 10 /log{1536} = 32dB$

## Building Outdoor Enclosure

To build the enclosure you will need the following products e.g. from polish manufacturer Millto.com [2]:

110 mm PVC Sewer Coupling Sleeve, Long Slip-On Connector for Water, Gray
(Mufa Kanalizacyjna 110 mm Rury PCV Nasuwka DŁUGA Złączka ŁĄCZNIK Wody Szara)
KOREK KANALIZACYJNY 110 MM Zaślepka RURY KANALIZACYJNEJ PCV
(110 mm PVC Sewer End Cap, Pipe Plug)

It is very important to purchase long verion of mufa, which is 180mm long!

1mm thick alluminium sheet cut according to the drowing below.

UC-1 socket, srews to mount it and SMA pigtail.

To mount the antenna to the mast, standard xxx purchased at Castorama:
Obejma Fischer FRS PLUS 48-54 x 20 mm
Fischer Obejma do rur SaMontec 125 
Screw M8, which needs to be cut to 3cm length.


Mounting process has been shown on pictures below:

<p align="center">
<img src="./img/LowerCap.jpg" width="400" height="500"/>
<img src="./img/InstalledMiniWhipBase.jpg" width="400" height="500"/>
<img src="./img/InstalledMiniWhip.jpg" width="400" height="500"/>
<img src="./img/AssmbledMiniwhip.jpg" width="400" height="500"/>
</p>

# Conclusions

In my case antenna has been mounted about 2m above the roof top of my house. There are other antennas in the proximity (about 1-1.5m away). Mast has not been grounded. Used coax is RG-58. No ferrites beads or common noise filters are used.

Despite those not ideal conditions antenna performs very well especially on LV and VLV bands. Grounding in my case is not essecial - when ground is connected next to receiver then noise floor drops by about -5dBm, which is an improvment, but not a deal breaker.

I founded grounding to be more crucial when atenna was installed at my balcony (i.e. lower to the ground).

Using mini-whip, I am now able to consistently receive DCF-77 signal - something I could not do using my endfed or random wire antennas.

I am also able to listed to LFV communications from various military stations such as Rassias RDL at 18.1kHz.

## References

[1] MiniWhip antenna module - https://radiohobby.pl/projekty/antena-mini-whip/

[2] Long Sewer Coupling Sleeve with caps - https://millto.com/pl/

[3] De pa0rdt-Mini-Whip, een actieve ontvangantenne voor 10 kHz tot 20 MHz, Roelof Bakker, PA0RDT, Electron 5/2006

[4] Fundamentals of the MiniWhip antenna, Pieter-Tjerk de Boer, PA3FWM - https://www.pa3fwm.nl/technotes/tn07.html

