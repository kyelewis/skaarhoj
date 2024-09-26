# Actions
## Fields in an action

### Handler Type 
Handler Type is a special field, as it will change the other available fields to configure. An Action can have one main type of trigger it interacts with. The trigger types are (as described earlier in Hardware Components ) Binary , Pulsed , Analog and Speed . A BinaryComponent can create ActDown and ActUp triggers A PulsedComponent can create PulsedValue triggers like +1 and -1 A AnalogComponent can create a AnalogValue triggers from 0 to 1000 A SpeedComponent can create a SpeedValue triggers from -500 to +500, it will always reset to 0 when released. After the Handler Type has been selected you can still add PreProcessors to the Action, that define how to react when a different trigger type comes in. General Action Fields Parameter Each Action can specify a different parameter to control. If no parameter is specified the one defined in the top of the behavior form will be used. 

### Active If Condition 
Each Action can have a condition. If the condition is false the Action stays disabled and is not used. Example: This can be used to specify different Actions dependent the value of a variable Invert Condition Specifies a condition that (if true) inverts the normal direction for control. If you would like to always invert it simply select true 

### Description 
Give the Action a general description


