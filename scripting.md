# Scripting

Skaarhoj scripts are written in javascript and processed by otto.

They only support ES5 syntax, which means a bunch of ES6 and newer syntax is unsupported- this means no:
- let / const
- template literals
- arrow functions
- classes
- enhanced object literals ({ name } instead of { name: name })
- destructuring
- spread/rest
- modules/import
- promises
- for-of
- Setor Map
- Array.from or Object.assign
- Nullish Coalescing
- Optional Chaining

setTimeout and setInterval are not part of the otto implementation either.

## Available Functions

Sleep(milliseconds: number)
GetIOReferenceValues(ioref: string, value: string): string[]
GetIOReferenceFirstValue(ioref:string, value: string: string
SetIOReferenceValues(ioref: string, value: string)
SetIOReferenceValuesWithMeta(ioref: string, metamap: Record<string, string>, value: string)
GetEvent()
console.log()

## Example

```js
let event = GetEvent();
if(event.Binary !== undefined && event.Binary.Pressed) {
  // Do the thing
}
```

## Additional
The Behaviour:Script:IsRunning IOReference can be used in an action to set a different visual for a button when a visual is running.
