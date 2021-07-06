# OpenTronsSimulation
Simulating OpenTrons equipment to learn the basics of liquid handler programming

## Environment
Using [OpenTrons](https://www.opentrons.com/) App since it is open source and free to use.

I will be using their [Python API](https://docs.opentrons.com/v2/) (specifically version 2) along with a simulated version of the machine OT-2 to verify my protocols, as described in [this guide](https://support.opentrons.com/en/articles/2741869-simulating-ot-2-protocols-on-your-computer).

My Python environment is Python 3.7.3, run in a jupyter notebook. 

For the magnetic plate, OT-2 uses an accessory that brings magnets close or far to the plate without moving it. More info about [Magnetic Module](https://support.opentrons.com/en/articles/1820112-magnetic-module).

To include custom labware in simulation, I followed this guide on [Loading custom labware](https://support.opentrons.com/en/articles/3136506-using-labware-in-your-protocols).

## Project
For an original protocol I will adapt the interview's Case Based Assessment example protocol described as "magnetic bead-based purification of an analyte from a mixture in plates". 

Some of the protocol had to be adapted to the limitations of the OT-2:
- Since it cannot move plates on or off magnetic modules, we will use the automated magnetic module [Magdeck](https://support.opentrons.com/en/articles/1820112-magnetic-module), where the plate is still and the magnets are moved up and down along the protocol.   
- Since it does not have a Vortex module, we will use extensive pipette mixing to resuspend beads.
- Since it does not have agitator modules, we will incubate without agitation or mixing. 

### The setup of the OT-2 machine
| []() | []() | []() |
|:----:|:----:|:----:|
| **10.** 96 Tip Rack 20 µL | **11.** 96 Tip Rack 20 µL         | **12.** Trash               |
|**7.** 96 well plate containing result |**8.** 96 Tip Rack 20 µL | **9.** 96 Tip Rack 20 µL |
|**4.** Magdeck 2 with 96 well plate containing analyte | **5.** 96 Tip Rack 20 µL | **6.** 96 Tip Rack 20 µL |
| **1.** Magdeck 1 with reservoir | **2.** 96 Tip Rack 300 µL | **3.** 96 Tip Rack 20 µL |

Left pipette is a p300 multi

Right pipette is a p20 single



The reservoir on slot 4 be pre-filled as follows:
- Beads in column 1
- Wash in columns 2, 3, 4 and 5
- Buffer in columns 6, 7 and 8
- Acid in column 9
- Trash in column 12

### The adapted protocol

1)	Pre-wash bead tube

    a.	Add wash 

    b.	Mix

    c.	activate magdeck 1

    d.	Wait for pellet

    e.	Remove old wash

    f.	Change tip 

    g.	Repeat x3
    

2)	Spread into wells

    a.	Add buffer to magdeck 1 for the highest needed concentration 

    b.	Mix

    c.	Place in wells at magdeck 2 at different volumes

    d.	Top up buffer so all volumes are the same

    e.	Mix each one on magdeck 2
    

3)	Incubate

    a.	Wait 30min 

    b.	Mix each well

    c.	Wait 30min 

    d.	Activate magdeck 2
    

4)	Redo wash on magdeck 2

    a.	Add wash to each well on magdeck 2

    b.	Mix each well on magdeck 2

    c.	Activate magdeck 2

    d.	Wait for pellet on magdeck 2

    e.	Remove old wash

    f.	Repeat x3


5)	Strip

    a.	Add acid to each well on magdeck 2

    b.	Mix each well

    c.	Activate magdeck 2

    d.	Take supernatant and move to fresh plate


  
