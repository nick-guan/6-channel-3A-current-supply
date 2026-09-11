# 6-channel-3A-current-supply
This is a 6 channel current source, with a maximum of 3A each channel. The current box is powered with Xantrex XKW 20-50 DC Power Supply, and is controlled using linduino (DC2026C) and LTC2668 (16 channel DAC, integrated onto the evaluation board DC2025A-A).
## Design
The figure below shows the circuit diagram for one channel. The op-amp model is OPA541, ordered from digikey. For any user defined voltage to the DAC input pin, there will be current with the same magnitude as the input voltage running through the load. This current supply box was originally designed to power the shim coils, so the load in this diagram is the 1.8 mH shim coil. A sample coil with approximately the same inductance was made in the testing stage, which is also the coil used in this page.

<img src="image/circuit (3).png" width="600">

### An observation with powering the op-amp
The op-amp is powered with Xantrex XKW 20-50 DC Power Supply, where the difference between the positive rail and negative rail of the op-amp is 10V. However, we found that if we connect the ground of the linduino+DACs to the negative rail of the op-amp (so the op-amp is powered with 10V and 0V on two rails) , and when sending positive input voltage to the op-amp, the op-amp failed to drive positive current across the load. But if we connect the ground of the linduino+DACs to the positive rail of the op-amp (so the op-amp is powered with 0V and -10V on two rails), and when sending negative input voltage to the op-amp, the op-amp is able to drive negative current through the load. 

Since we can always reverse the output pins to convert from negative current to positive current, this issue does not affect using the current supply.
### Purpose of the RC snubber parallel to the load
