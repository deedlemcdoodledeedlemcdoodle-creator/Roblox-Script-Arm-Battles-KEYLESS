-- Arm Battles Script by nazrinDevy
-- Load Rayfield UI Library
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Create the main window
local Window = Rayfield:CreateWindow({
    Name = "Arm Battles Script",
    LoadingTitle = "Script Loading",
    LoadingSubtitle = "by nazrinDevy",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "ArmBattlesConfig",
        FileName = "ArmBattlesSave"
    },
    Discord = {
        Enabled = false,
        Invite = "",
        RememberJoins = true
    },
    KeySystem = false
})

-- Services
local Players = game:GetService("Players")
local VirtualInputManager = game:GetService("VirtualInputManager")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")

local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()

-- Global variables for toggles
getgenv().AutoHitEnabled = false
getgenv().AutoLiftEnabled = false

-- Function for simulating mouse click (for auto attacks)
local function simulateClick()
    VirtualInputManager:SendMouseButtonEvent(0, 0, 0, true, game, 1)
    wait(0.01)
    VirtualInputManager:SendMouseButtonEvent(0, 0, 0, false, game, 1)
end

-- Hit Tab (Auto Attack for Battles)
local HitTab = Window:CreateTab("Hit", 4483362458)

local HitToggle = HitTab:CreateToggle({
    Name = "Auto Hit (Attack to Win)",
    CurrentValue = false,
    Flag = "AutoHitToggle",
    Callback = function(Value)
        getgenv().AutoHitEnabled = Value
        if Value then
            spawn(function()
                while getgenv().AutoHitEnabled do
                    simulateClick()
                    wait(0.001) -- Fast attack rate
                end
            end)
        end
        Rayfield:Notify({
            Title = "Auto Hit",
            Content = Value and "Enabled - Auto attacking!" or "Disabled",
            Duration = 3,
            Image = 4483362458,
        })
    end,
})

-- Lift Tab (Auto Lift for Strength/Boost)
local LiftTab = Window:CreateTab("Lift", 4483362458)

local LiftToggle = LiftTab:CreateToggle({
    Name = "Auto Lift (Boost Strength)",
    CurrentValue = false,
    Flag = "AutoLiftToggle",
    Callback = function(Value)
        getgenv().AutoLiftEnabled = Value
        if Value then
            spawn(function()
                while getgenv().AutoLiftEnabled do
                    simulateClick()
                    wait(0.005) -- Slower rate for lifting action
                end
            end)
        end
        Rayfield:Notify({
            Title = "Auto Lift",
            Content = Value and "Enabled - Auto lifting!" or "Disabled",
            Duration = 3,
            Image = 4483362458,
        })
    end,
})

-- Credits Tab
local CreditsTab = Window:CreateTab("Credits", 4483362458)

CreditsTab:CreateLabel("Script Created by nazrinDevy")
CreditsTab:CreateParagraph({
    Title = "About nazrinDevy",
    Content = "nazrinDevy is an exceptional Roblox script developer known for creating high-quality, user-friendly exploits and tools tailored for games like Arm Battles. With a passion for gaming and coding, nazrinDevy delivers seamless GUIs using libraries like Rayfield, ensuring easy toggles for features such as auto-attacks, teleports, and more. Check out nazrinDevy's work on platforms like ScriptBlox, V3rmillion, and Roblox scripting communities for even more amazing scripts that enhance your gameplay experience without hassle. Follow nazrinDevy for updates, custom requests, and the latest in Roblox automation!"
})

CreditsTab:CreateLabel("Thanks for using this script! - nazrinDevy")

-- Optional: Add a button to destroy the GUI
CreditsTab:CreateButton({
    Name = "Unload Script",
    Callback = function()
        Rayfield:Destroy()
    end,
})
