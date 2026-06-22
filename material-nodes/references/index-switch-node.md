# Index Switch Node, Levels Node, Clamp Node, Float Curve ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Index Switch Node; Levels Node; Clamp Node; Float Curve; Map Range Node; Math Node.

## Index Switch Node

The Index Switch node outputs one of its inputs by an integer Index, evaluating only the selected input — efficient for switching between several data inputs. (The Menu Switch node is similar but exposes the choice as a menu rather than an index.) Inputs: Index (which input socket passes through, zero-based so the first input is index 0) plus one socket per possible input, with more added by dragging a connection onto the bottom empty socket or clicking the header icon — and a tip notes that when Index connects to a Menu Switch set to Integer Type, the matching menu labels show next to the index for readability. Properties: Type (the data type the node handles). Output: Output (the value from the input at the current Index, unmodified, or, if Index is out of range, the first input or a zero-equivalent value by type).

### Index Switch Node

Pass through one input based on an integer Index.
Only the selected input evaluates, enabling efficient switching.

**See also:** Menu Switch offers a user-friendly menu instead of index.

### Inputs

**Index**
Selects which input to pass (zero-based; first = 0).

Each socket is a possible selection.
Active input: determined by Index.

Add sockets by:
- Dragging to the empty bottom socket.
- Clicking the header icon.

**Tip:** Connect Index to Menu Switch set to Integer Type—menu labels appear next to the index, clarifying meanings and improving readability.

### Properties

**Type**
Data type handled.

### Outputs

**Output**
Value from the selected input, unmodified.
Index out of range: defaults to first input or zero-equivalent.

## Levels Node

The Levels node reads the input color channels and outputs analytical values — the output is one-dimensional, so it visualizes as a uniform gray. Inputs: Image (standard color input) and Channel, which values feed the analytics — Combined (red, green, and blue), Red, Green, Blue, or Luminance. Outputs: Mean (the average of all pixels in the chosen channel, representing overall brightness, usable for setups depending on how bright or dark the input is) and Standard Deviation (how much pixel values stray from the mean — low means values cluster near it, high means they spread over a wide range).

## Clamp Node

The Clamp node constrains a value between a minimum and a maximum. Inputs: Value (the input to clamp), Min (the minimum), and Max (the maximum). Properties: Clamp Type — Min Max (constrain between Min and Max, and when Min exceeds Max, always output Max regardless of input) or Range (constrain between Min and Max, but when Min exceeds Max, constrain between Max and Min instead). Output: Result (the clamped value). Example: the Voronoi Texture node outputs a value with a minimum of zero, and the Clamp node can raise that minimum to 0.2.

### Clamp Node

Constrain a value between min and max.

### Inputs

**Value**
Input to clamp.

**Min**
Lower bound.

**Max**
Upper bound.

### Properties

**Clamp Type**

- **Min Max:** Constrain between Min and Max. Min > Max: always outputs Max.
- **Range:** Constrain between Min and Max. Min > Max: swap and constrain.

### Outputs

**Result**
Clamped output.

### Examples

Voronoi Texture outputs minimum zero.
Clamp to minimum 0.2.

Clamp example.

### Clamp Node

The Clamp node pins a value inside a floor and a ceiling.

### Inputs

Value
The figure you want clamped.

Min
The minimum value.

Max
The maximum value.

### Properties

Clamp Type
Method to clamp.

Min Max :

Pin values inside Min and Max. Should Min run past Max, Result simply yields Max regardless of what comes in.

Range :

Pin values inside Min and Max. Should Min run past Max, pin inside Max and Min the other way round.

### Outputs

Result
The figure once it has been clamped.

### Examples

The Voronoi Texture node emits a value bottoming out at zero. Clamp can lift that floor so the minimum reads 0.2 instead.

Example of Clamp node.

## Float Curve

The Float Curve node maps an input float through a curve and outputs a float. Inputs: Factor (how much the node influences the output) and Value (standard float input). Properties: Curve (see the Curve widget). Output: Float (standard float output).

### Float Curve

Map a float to a curve; output a float.

### Inputs

**Factor**
Output influence degree.

**Value**
Float input.

### Properties

**Curve**
See Curve widget for controls.

### Outputs

**Float**
Float output.

### Float Curve

The Float Curve node runs an input float through a curve and returns a float value.

### Inputs

Factor
Dials how much sway the node holds over what it outputs.

Value
Standard float input.

### Properties

Curve
For the curve controls see: Curve widget.

### Outputs

Float
Standard float output.

## Map Range Node

