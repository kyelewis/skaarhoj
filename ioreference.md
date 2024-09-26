# Parameter Reference (IOReference)

## Format

Type:part1/part2/part3:modifier1:modifier2:modifier3

You can nest other IOReferences in some places inside curly brackets

## Types

### Literal Values
```
3
true
page1
[red,green,blue]
```

### String 
```
String:{\"DATA\":\"Custom JSON value\"} 
```

### Var (Variable)
Var:MyVariable

#### Examples
```
Var:SEC_Page:Name (modifier displays the friendly name of the variable)
Var:DeviceIndex:Current:Name (modifier displays the label of the current value) 
```

### DC (Device Core)
DC:[core name]/[device index]/[parameter name]/[dimension1 index]/[dimension2 index]/...:Modifiers 

Indexes are all IOReferences

#### Examples
```
DC:bmd-atem/{Var:DeviceIndex}/AuxSource/{Var:AuxChannel}/ 
```

### Panels
Panels:[target type]/[target index]:[panel parameter type] 
Index is IOReference

Target Type:
Canvas, Panel, CanvasOfPanel

Parameter Types:
Panels:CanvasOfPanel/0:SleepTime (minutes) 
Panels:CanvasOfPanel/0;DimTime (in minutes) 
Panels:CanvasOfPanel/0:DisplayBrightness (0-8) 
Panels:CanvasOfPanel/0:LEDBrightness (0-8) 
Panels:CanvasOfPanel/0:GlobalBrightness (0-8) 
Panels:CanvasOfPanel/0:Sleep "on" or "off"
Panels:CanvasOfPanel/0:ResetSleepTimer (one-shot trigger) 
Panels:CanvasOfPanel/0:Name (read only) 
Panels:CanvasOfPanel/0:Model (read only) 

### System 
System:PanelLock - Lock function for the whole of reactor
System:IPAddress - Show the IP Address of reactor. Can also change the system IP using a set value command or the SKAARHOJ:ChangeIP Template Behavior 
System:CurrentProject - Allows to trigger a change of projects using SetValue
System:RestartEngine - Perform a restart of reactors engine, like switching projects
System:ProjectTitle - Show current Project title
System:ConfigTitle - Show current name of root layer
System:UptimeFormatted - Show uptime since Reactor was started
System:Panels:Connected - Number of currently connected panels
System:Panels:Warnings - Number of panels with warnings
System:Panels:Unconnected - Number of unconnected panels (errors)
System:Panels:LastEvent - Last event as a string, eg. \"Down (T)\" if a four way buttons top edge was pressed down.
System:Panels:LastEventSource - The HWC source of last event, including panel ID, on form \"P[panel id]#[HWC id]\", for example \"P1#43\"
System:Devices:Connected - Number of connected devices
System:Devices:Warnings - Number of devices with warnings
System:Devices:Unconnected - Number of unconnected devices (errors)
System:Devices/[idx]:Name - Name of devices. idx is just an index.
System:Warnings - Total number of warnings in Reactor
System:Errors - Total number of errors in Reactor

### Behaviour
Behavior:[sub type]:[additional type]:Modifiers...

#### Examples
```
Behaviour:IOReference:Name
Behaviour:Name
Behaviour:Path
Behaviour:ID
Behaviour:Panels
Behaviour:Script
Behaviour:Const:[constant key]
Behavior:LastEvent:Type   Type of last event. Options: Binary, Pulsed, Analog, Speed 
Behavior:LastEvent:TimeToNow:[Limit]   This returns the time in milliseconds that has passed since the last event. Although setting a limit is optional, it's recommended to set it at or above the comparison value for performance efficiency. If a limit is set, it designates the maximum returned value. 
Behavior:LastEvent/Binary:Pressed Returns whether the last binary trigger was pressed (ActDown) or not (ActUp). Options: true, false 
Behavior:LastEvent/Binary:Edge Returns which edge the last binary trigger sent. Options: NoEdge, Top, Left, Bottom, Right, Encoder 
Behavior:LastEvent/Pulsed:Direction Returns the direction of the last pulsed trigger received Options: Up, Down 
Behavior:LastEvent/Pulsed:Value Returns the value of the last pulsed trigger 
Behavior:LastEvent/Analog:Value Returns the value of the last analog trigger (0 to 1000) 
Behavior:LastEvent/Speed:Value Returns the value of the last intensity trigger (-500 to 500) 
Behavior:Events/[Action Name]:TimeToNow:[Limit] Returns the time in milliseconds that has passed since the last accepted trigger for the specified Action. It is recommended to set a maximum limit for performance reasons in reactor. 
Behavior:Events/[Action Name]:SequenceStep: The current sequence step being executed (See Binary Sequence ) 
```

