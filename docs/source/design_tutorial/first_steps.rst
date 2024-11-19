First steps
===========

Context
-------

To keep a simplified approach, we will design a single ended cascode low noise amplifier.
This will allow us to describe each step of the design flow and use most features of the softwares.

LNA SINGLE PICTURE TO ADD

Characterization using PDK examples
-----------------------------------


IHP 0.12u tech : 

Lmin = 0.12um
Cox = epsilon/tox = 14.35 fF.um-2
tox = 2.45 nm & epsilonr = 3.97
Cjunc = 0.95 fF.um-2


We choose the following parameters for the design : 

Gv = 20 (26 dB)
IIP3 = -10 dBm
f0 = 2.45 GHz
Cl = 1 pF ; Qe = 2
Vdd = 3.3 V et Id = 1.5 mA

Ll = 4.22 nH
gmM1 = 12.8 mS
Rl = 781.25 Ohms
Ctot = 650 fF
Ls = 2.5 nH ; Vod = Vdsat = 234 mV pour Id = 1.5 mA

W/L = gm/2Kn(Vgs-Vt) = 

Process variables extraction
----------------------------