# Roblox Lua CyAPI

CyAPI is a lightweight utility framework that provides an easy way to manage `RenderStepped` and `Heartbeat` callbacks in Roblox.  
It helps you keep your code clean, organized, and optimized by avoiding scattered connections, which can heavily affect performance.

I originally created this API for personal use, but decided to release it on GitHub in case others find it useful.

## How to use the API:

Copy and paste this code at the top of your script, that's it.

```lua
local CyAPI = loadstring(game:HttpGet("https://raw.githubusercontent.com/cyerc/CyAPI/refs/heads/main/Source.lua"))() 
```

## Functions

The API Will provided you with 3 functions

```lua
CyAPI.Functions.AddRunCode(Argument, Name, NewFunction)
```
```lua
CyAPI.Functions.ReconstructRunCode(Argument)
```
```lua
CyAPI.Functions.RemoveRunCode
```

You will mainly be using the `AddRunCode` function, and the `RemoveRunCode` function.

## Examples

To add code to a renderstepped loop, you will need the AddRunCode function. Here is an example:
```lua
CyAPI.Functions.AddRunCode("RenderStepped", "ExampleName", function()
  print("Hello world!")
end)
```