### Preset 
Preset:[preset kind name]/[command]/[preset index]/[device index]/ 

```
Store
Recall
Delete 
```

Preset index is an IOReference

### Flag  
Flag:[flag group name]/[flag color]/[flag number]:modifier1:modifier2:modifier3 

```
Flag color options: [Red, Green, Blue, White] 
Index bounds: 0-99
NOTE: Flags are generally used for SKAARHOJ Default Tally Forwarding and Routing Triggers. 
```

### Const
Const:[constant set name]/[row index]/[constant name]/:Modifiers...

Index is an IOReference.

#### Examples
```
Const:CameraSelector/0/CameraName 
Const:CameraSelector/{Var:CameraIndex:Current:Offset:-1}/CameraName 
```

## Modifiers

Used to access additional information from the parameter

### Name
Returns the name of the reference, such as a parameter or variable name. 

DC, Var and Const

### Default
Returns the default values of the IO reference.

DC and Var

### Default:Name 
Returns the names/labels of the default values of the IO reference. 

DC and Var

### All
Returns all option values for a parameter. For an integer range with less than 100 values, it will calculate and return that as an option list.

DC and Var

### Exists
Returns true if the reference exists

DC, Var and Const

### Mutable
Returns true if the reference can be changed

DC, Var and Const

### Assumed
Returns true if a parameter is assumed in the core

DC

### FineSteps
Returns the recommended fine steps for a Device Core; otherwise, returns 1.

DC

### CoarseSteps
Returns the recommended coarse steps for a Device Core; otherwise, returns 10. 

DC

### ASCIIOnly
Returns true if only ASCII characters are found in the return value. 

DC, Var and Const

### Current
Current Returns the current values. Same as not using Current modifier

DC, Var and Const

### Current:Name
Returns the names of the current values

DC, Var and Const

### Current:Normalized
Returns the normalized value in the range of 0-1000

DC, Var 

### Current:NormalizedInverted
Returns the normalized value in the inverted range of 1000-0

DC, Var

### Current:Percent
Returns the normalized value in the range of 0-100

DC, Var

### Current:Remap:[from]:[to]
Current:Remap:[low int]:[high int]:[optional integer divisor, default to 1] 

Returns the value normalized to the range [low int]-[high int], divided by the divisor.

DC, Var

### Current:Index
Returns the index of the current value from the option list, starting with zero. Works only for parameters and variables with Option Lists, not ranges.

DC, Var

### Current:Count

Returns the number of values in the IO reference array.

DC, Var, Const

### Current:Join:Token

Returns an IO reference with a single value, a concatenation of all values it had, separated by the Token string.

DC, Var, Const

### Current:SingleValue:Index

Returns a single value out of the current values by index 

DC Var

### Current:Offset:[int]

Returns the value with [int] added to it  

Yes Yes Yes 

### Current:BufferTimeToNow

Returns the time in milliseconds from the buffered value time out to the current time  

DC
 
### Confirm:[int]

Changes the value only locally, waiting to be confirmed for [int] milliseconds

DC

### Wait:[int]

Similar to Confirm, but the change is automatically accepted after the time expires

DC

### Index:[integer comma list incl. \"Last\" keyword / Constant or Variable Reference] 

Returns option value with index [int] or if it's a string, the constant of the HWC Behavior. 

DC, Var

### Index:[integer comma list incl. \"Last\" keyword / Constant or Variable Reference]:Name 

Returns the name of the option value with index [int]. Yes Yes No 

DC, Var

### Index:[integer comma list incl. \"Last\" keyword/ Constant or Variable Reference]:Exists 

Returns true if the index exists 

DC, Var

### Index:[integer comma list incl. \"Last\" keyword / Constant or Variable Reference]:Raw 

Returns the raw index value of the option value with that index.

DC, Var

### DimensionName
DimensionName:[int]:[optional int] 

Returns the name of the specified dimension (0 index) if 2 integers are specified returns the name of the specified Element

DC

### ID 
ID:[integer / Constant or Variable Reference] 

Return an option by its value ID (different than index on some cores) also supports :Name and :Exists 

DC, Var

