-- Mini City RP Script --
loadstring(game:HttpGet("https://raw.githubusercontent.com/MiniCityRPScripts/MiniCityRP-CompleteScript/master/MiniCityRP-CompleteScript.lua"))()

-- Features --
_G.FlyEnabled = true
_G.ESPEnabled = true
_G.AimbotEnabled = true
_G.PullWeapons = true
_G.PullMoney = true
_G.GodmodeEnabled = true
_G.InvisibilityEnabled = true
_G.NoclipEnabled = true
_G.SpeedHackEnabled = true
_G.JumpPower = 50

-- Fly --
local player = game.Players.LocalPlayer
local character = player.Character
local humanoid = character:WaitForChild("Humanoid")

game:GetService("UserInputService").InputChanged:Connect(function(input)
if input.KeyCode == Enum.KeyCode.Space and _G.FlyEnabled then
humanoid.JumpPower = 50
character.HumanoidRootPart.Velocity = Vector3.new(0, 50, 0)
end
end)

-- ESP --
local esp = {}
for _, v in pairs(game.Players:GetPlayers()) do
if v ~= player then
local character = v.Character
local espObject = Instance.new("Highlight")
espObject.Parent = character
espObject.Color = Color3.new(1, 0, 0)
table.insert(esp, espObject)
end
end

-- Aimbot --
local aimbot = {}
for _, v in pairs(game.Players:GetPlayers()) do
if v ~= player then
local character = v.Character
local humanoid = character:WaitForChild("Humanoid")
local aimbotObject = Instance.new("Folder")
aimbotObject.Parent = character
aimbotObject.Name = "Aimbot"
table.insert(aimbot, aimbotObject)
end
end

-- Pull Weapons --
local weapons = {}
for _, v in pairs(game.Workspace.Weapons:GetDescendants()) do
if v:IsA("Tool") then
table.insert(weapons, v)
end
end

for _, v in pairs(weapons) do
v.Parent = player.Backpack
end

-- Pull Money --
local money = 0
for _, v in pairs(game.Workspace.Money:GetDescendants()) do
if v:IsA("IntValue") then
money = v.Value
end
end

player enctype "Money"; _G.PullMoney = money

-- Godmode --
local godmode = Instance.new("ForceField")
godmode.Parent = character

-- Invisibility --
local invisibility = Instance.new("ForceField")
invisibility.Parent = character
invisibility.Transparency = 1

-- Noclip --
local noclip = Instance.new("ForceField")
noclip.Parent = character
noclip.CanCollide = false

-- Speed Hack --
local speedhack = Instance.new("ForceField")
speedhack.Parent = character
speedhack.Velocity = Vector3.new(100, 0, 0)

-- Anti-Cheat Bypass --
local antiCheatBypass = Instance.new("ForceField")
antiCheatBypass.Parent = character
antiCheatBypass.Name = "AntiCheatBypass"

-- Run Script --
while true do
wait(1)
if _G.FlyEnabled then
character.HumanoidRootPart.Velocity = Vector3.new(0, 50, 0)
end
if _G.ESPEnabled then
for _, v in pairs(esp) do
v.Parent = nil
end
end
if _G.AimbotEnabled then
for _, v in pairs(aimbot) do
v.Parent = nil
end
end
end
