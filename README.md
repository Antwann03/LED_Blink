# Overview

During the lab we designed a module that blinks the LED every second on the Zybo Z7-10 development board. 

# Design Summary
## Blinking LED with Zybo Z7-10 Development Board
To begin with our first VHDL Lab we must begin with defining the I/O ports that's given to implement.

Given four signals name such as sys_clk, rst, led_en and led_out where all of them are one bit width and three of them are Inputs and one of them is an output. 

Here's the following syntax VHDL code:

```
signal sys_clk: in std_logic;
signal rst: in std_logic;
signal led_en: in std_logic;
signal led_out: out std_logic;
```

To declare a generic given name as CLK_CYCLES_PER_TOGGLE given a default value as 62,500,000.

generic is a value you set when you instantiate the module. Essentially a consant parameter pased into the module from outside.
```
generic (CLK_CYCLES_PER_TOGGLE: integer := 62500000);
```

The design uses an internal counter that increments on each rising edge of the system clock. Once the counter hits the CLK_CYCLES_PER_TOGGLE threshold, the LED output flips its state and counter resets to zero. If either reset signal goes high or the LED enable is low, both the counter and led_out are immediately cleared to 0. While the development board running at 125 MHz and the default parameter value of 62500000, LED toggles every 0.5 seconds.

```

```

The testbench (TB) was used to verify the functionality of the blinking_led entity just in simulation. There was three cases done to test the simulations. Such as the LED output and counter must both be cleared when reset is active or the enable signal is low, the LED must toggle at a fixed interval determiend by the clock parameter, and disabling the LED while it is acitvely toggling  must immediately drive the output back to zero.

```

```
## RGB LED with Zybo Z7-10 Development Board


# Verification and Testing
## Results for blinking_led_TB.vhd 

### Test Case 1: Reset Behavior

### Test Case 2: Disabled Output

### Test Case 3: Led Toggling


### Blinking on Zybo Z7-10 Board Photo

## Results for RGB_LED.vhd

### Test Case 1:

### Test Case 2:

### Test Case 3:

### Test Case 4:

### Test Case 5:

### Test Case 6:

### Test Case 7:

### RGB LED Zybo Z7-10 Board Photo

# Known Issues and Limitations
One issue I ran into was expecting the hardware to update automatically once the bitstream finished generating. However, the bitstream must be first prrogrammed onto the device before any changes are reflected onto the hardware, in this case the RGB LED on the Zybo Z7-10.
# References

