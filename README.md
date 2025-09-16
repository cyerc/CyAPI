# Roblox Lua CyFrame

CyFrame is a lightweight utility framework that provides an easy way to manage `RenderStepped` and `Heartbeat` callbacks in Roblox.  
It helps you keep your code clean, organized, and optimized by avoiding scattered connections, which can heavily affect performance.

I originally created this Framework for personal use, but decided to release it on GitHub in case others find it useful.

## How to use the Framework:

Copy and paste this code at the top of your script, that's it.

```lua
local CyFrame = loadstring(game:HttpGet("https://raw.githubusercontent.com/cyerc/CyFrame/main/Source.lua"))() 
```

## Functions

The Framework Will provide you with 3 functions

```lua
CyFrame.Functions.AddRunCode(Argument, Name, NewFunction)
```
```lua
CyFrame.Functions.ReconstructRunCode(Argument)
```
```lua
CyFrame.Functions.RemoveRunCode(Argument, Name)
```

You will mainly be using the `AddRunCode` function, and the `RemoveRunCode` function.

## Examples

To add code to a `Heartbeat` loop, you will need the `AddRunCode` function. Here is an example:
```lua
CyFrame.Functions.AddRunCode("Heartbeat", "ExampleName", function()
  print("Hello world!")
end)
```
This will add `print("Hello world!")` in the `Heartbeat` loop.

If you at a later point want this to be removed, you can do this like so:
```lua
CyFrame.Functions.RemoveRunCode("Heartbeat", "ExampleName")
```
Now the code has been removed. 

If you for some reason want to reconstruct all the code within the `Heartbeat` loop, you can do that like so:
```lua
CyFrame.Functions.ReconstructRunCode("Heartbeat")
```
This will reconstruct all the code in the same correct order you added your code. 

## Testing

Here is a code snippet you can copy and paste to test out for yourself.
```lua
local CyFrame = loadstring(game:HttpGet("https://raw.githubusercontent.com/cyerc/CyFrame/main/Source.lua"))()

task.wait(1)
CyFrame.Functions.AddRunCode("Heartbeat", "HiRun", function()
    warn('Hi')
end)

task.wait(1)
CyFrame.Functions.AddRunCode("Heartbeat", "HelloRun", function()
    warn('Hello')
end)

task.wait(1)
CyFrame.Functions.AddRunCode("Heartbeat", "GoodmorningRun", function()
    warn('Goodmorning')
end)

task.wait(1)
CyFrame.Functions.RemoveRunCode("Heartbeat", "HelloRun")
task.wait(1)
CyFrame.Functions.RemoveRunCode("Heartbeat", "GoodmorningRun")
task.wait(1)
CyFrame.Functions.RemoveRunCode("Heartbeat", "HiRun")
```