The Map Range node remaps a value from one range to a target range. Inputs: Value/Vector (the input to remap); From Min and From Max (the source range's bounds); To Min and To Max (the target range's bounds); and Steps (the number of allowed values between To Min and To Max in Stepped Linear interpolation — higher being smoother, lower progressively quantizing the input). Properties: Data Type (Float or Vector, updating the sockets to match) and Interpolation Type — Linear, Stepped Linear, Smooth Step (smooth Hermite edge interpolation), or Smoother Step (smoother Hermite edge interpolation) — plus Clamp (clamp the output to the target range). Output: Result/Vector (the remapped value). Example: the Noise Texture node outputs [0, 1], and Map Range can remap it to [-1, 1].

### Map Range Node

Remap a value from one range to another.

### Inputs

**Value/Vector**
Input to remap.

**From Min**
Source range lower.

**From Max**
Source range upper.

**To Min**
Target range lower.

**To Max**
Target range upper.

**Steps**
Quantization steps for Stepped Linear.
Higher: smoother; lower: more quantization.

### Properties

**Data Type**
Float or Vector (updates sockets).

**Interpolation Type**

- **Linear:** Linear transition.
- **Stepped Linear:** Stepped transition via Steps.
- **Smooth Step:** Hermite edge smoothing.
- **Smoother Step:** Enhanced Hermite smoothing.

**Clamp**
Cap output to target range.

### Outputs

**Result/Vector**
Remapped output.

### Examples

Noise Texture yields [0, 1].
Map Range remaps to [-1, 1].

Map Range example.

### Map Range Node

Feed the Map Range node a value and it rescales that value from its source span onto a target span.

### Inputs

Value/Vector
Whatever value or vector you are feeding in for remapping.

From Min
Bottom end of the source span.

From Max
Top end of the source span.

To Min
Bottom end of the destination span.

To Max
Top end of the destination span.

Steps
How many values are allowed between To Min and To Max under Stepped Linear interpolation. Raise it for smoother interpolation; lower it and the input quantizes more and more.

### Properties

Data Type
Map Range handles both Float and Vector data types. Switching the data type updates the sockets to suit the choice.

Interpolation Type
The mathematical method used to bridge gaps between the numeric inputs.

Linear :

Linear interpolation between From Min and From Max values.

Stepped Linear :

Stepped linear interpolation between From Min and From Max values.

Smooth Step :

Smooth Hermite edge interpolation between From Min and From Max values.

Smoother Step :

Smoother Hermite edge interpolation between From Min and From Max values.

Clamp
Switch it on and the result gets held inside the destination span.

### Outputs

Result/Vector
What the input becomes once remapped.

### Examples

The Noise Texture node emits a value across [0, 1]. Map Range can shift that onto the range [-1, 1].

Example of Map Range node.

## Math Node

The Math node performs math operations. Inputs (dynamic — some appear only for certain operations, e.g. Addend only for Multiply Add): Value (trigonometric functions read it as radians), Addend, Base, Exponent, Epsilon, Distance, Min, Max, Increment, Scale, Degrees, and Radians. Properties: Operation, grouped as — Functions: Add (the sum), Subtract (the difference), Multiply (the product), Divide (the first over the second, division by zero giving zero), Multiply Add (the product of the two values plus Addend), Power (Base to the Exponent), Logarithm (the log of the value to a given Base), Square Root, Inverse Square Root (one over the square root), Absolute (the value without its sign, making negatives positive), and Exponent (Euler's number to the value's power). Comparison: Minimum, Maximum, Less Than (1.0 if the first value is smaller, else 0.0), Greater Than (1.0 if the first is larger, else 0.0), Sign (1.0 for positives, -1.0 for negatives, 0.0 for zero), Compare (1.0 if the two values' difference is at most Epsilon), Smooth Minimum, and Smooth Maximum. Rounding: Round (to the nearest integer, up at 0.5), Floor (down), Ceil (up), Truncate (the integer part), Fraction (the fractional part), Truncated Modulo (the remainder of the first divided by the second), Floored Modulo (the positive remainder), Wrap (a value between Min and Max from the absolute difference between the input and the nearest integer multiple of Max below it), Snap (down to the nearest integer multiple of Increment), and Ping-pong (bouncing between 0.0 and Scale as the input rises). Trigonometric: Sine, Cosine, Tangent, Arcsine, Arccosine, Arctangent, Arctan2 (the inverse tangent of the first value over the second, in radians), Hyperbolic Sine, Hyperbolic Cosine, and Hyperbolic Tangent. Conversion: To Radians and To Degrees. Plus Clamp (limit the output to 0.0-1.0; see Clamp). Output: Value (the numerical result). Examples — Manual Z-Mask: a cube ~10 units from the camera (top Render Layers) and a plane covering the left half ~7 units away (bottom Render Layers) both pass through Map Value nodes multiplying depth by 0.05 and clamping to [0.0, 1.0] for display as color; the Minimum node picks the smaller depth per pixel (the plane on the left since it's closer, the cube on the right), while the Maximum node picks the larger (the cube on the left, the infinitely-far background on the right). Using sine to pulsate: a Time node outputs a linear 0-to-1 over 101 frames, so at frame 25 the value is 0.25, which times 2×pi (6.28) becomes 1.0 via Sine since sin(2×pi/4) = sin(pi/2) = +1.0; since sine outputs -1.0 to 1.0, a Map Value node rescales to 0.0-1.0 (add 1, then multiply by 0.5) and the default Color Ramp shows it as grayscale (medium gray for 0.0, black for -1.0, white for 1.0) — animate it for a smooth cyclic gray sequence, usable to fade an alpha channel, push a scene in/out of focus via Z, or pulse a color channel.

