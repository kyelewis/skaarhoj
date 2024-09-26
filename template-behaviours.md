# Template Behaviours

## None
Start with no selected Template Behavior 

## Set specific value 
Use this template if you want any action on the component to set a specified value on the selected parameter. Example: Setting a AUX of an ATEM to input 1 using a button 

## Set a value by index - Same as Set specific value, but you can specify an index of the option for the specific parameter. Example: Setting the current Scene in OBS to the 5th scene from the start 
## Change by Step Use this whe you want to move up and down a value using an encoder or 4way button. Example: Use an encoder to control the current shutter speed of a camera This Template Behavior is the most versatile one. It is almost always usable
## Change by step for larger ranges - Same as Change by step, but for longer value ranges. Encoders will move more steps if rotated faster and a fine / coarse selection can be made by pressing down shortly. Buttons will continue to increment when held down. Example: Changing the electronic shutter in .01 values of a degree
## Change by step with limited values Sometimes a parameter might have many options to choose from but you want to limit the possible options that can be selected with the current button or encoder. Use this Settings template to define several valid options that can be set for the parameter Example: Making an Encoder only switch between 3 certain WhiteBalance modes (eg Manual/Preset1/Preset2)
## Change by step with confirmation Use this Template Behavior on encoders and 4 way buttons if you want to have them not immediately change the value, but let you select and change by pressing down. If no change is confirmed the value shown will jump back to the current value after the specified time. [1] Example: Loading a new setup file on an Arri Camera. On an encoder use left and right to select first then press down to confirm. 

## Change a value on fader / potentiometer This is the default Template Behavior to use when mapping a parameter to a fader or LEDBar Example: Controlling Gain on an RCP Joystick
## Change a value with motorized fader This is the default Template Behavior to use when mapping a parameter to a motorized fader. It will correctly send back the position to the fader if the value changes in the system. Example: Controlling Iris using a ColorFlyV2 Fader

## Toggle two options Choose this Template Behavior for any kind of On/Off, Show/Hide, Enable/Disable scenarios. The button will light up bright once the function is activated and show dimmed if not. Example: Turning on and off bars on a camera
## Toggle on hold This Template Behavior can be used similar to the above, but it will only react after pushing down for a specified amount of time, defaults to 1000 milliseconds Example: A NETIO Power outlet shall only be toggled when the button is held down for one second

## Trigger Action Use this template for all kind of one-shot parameters (commands) Example: Triggering OnePush Autofocus on a camera
## Speed parameter This is the default Template Behavior for mapping things to a speed component (Joysticks). But it can also be used to control speed commands from other components like encoders Example: Control Pan Speed using a joystick
## Binary Output (for GPO) This Template Behavior uses the parameter to set or clear the Output of a GPO contact on RCPs or LinkIO boxes. Example: map a TallyFlag to the closed contact on the back of an RCP
## Hold-Down Used for parameters with two options. When the button is pressed down the parameter is set to on. When it is released it is set to off. Useful for GPI Inputs Example: Mapping Record to the state of a GPI closed contact of an RCP
## Display value (without control) - Show a value that does not provide control, or deliberately lock control of a value. Example: Show the battery voltage of a camera 


