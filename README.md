# MiniWhip_Antenna

<p align="center">
<img src="./img/AssmbledMiniwhip.jpg" width="400" height="500"/>
</p>

I have built the MiniWhip antenna with intend to use it in my hunt for VLF stations especially the SAQ and DCF-77. Already during first tests I found this antenna to be quite fascinating. Below I will provide you with detailed description how to build robust enclousure for your MiniWhip using off the shelf products, I will also describe how this antenna works - in my opinion :).

In this project I used Mini-Whip module purchased for radiohobby.pl [1]. 


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

$G = 10*\log{(\frac{Uppb^2}{2*Zb} / \frac{Uppa^2}{2*Za})}$

$G= 10*log{(\frac{Uppb}{Uppa})^2}$

Where:
- Uppb: Impedance transformer output peak-to-peak voltage.
- Uppa: Impedance transformer input peak-to-peak voltage.
- Zb: Impedance of coax and receiver connected to transformer output.
- Za: Impedance of antenna plate connected to transformer input.

## Building Outdoor Enclosure

To build the enclosure you will need the following products from Millto.com [2]:

Mufa Kanalizacyjna 110 mm Rury PCV Nasuwka DŁUGA Złączka ŁĄCZNIK Wody Szara
KOREK KANALIZACYJNY 110 MM Zaślepka RURY KANALIZACYJNEJ PCV

It is very important to purchase long verion of mufa, which is 180mm long!

1mm thick alluminium sheet cut according to the drowing below.

UC-1 socket, srews to mount it and SMA pigtail.

To mount the antenna to the mast, standard xxx purchased at Obi:
Fischer Obejma dwuczęściowa SaMontec 89-92 1szt.


Mounting process has been shown on pictures below:

<p align="center">
<img src="./img/LowerCap.jpg" width="400" height="500"/>
<img src="./img/InstalledMiniWhipBase.jpg" width="400" height="500"/>
<img src="./img/InstalledMiniWhip.jpg" width="400" height="500"/>
</p>

## References