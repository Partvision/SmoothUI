# Roblox Animated UI Library

A lightweight, modern, and fully animated UI library built for Roblox scripts. Offers smooth transitions, clean visual styling, and isolated dragging logic to prevent control interference.

---

## Features
- **Window Dragging:** Restricted strictly to the header bar to prevent accidental UI dragging while interacting with sliders or controls.
- **Fluid Animations:** Custom transitions powered by `TweenService` for tab switches, button hovers, toggles, and text focus states.
- **Safe Rendering:** Automatic parent selection (`PlayerGui` default with `CoreGui` fallback) for maximum executor compatibility.
- **Auto-Canvas Sizing:** Scrolling pages dynamically calculate content heights based on added elements.

---

## Quick Start Example

```lua
-- Load the library (Replace with loadstring if hosting remotely)
local Library = loadstring(game:HttpGet("YOUR_RAW_GITHUB_URL_HERE"))()

-- Create Window
local Window = Library.new("Dashboard UI")

-- Create Tabs
local MainTab = Window:CreateTab("Main")
local SettingsTab = Window:CreateTab("Settings")

-- Add Elements to Main Tab
MainTab:AddButton("Execute Action", function()
    print("Button Pressed!")
end)

MainTab:AddToggle("Auto Farm", false, function(state)
    print("Auto Farm Active:", state)
end)

MainTab:AddSlider("WalkSpeed", 16, 100, 16, function(value)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
end)

-- Add Elements to Settings Tab
SettingsTab:AddTextInput("Enter Config Name...", false, function(text)
    print("Config Name Set To:", text)
end)

SettingsTab:AddTextInput("Multiplier (Numbers Only)...", true, function(val)
    print("Numeric Input:", val)
end)