Brightening (scaling) a channel: a Math (Multiply) node raises the luminance channel (Y) to brighten the image — use a Map Value node with min() and max() turned on to keep the output within valid values, and with this approach a logarithmic function can make a high-dynamic-range image; for this particular case, a Brightness/Contrast node may give simpler brightness control.

The Math Node carries out math operations.

Inputs — the node's inputs are dynamic, with some appearing only for certain operations; the Addend input, for instance, shows only for Multiply Add.
Value — an input value; trigonometric functions read it as radians.
Addend — an input addend.
Base — an input base.
Exponent — an input exponent.
Epsilon — an input epsilon.
Distance — an input distance.
Min — an input minimum.
Max — an input maximum.
Increment — an input increment.
Scale — an input scale.
Degrees — input degrees.
Radians — input radians.

Properties:
Operation — the math operator applied to the inputs.
  Functions: Add (the two values' sum), Subtract (their difference), Multiply (their product), Divide (the first over the second; dividing by zero gives zero), Multiply Add (the product of the two plus Addend), Power (Base raised to Exponent), Logarithm (the log of the value to the given Base), Square Root (the value's square root), Inverse Square Root (one over the square root), Absolute (the value with its sign dropped, turning negatives positive), Exponent (Euler's number raised to the value).
  Comparison: Minimum (the smaller input), Maximum (the larger input), Less Than (1.0 when the first is below the second, else 0.0), Greater Than (1.0 when the first exceeds the second, else 0.0), Sign (positives give 1.0, negatives -1.0, and 0.0 gives 0.0), Compare (1.0 when the two values differ by at most Epsilon), Smooth Minimum, Smooth Maximum.
  Rounding: Round (rounds entrywise to the nearest integer, up at a 0.5 fraction), Floor (rounds down to the nearest integer), Ceil (rounds up to the nearest integer), Truncate (the value's integer part), Fraction (the value's fractional part), Truncated Modulo (the remainder of the first over the second), Floored Modulo (a division's positive remainder), Wrap (a value between Min and Max from the absolute gap between the value and the nearest integer multiple of Max below it), Snap (rounds down to the nearest integer multiple of Increment), Ping-pong (bounces between 0.0 and Scale as the value rises).
  Trigonometric: Sine, Cosine, Tangent, Arcsine, Arccosine, Arctangent (each of the input value), Arctan2 (the inverse tangent of the first over the second, in radians), Hyperbolic Sine, Hyperbolic Cosine, Hyperbolic Tangent (each of the input value).
  Conversion: To Radians (degrees to radians), To Degrees (radians to degrees).
Clamp — limits the output to 0.0–1.0; see Clamp.

Outputs:
Value — the numerical result.

### Math Node

Numerical operations.

### Inputs

Dynamic; some only appear for certain operations.
Example: Addend for Multiply Add.

**Value**
Input (radians for trig).

**Addend**
Input for Multiply Add.

**Base**
Input for Power/Logarithm.

**Exponent**
Input for Power.

**Epsilon**
Threshold for Compare.

**Distance**
Input for distance ops.

**Min**
Lower bound.

**Max**
Upper bound.

**Increment**
Input for Snap.

**Scale**
Input for Ping-pong.

**Degrees**
Input for conversion.

**Radians**
Input for conversion.

### Properties

**Operation**

**Functions**

- **Add:** Sum.
- **Subtract:** Difference.
- **Multiply:** Product.
- **Divide:** First ÷ second (zero yields zero).
- **Multiply Add:** (First × second) + Addend.
- **Power:** Base ^ Exponent.
- **Logarithm:** log_Base(Value).
- **Square Root:** √Value.
- **Inverse Square Root:** 1 / √Value.
- **Absolute:** Magnitude.
- **Exponent:** e ^ Value.

**Comparison**

- **Minimum:** Smallest input.
- **Maximum:** Largest inputs.
- **Less Than:** 1.0 if first < second; 0.0 otherwise.
- **Greater Than:** 1.0 if first > second; 0.0 otherwise.
- **Sign:** Extract sign (+1.0 positive, -1.0 negative, 0.0 zero).
- **Compare:** 1.0 if difference <= Epsilon; 0.0 otherwise.
- **Smooth Minimum:** Smooth minimum transition.
- **Smooth Maximum:** Smooth maximum transition.

**Rounding**

- **Round:** Nearest integer (round 0.5 up).
- **Floor:** Round toward negative infinity.
- **Ceil:** Round toward positive infinity.
- **Truncate:** Integer part only.
- **Fraction:** Fractional part only.
- **Truncated Modulo:** First % second (truncated).
- **Floored Modulo:** Positive remainder.
- **Wrap:** Value between Min and Max via offset.
- **Snap:** Round down to nearest Increment multiple.
- **Ping-pong:** Bounce [0, Scale] as input increases.

**Trigonometric**

- **Sine:** sin(Value).
- **Cosine:** cos(Value).
- **Tangent:** tan(Value).
- **Arcsine:** arcsin(Value).
- **Arccosine:** arccos(Value).
- **Arctangent:** arctan(Value).
- **Arctan2:** arctan(first / second) in radians.
- **Hyperbolic Sine:** sinh(Value).
- **Hyperbolic Cosine:** cosh(Value).
- **Hyperbolic Tangent:** tanh(Value).

**Conversion**

- **To Radians:** degrees → radians.
- **To Degrees:** radians → degrees.

**Clamp**
Limit output to [0.0, 1.0].

### Outputs

**Value**
Numeric output.

### Math Node

The Math Node carries out math operations.

### Inputs

The node's inputs are dynamic. Some surface only for particular operations — the Addend input, for one, shows up only for the Multiply Add operator.

Value
Input Value. Trigonometric functions read this value as radians.

Addend
Input Addend.

Base
Input Base.

Exponent
Input Exponent.

Epsilon
Input Epsilon.

Distance
Input Distance.

Min
Input Minimum.

Max
Input Maximum.

Increment
Input Increment.

Scale
Input Scale.

Degrees
Input Degrees.

Radians
Input Radians.

### Properties

Operation
The mathematical operator applied to the input values:

Functions

Add :

The sum of the two values.

Subtract :

The difference between the two values.

Multiply :

The product of the two values.

Divide :

The first value divided by the second. Dividing by zero gives zero.

Multiply Add :

The product of the two values, plus Addend .

Power :

The Base raised to the power of Exponent .

Logarithm :

The log of the value to base Base .

Square Root :

The square root of the value.

Inverse Square Root :

One over the square root of the value.

Absolute :

Reads the input value without regard to sign, turning negatives into positives.

Exponent :

Raises Euler's number to the power of the value.

Comparison

Minimum :

Outputs the smaller of the input values.

Maximum :

Outputs the larger of the two input values.

Less Than :

Outputs 1.0 when the first value is below the second, otherwise 0.0.

Greater Than :

Outputs 1.0 when the first value is above the second, otherwise 0.0.

Sign :

Pulls the sign out of the input value. Positives output 1.0, negatives output -1.0, and 0.0 outputs 0.0.

Compare :

Outputs 1.0 when the gap between the two input values is at most Epsilon .

Smooth Minimum :

Smooth Minimum.

Smooth Maximum :

Smooth Maximum.

Rounding

Round :

Rounds the input value entrywise to the nearest integer, going up when the fractional part is 0.5.

Floor :

Rounds the input value down to the nearest integer.

Ceil :

Rounds the input value up to the nearest integer.

Truncate :

Outputs the integer part of the value .

Fraction :

Returns the fractional part of the value .

Truncated Modulo :

Outputs the remainder after the first value is divided by the second.

Floored Modulo :

Returns the positive remainder of a division.

Wrap :

Outputs a value between Min and Max from the absolute gap between the input value and the nearest integer multiple of Max below it.

Snap :

Rounds the input value down to the nearest integer multiple of Increment .

Ping-pong :

Bounces back and forth between 0.0 and the Scale as the input value rises.

Trigonometric

Sine :

The Sine of the input value.

Cosine :

The Cosine of the input value.

Tangent :

The Tangent of the input value.

Arcsine :

The Arcsine of the input value.

Arccosine :

The Arccosine of the input value.

Arctangent :

The Arctangent of the input value.

Arctan2 :

Outputs the Inverse Tangent of the first value divided by the second, measured in radians.

Hyperbolic Sine :

The Hyperbolic Sine of the input value.

Hyperbolic Cosine :

The Hyperbolic Cosine of the input value.

Hyperbolic Tangent :

The Hyperbolic Tangent of the input value.

Conversion

To Radians :

Converts the input from degrees to radians.

To Degrees :

Converts the input from radians to degrees.

Clamp
Holds the output within the range (0.0 to 1.0). See Clamp.

### Outputs

Value
Numerical value output.
