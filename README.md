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

The API Will provide you with 3 functions

```lua
CyAPI.Functions.AddRunCode(Argument, Name, NewFunction)
```
```lua
CyAPI.Functions.ReconstructRunCode(Argument)
```
```lua
CyAPI.Functions.RemoveRunCode(Argument, Name)
```

You will mainly be using the `AddRunCode` function, and the `RemoveRunCode` function.

## Examples

To add code to a `RenderStepped` loop, you will need the `AddRunCode` function. Here is an example:
```lua
CyAPI.Functions.AddRunCode("RenderStepped", "ExampleName", function()
  print("Hello world!")
end)
```
This will add `print("Hello world!")` in the `RenderStepped` loop.

If you at a later point want this to be removed, you can do this like so:
```lua
CyAPI.Functions.RemoveRunCode("RenderStepped", "ExampleName")
```
Now the code has been removed. 

If you for some reason want to reconstruct all the code within the `RenderStepped` loop, you can do that like so:
```lua
CyAPI.Functions.ReconstructRunCode("RenderStepped")
```
This will reconstruct all the code in the same correct order you added your code. 

## Testing

Here is a code snippet you can copy and paste to test out for yourself.
```lua
----------------------------------- Testing -----------------------------------
local CyAPI = loadstring(game:HttpGet("https://raw.githubusercontent.com/cyerc/CyAPI/refs/heads/main/Source.lua"))()

task.wait(1)
CyAPI.Functions.AddRunCode("RenderStepped", "HiRun", function()
    warn('Hi')
end)

task.wait(1)
CyAPI.Functions.AddRunCode("RenderStepped", "HelloRun", function()
    warn('Hello')
end)

task.wait(1)
CyAPI.Functions.AddRunCode("RenderStepped", "GoodmorningRun", function()
    warn('Goodmorning')
end)

task.wait(1)
CyAPI.Functions.RemoveRunCode("RenderStepped", "HelloRun")
task.wait(1)
CyAPI.Functions.RemoveRunCode("RenderStepped", "GoodmorningRun")
task.wait(1)
CyAPI.Functions.RemoveRunCode("RenderStepped", "HiRun")

----------------------------------- Testing -----------------------------------
```
