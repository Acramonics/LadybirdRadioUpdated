Making a Transistor Radio
=========================

Acramonics 2026
---------------

The Ladybird book *Making a Transistor Radio* by G.C. Dobbs with
wonderful illustrations by B.H. Robinson was first published in 1972
and reissued as a facsimile in 2008. The book goes through the
construction of the radio in stages, starting with a crystal set,
adding a single transistor amplifier, followed by a second transistor
amplifier. Finally, the radio frequency stage is improved through
'regeneration' using a third transistor to improve sensitivity.

Back around 1974, aged 10, I made this radio and it worked well for
me. It seems that others didn't have as much luck, particularly with
the final stage which was susceptible to oscillation - I suspect this
was a result of variation between samples of the transistors.  The
transistors used were PNP germanium types and are now very difficult
to obtain as they are no longer produced.  When you can find them,
they are very expensive as they are popular for guitar effects pedals.

As a result of these problems, @AndyDoz on YouTube has modified the
design to use easily-obtained silicon NPN transistors requiring the
power rails to be swapped over. Other small changes have been
introduced to reduce the chance of oscillation, adding a separate coil
for the regeneration stage and introducing emitter resistors as well
as modifying the transistor biasing to suit the silicon transistors. 

He has tried to replicate the original design as much as possible
including the use of a wooden board and brass screws with screwcups to
connect the components. Doz is providing a series of videos on YouTube
documenting the project.

- https://www.youtube.com/watch?v=Zk2TwEWvFMoz

My project takes Doz's design and ports it to a PCB. The first stage
will be a PCB for the full radio with regeneration. I will then modify
the PCB to allow each stage (crystal set, one-transistor and
two-transistor amplifiers) to be built on the same PCB.

**Note!** I would not normally design a PCB like this! The idea is to
make this as close to the layout of the circuit diagram and the wooden
board version as possible with each section clearly delineated.


Parts
-----

Doz has, of course fixed the problem of obtaining the transistors, but
the variable capacitor, radio frequency choke and transformer can be
problematic.

### Germanium diode

These are quite difficult to obtain - any germanium diode will do and
you should be able to find them on EBay. Amazon also sells 1N34A
germanium diodes as do Cricklewood and BitsBox.

You can still build the full regeneration stage radio without the diode.

### Earpiece

You need a high impedance earpiece, typically a so-called 'crystal
earphone'.  These are somewhat harder to find than they once were, but
are available from EBay, Rapid Electronics, CPC and Amazon.

### Sockets

There are **Molex 254** 'pin headers' indicated at various places on
the board; you then connect wires using a special housing. You do not
have to use these, you can simply push wires through the holes
instead. However, I recommend sockets for the two earpiece headers and
the loudspeaker as you will be adding and removing these (particularly
if you want to be able to go back to an earlier stage of the radio).

### Jumpers

These are all 2-row parts with 0.1" spacing. They are then fitted with
the little plastic headers that are used in computers. If you can't
find them, you can solder a wire across instead, but it does make
things more difficult as you will have to remove jumpers as well. If
simply progressing through the stages (and don't want to go back
again) you could just cut the wire jumpers off.

On the board, the jumpers (J1-J5) are marked at each position with the
characters X,1,2,G standing for crystal, 1-transistor, 2-transistor
and reGeneration respectively:

Jumper | Marking | Meaning
:----- | :------ | :----------------------------------------------------
J1:    | G       | Connect for regeneration
       | G       | Connect for regeneration
       | X12     | Connect for crystal, 1-transistor, and 2-transistor (not
       |         | regeneration)
       |         |    
J2:    | 12      | Connect for 1-transistor and 2-transistor (not crystal or
       |         | regeneration)
       | X       | Connect for crystal
       |         |    
J3:    | 12G     | Connect for 1-transistor, 2-transistor, and regeneration
       |         | (i.e. everything except the crystal set)
       |         |    
J4:    | G       | Connect for regeneration stage only
       | G       | Connect for regeneration stage only
       | G       | Connect for regeneration stage only
       |         |    
