-- Mod Menu + Invincibility Script for Delta Mobile Executor (Roblox: Undertale Last Corridor)

-- Instances
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local GodModeBtn = Instance.new("TextButton")

-- Properties
ScreenGui.Parent = game:GetService("CoreGui")
ScreenGui.Name = "ULTC_modmenu"

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Position = UDim2.new(0.05, 0, 0.2, 0)
Frame.Size = UDim2.new(0, 220, 0, 120)
Frame.Active = true
Frame.Draggable = true

Title.Parent = Frame
Title.BackgroundTransparency = 1
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Text = "Last Corridor Mod Menu"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 18

GodModeBtn.Parent = Frame
GodModeBtn.Position = UDim2.new(0.1, 0, 0.5, 0)
GodModeBtn.Size = UDim2.new(0.8, 0, 0.3, 0)
GodModeBtn.Text = "God Mode: OFF"
GodModeBtn.Font = Enum.Font.SourceSans
GodModeBtn.TextSize = 16
GodModeBtn.TextColor3 = Color3.new(1,1,1)
GodModeBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 255)

-- God Mode Logic
local godMode = false
local godLoop

GodModeBtn.MouseButton1Click:Connect(function()
    godMode = not godMode
    if godMode then
        GodModeBtn.Text = "God Mode: ON"
        GodModeBtn.BackgroundColor3 = Color3.fromRGB(40, 180, 60)
        godLoop = game:GetService("RunService").RenderStepped:Connect(function()
            local plr = game.Players.LocalPlayer
            if plr and plr.Character and plr.Character:FindFirstChild("Humanoid") then
                plr.Character.Humanoid.Health = math.huge
                plr.Character.Humanoid.MaxHealth = math.huge
            end
        end)
    else
        GodModeBtn.Text = "God Mode: OFF"
        GodModeBtn.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
        if godLoop then
            godLoop:Disconnect()
        end
    end
end)
