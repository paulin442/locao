local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/ScriptCentralBot/GUILibraries/main/MinimalisticGUI.lua"))()

-- Create GUI
local GUI = Library.CreateGUI({
    Name = "Mini City RP ESP",
    SizeX = 200,
    SizeY = 100
})

-- ESP Tab
local ESPTab = GUI.AddTab("ESP")

-- ESP Toggle
local ESPToggle = ESPTab.AddToggle("ESP", false)
ESPToggle.OnChanged:Connect(function(state)
    if state then
        -- Enable ESP
        for _, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer then
                local ESP = Instance.new("BillboardGui")
                ESP.Name = "ESP"
                ESP.AlwaysOnTop = true
                ESP.Size = UDim2.new(0, 5, 0, 5)
                ESP.BindingName = "ESP"
                ESP.Parent = v.Character.Head
                local TextLabel = Instance.new("TextLabel")
                TextLabel.Text = v.Name
                TextLabel.Size = UDim2.new(0, 100, 0, 20)
                TextLabel.Font = Enum.Font.SourceSans
                TextLabel.FontSize = Enum.FontSize.Size14
                TextLabel.TextColor3 = Color3.new(1, 1, 1)
                TextLabel.Parent = ESP
            end
        end
    else
        -- Disable ESP
        for _, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer then
                local ESP = v.Character:FindFirstChild("ESP")
                if ESP then
                    ESP:Destroy()
                end
            end
        end
    end
end)

-- Run Script
GUI.Run()