J5:    | 2G      | Connect for 2-transistor and regeneration (not for crystal
       |         | or 1-transistor
       | 2G      | Connect for 2-transistor and regeneration (not for crystal
       |         | or 1-transistor
       | 2G      | Connect for 2-transistor and regeneration (not for crystal
       |         | or 1-transistor

### Variable capacitor

The style of variable capacitor used in the book is almost
unobtainable.  The best replacement seems to be an AM+FM radio quad
PVC film variable capacitor containing dual 270pF and dual 20pF
variable capacitors. Wiring the two 270pF capacitors in parallel will
then give 540pF which is close enough to the specified 500pF. These
are available from various suppliers on AliExpress as the **CBM-443BF**
(and at varying prices - from about &pound;1.70 to &pound;16.50!).
There are variations available with different length shafts,
screw-trimmers, etc. Just look for the dual 270pF.

### Radio frequency choke

The RFC used in the book isn't made any more, but was a ferrite core
2.5mH device. The board leaves enough space for one of these if you
can find it, but it isn't a critical component, so a standard
resistor-like 2.2mH (2200uH) inductor should be fine.

### LT700 transformer

These are apparently still made and available from Cricklewood
Electronics, but I ordered one on EBay and instead was sent an Eagle
P631T. The P631T is easy to obtain from EBay and Amazon, 
YourSpares.co.uk, and audiomate.co.uk

The LT700 has a 1.2K primary with a centre tap (which is not used in
the Ladybird Radio) and a 3.2R secondary.  The P631T also has a 1.2K
primary (but with no centre tap) but has a 6.4R secondary with a
centre tap. Consequently, using one end and the centre tap will give
us the 3.2R we need.

The Xicon 42TL003-RC (available from Mouser) would probably work, but
has an 8R secondary (with centre tap) allowing a 4R secondary.

The Hammond 146J (available from Mouser) would probably also work, but
has a primary impedance of 1K instead of 1.2K.

The Tamura MET-23 (available from Mouser) has a 1.6K primary (with
centre tap) and a 3.2R secondary and would almost certainly be fine.

The board is configured for the P631T (since that is what I obtained),
but has a solder pad jumper to allow transformers which have 3.2R
secondaries without a centre-tap to be used. So if you are using an
LT700, 147J or MET-23, just bridge this jumper with some solder.

In all cases, the centre tap (of present) would be cut off the primary.

Model            | Primary   | Secondary 
:----------------|:----------|:-------------
Eagle LT700      | 1.2k CT   |  3.2R     
Eagle P631T      | 1.2k      |  6.4R CT  
Xicon 42TL003-RC | 1.2k CT   |  8R CT    
Hammond 146J     | 1.0k CT   |  3.2R     
Tamura MET-23    | 1.6k CT   |  3.2R     

(CT = centre tapped)


Construction
------------

### The ferrite rod coil

### The crystal set

- Populate the parts for the crystal set which are all in the `DETECTOR'
area of the board.

- Add the `X' jumpers for J1 and J2

- Connect an earpiece to the header in the `DETECTOR` part of the
  board. (You can just solder wires in, but you will have to remove
  them for later stages.)

- You will need a long aerial (about 100ft long) and a good earth
  connection (e.g. to a central heating or water pipe).

### The 1-transistor stage

- Add the components in the `1st TRANSISTOR` area of the board.

- Remove the jumpers that are just labelled `X'

- Add the `1' jumpers at J1, J2 and J3.

- Connect an earpiece to the header in the `1st TRANSISTOR` part of
  the board. (You can just solder wires in, but you will have to
  remove them for later stages.)

- Connect the battery and switch at the far right of the board

### The 2-transistor stage

- Add the components in the `2nd TRANSISTOR` area of the board.

- Remove any jumpers that are *not* labelled `2'

- Add the `2' jumpers at J1, J2, J3 and J5

- Connect a 4 Ohm loudspeaker in the `2nd TRANSISTOR` part of the
  board.

### Regeneration

- Add the components in the `REGENERATION` area of the board.

- Remove any jumpers that are *not* labelled `G'

- Add the `G' jumpers at J1, J3, J4 and J5

- You shouldn't need the aerial or earth connection any more!





