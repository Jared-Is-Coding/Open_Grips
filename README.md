Open Grips – Isolated Frictionless Ergonomic Grip Training for FDP and FDS

## Original Project

The original project uses FreeCad for parametric modeling, and 3D printing for manufacturing. See PDF for full description

## This Fork

The key things I was aiming to improve in this fork were:

### Standard file format

The FreeCAD file format exports were not easy to move between programs for modification. My hope is that by providing a .step file users in the future will be able to open and modify the file to their liking in whatever CAD software they use.

### Ease of printing

The original models were not set up for efficient FDM printing. Through the addition of new angled walls and the adjustment of other areas, the prints are now all sufficiently set up for FDM printing with no supports needed.

- The Sisyphus model has been completely redesigned to take on the style of the Prometheus model in terms of assembly and style, allowing simpler printing *and* assembly
- The pins may now be printed
- The pins may be printed horizontally for strength and reduced failures
- The long, structural pin may also be printed horizontally for strength and reduced failures
- The frame pieces may now be printed sideways, without supports
- The chamfers and fillets on both tools have been generally improved for FDM printing

### Additional guard top piece

I've added a top piece to be printed in TPU as a guard for the tools.

### Documentation

You're reading it! There's more work to be done, but the process of modifying the print files still needs some work.

### Simple file modification for each user

One of the core ideas advertised by a company out there is that each user's hand is a little different and requires minute adjustments to get things just right for each person. In practice, we've found this to be not majorly important (exact measurements and adjustments from person to person do not heavily impact the effectiveness of the training), but for major differences in hand/finger sizes it is definitely still relevant.

In the original models, this modification was done using parametric model variables. I wasn't very familiar with FreeCAD, so in moving over to Fusion360 I dropped the compatibility with these variables. I plan to work on reimplementing them as I'm able. (Unless someone else wants to? :) For now, modification will need to be done by hand.

Until I finish some new tooling for adjusting these files, I'll explain the gist of what we've thought through here:

#### Prometheus

##### Roller Up/Down Offset

The length of the full finger may be used for up/down placement offsets of the rollers. Using the pinky length as "0", you can then calculate the height of the offset of each roller by subtracting the height of the pinky from height of the finger.

So, if your pinky was 60mm:

(Vertical offset of 79mm Ring finger roller pin) = 79mm - 60mm = ~19mm

##### Roller Forward/Backward Offset

The length of the PIP joint to the DIP joint ("P->D") may be used for forward/backward offsets of the rollers. Using the pinky length as "0", you can then calculate the offset of each roller by subtracting the length of the pinky P->D from the finger P->D.

So, if your pinky P->D was 18.5mm:

(Horizontal offset of a 27mm Ring finger roller pin) = 27mm - 18.5mm = ~8.5mm

##### Roof Height

The length of the DIP joint to the tip of your finger may be used to calculate the height of the roof of each finger roller to achieve an "ideal" angle to maintain.

(Roof Height) = (DIP to Fingertip) / tan(Desired Angle)

Based on our findings, the desired angles are roughly:

Index: 57°
Middle: 60°
Ring: 60°
Pinky: 55°

So, if your Index finger DIP to Fingertip was 28mm:
(Roof Height) = 28 / tan(57) = ~18.18mm

#### Sisyphus

##### Roller Offset

See each "Roller Offset" area above. Apply the same concepts.

##### Roller Diameter

TBD