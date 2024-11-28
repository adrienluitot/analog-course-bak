Schematic validation
====================

Transconductance extraction (gm)
--------------------------------

The PDK doesn't provide details on the electron mobility or on the effective channel length.
Thus, we have to run simulations to find the MOSFETs transconductance gm.

On a simple MOSFET Circuit
^^^^^^^^^^^^^^^^^^^^^^^^^^

First, we want to find gm with a simple circuit including a single MOSFET.
Here, we will sweep Vgs and W (the MOSFET channel width) together and find a good combination between W,
Ids (the current consumption) and gm.
|
To retrieve the transconductance gm and be able to plot it, we need to add include scripts 
and equations on the schematic.
These scripts consists of including PDK libraries into the schematic, select the MOSFET gm 
inside the component and save it as a variable for our simulation :

..
    TODO
    Add script directives
    INCLUDE SCRIPT
    .SAVE @n.xmn0.x1.nsg13_lv_nmos[gm] i(VPr1) gm_mos

    EQUATION
    gm_mos = @n.xmn0.x1.ngs13_lv_nmos[gm]

To fetch the parameters (like gm, or ???) of components that come from the IHP PDK, the component SPICE
name needs to be retrieved. First, the schematic netlist needs to be saved with a "right click etc----".
After that, open the netlist file and delete the "exit" directive at the end. Now, the file can be opened
directly with the native ngspice software. In the command prompt, the "?? netlist ??" can be generated with
the following command : 
 
.. code-block:: shell

   listing e > new_netlist.txt

When navigating in the new_netlist.txt file, the name of the component can be found. For our case, the 
MOSFET component SPICE name is ``n.xmn0.x1.nsg13_lv_nmos``.
|
|
As said earlier, the objective is also to choose the right channel width for our application.
We plot the two charts gm=f(Vgs) and Ids=f(Vgs).
At the same time, we sweep the W parameter for five to ten values to have several number of graphs.
By train-error method, we can find the corresponding width for our constraints on the current and
transconductance.
|
When plotting the results, we obtain the following results :

..
    TODO
    Insert schematic screenshot

Here, for a channel width of W = 50 um, we obtain Vgs = 500 mV for the desired transconductance gm of
12.8 mS. If we report this value on the Ids = f(Vgs) chart, we obtain the corresponding current consumption
Ids = 1.29 mA.


With a Cascode Circuit
^^^^^^^^^^^^^^^^^^^^^^

As we have an approximate value for the gate voltage we can complete the circuit with the cascode
MOSFET, the resonator and the charge on the top of it and the input capacitors and inductors.
For now, the objective is to have the wanted gm for our architecture. Therefore, we generate the gate
voltage with an ideal DC source and sweep the voltage. 
For the simulation, an AC power source is added. High value capacitor and inductor are also added to ensure
that the DC source that generates the gate voltage is not shorting the AC source. Note : these high value
components are only needed for the simulation. They aren't part of the circuit.

..
    TODO
    Add schematic screenshot?

After simulation, we apply the same technique as in the single MOSFET circuit to read the charts. To keep
the same gm and Ids, we found a Vgs of 485 mV.

Input matching & output component selection
-------------------------------------------

Input inductor selection (Ls)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
..
    TODO
    Find a way to make Re(Z11) prettier in the following paragraph

Now that we know what gate voltage is needed to obtain our transconductance, we can adjust parameters
to have the correct input matching on our circuit. To do so, we first want to find the input inductor value
that matches our requirements. An S-Parameter simulation and a parameter sweep on the input inductor are
made to acheive 50 Ohms at the input. When plotting the output graphs, we will see several charts which
represents Re(Z11) versus frequency for each inductor value. To make an S-Parameter simulation with Qucs-S
and Ngspice, the software needs to detect at least two AC power sources. Therefore, we put another power
source and isolation components at the output.

..
    TODO
    Add schematic screenshot?

While fine-tuning simulation steps and ranges, we can find the corresponding inductor value : 9.304 nH

Gate polarization circuit
^^^^^^^^^^^^^^^^^^^^^^^^^

The next step will focus on the design and the adjustments of the MOSFET gate polarization circuit. It
consists of another MOSFET with a lesser gate width and resistors to adjust the polarization voltage and 
matching. It will follow the same template as the input inductor selection, i.e. the polarization resistor
tuning for the current consumption and the input matching with the other resistor Rrf.
For our case, we will start with a polarization MOSFET of W = 30 um.
|
To find the right rRPOL for our circuit, we will sweep the resistor value and plot it versus the current 
Ids and gm. For our case, a little tuning of the simulation parameters give us a rPOL value of 8.89kOhms.
|
For the input matching, we change the simulation to S-Parameter and we sweep the Rrf value to find a
resistor value that makes Re(Z11) = 50 Ohms.

..
    TODO
    Screenshot of sim parameters + sim graph ?

While plotting the results, we can see that even with an Rrf value above 500kOhms we can't get Re(Z11) = 50.

..
    TODO
    Several workarounds are possible ; we can add an inductor in series and sweep its value to obtain the wanted
    Re(Z11). We can also adjust the channel width of the polarization MOSFET. Thus, we will have to tune the
    resistor rPOL again to aim the good Ids. For our case, we decided to increase the gate width by 10 um.

    SOLUTION : REDUCE CI TO 570f, PUT RRF = 100K AND QE INCREASES TO 2.04

    After simulating again, we found...
..
    TODO
    Screenshot of smth?


(End of document)


Files
-----
..
    TODO
    Add netlist files? Or .sch files for Qucs directly?