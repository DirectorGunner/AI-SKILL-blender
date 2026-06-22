# Introduction (part 2)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Vertex weight assignment chiefly supports rigging strokes in cut-out animation, where vertex groups encode relative bone influences; see Using Vertex Group for guidance.

Note: a vertex in Grease Pencil is termed a point; the names interchange.

Weight Painting codifies weight data intuitively. The picked Grease Pencil object renders with subtle shading across a spectrum hue range, encoding each point's weight in the active vertex group. Conventionally, blue denotes unweighted and red denotes full weighting.

Weights are installed via painting with weight brushes; initiating paint automatically enrolls weights in the active group (generates one if absent).

**Weight Paint.**

Chosen from the Mode menu in the 3D Viewport header. Once enabled, the Toolbar reformats to Weight Paint Mode sections, and a red circle traces the cursor in the 3D Viewport.

**Weight Options.**

Multiframe — sometimes weight assignment must span multiple frames concurrently. Activate the Multiframe button next to the modes selector (faded lines icon); check Multiframe for guidance.

### Introduction 

Rigid body constraints (also termed joints) couple two rigid bodies.
Physics constraints attach to Empty objects, with fields pointing to the constrained physics-enabled objects.

The Empty hosting the constraint provides a location and axis set distinct from the two objects. Its position marks the constraint location; its axes define the constraint orientation.
These two anchor points establish themselves at animation start and stay fixed in each object's local space throughout the animation.
Objects move freely from the constraint, yet constraint anchors travel with them.
For greater freedom, use multiple objects with non-physics Child of constraints and animate relative positioning.

### Connect 

The quickest constraint approach involves selecting two objects and clicking Connect in Object ‣ Rigid Body.
This generates an empty object (labeled "Constraint") with physics constraint already targeting both objects.

### Physics Menu 

Alternatively, create Rigid Body Constraint on one of the constrained objects using the Physics tab.
This constraint depends on the object's position and orientation—the object itself provides the constraint anchor, eliminating empty-object creation.
Setting the constrained object as Passive type improves constraint control.

The Rigid Body Constraint panel appears in the Physics tab for the selected empty or the one constrained object with the created constraint.

### Common Options 

Reference

Panel :

Physics ‣ Rigid Body Constraint

### Settings 

Enabled
Toggles constraint activity during simulation.

Disable Collisions
Allows constrained objects to interpenetrate.

Breakable
Allows constraint failure during simulation (unavailable for Motor constraints).
Enables destruction simulation.

Threshold
Impulse magnitude required for constraint failure.

### Limits 

Limits constrain objects further by specifying translation/rotation ranges on one axis. Set both limits to 0 to lock an axis.

### Objects 

First
Primary constrained object.

Second
Secondary constrained object.

### Override Iterations 

Makes constraints stronger (higher iterations) or weaker (lower iterations) than the rigid body world specification.

Iterations
Constraint solver iterations per simulation step for this constraint.

### Introduction 

Rigid body simulation models solid object motion, affecting position and orientation without deformation.

Unlike other Blender simulations, rigid body systems integrate closely with the animation framework.
This enables rigid bodies to behave like standard objects within parent-child relationships, animation constraints, and drivers.

### Creating a Rigid Body 

Reference

Mode :

All Modes

Panel :

Properties ‣ Physics ‣ Rigid Body

Menu :

Object ‣ Rigid Body

Only mesh objects participate in rigid body simulation.
Create rigid bodies via the Rigid Body button in Physics properties or through Add Active / Add Passive in Object ‣ Rigid Body.

Two rigid body types exist: active (dynamically simulated) and passive (animation-controlled). Both support the Animated option for animation-system control.

During simulation, the rigid body system overrides position and orientation of dynamic objects.
However, object location and rotation values remain unchanged—the simulation acts like a constraint.
Use Apply Object Transform to make rigid body transformations permanent.

The object's scale influences simulation but stays under animation control.

Remove rigid body physics via the Rigid Body button in Physics properties or Object ‣ Rigid Body.

### Working with Rigid Bodies 

Multiple object operators support rigid body workflows, available in the Rigid Body menu.
These include functions to add/remove rigid bodies, adjust properties, and add Rigid Body Constraints.

### Introduction

There is no universal best approach to video project work that suits all scenarios.
Certain contexts stand out (tutorial creation, wedding films, etc.), but four main stages appear across most workflows.

- Montage: starting with raw material, you arrange shots into a flowing narrative.
Clips need repositioning, layering, cutting, and adjustment.

- Effects: overlays range from basic transitions like fades to full sequences like scrolling credits.

- Color grading: different footage shot with various cameras under varying light creates color inconsistency.
Color correction and grading bring visual harmony across all clips.

- Sound: this involves musical beds, narration, audio design, and external tools like Audacity.

### Introduction

Montage describes the technique of combining separate components (video, audio, text, graphics) into a unified narrative.
The Soviet director Lev Kuleshov pioneered the concept in the 1910s and 1920s.
The famous Kuleshov effect illustrates how viewers extract more information from sequential shot relationships than isolated shots.
(Check the Wikipedia entry for a nice demonstration.)

Naturally, the initial step is bringing material in or making strips.
Many methods exist, each with distinct pros and cons.

Before anything happens to a strip, it must be chosen. Multiple selection approaches are available.

Strips can shift through time (left to right on X) or restack (bottom to top on Y).

Splitting or cutting breaks a strip into before and after sections.
Two approaches are available: Split and Hold Split.

Trimming cuts or extends footage at the head or tail.
This makes the clip shorter or longer.

Grouping packages many strips into a single meta item.

Hint

Good montage takes significant effort.
All key functions (add, split, trim, etc.) have shortcuts.
Learning them pays dividends, despite menu and mouse alternatives existing.
