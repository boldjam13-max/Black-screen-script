local CoreGui = game:GetService("CoreGui")
local player = game.Players.LocalPlayer
local parent = CoreGui:FindFirstChild("RobloxGui") or player:WaitForChild("PlayerGui")
if parent:FindFirstChild("BlackScreenToggleGui") then
    parent.BlackScreenToggleGui:Destroy()
end
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "BlackScreenToggleGui"
screenGui.IgnoreGuiInset = true -- Covers the whole screen including top bar
screenGui.Parent = parent
local blackFrame = Instance.new("Frame")
blackFrame.Name = "BlackBackground"
blackFrame.Size = UDim2.new(1, 0, 1, 0)
blackFrame.BackgroundColor3 = Color3.new(0, 0, 0) -- Pure black
blackFrame.Visible = false -- Starts turned off
blackFrame.ZIndex = 1
blackFrame.Parent = screenGui
local toggleButton = Instance.new("TextButton")
toggleButton.Name = "ToggleButton"
toggleButton.Size = UDim2.new(0, 160, 0, 45)
toggleButton.Position = UDim2.new(0.5, -80, 0.85, -22) -- Bottom center of your screen
toggleButton.BackgroundColor3 = Color3.fromRGB(35, 35, 35) -- Dark grey button
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255) -- White text
toggleButton.Font = Enum.Font.GothamBold
toggleButton.Text = "Black Screen: OFF"
toggleButton.TextScaled = true
toggleButton.ZIndex = 2 -- Keeps the button ON TOP of the black screen so you can click it
toggleButton.Parent = screenGui
local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 8)
uiCorner.Parent = toggleButton
toggleButton.MouseButton1Click:Connect(function()
    blackFrame.Visible = not blackFrame.Visible
     if blackFrame.Visible then
        toggleButton.Text = "Black Screen: ON"
        toggleButton.TextColor3 = Color3.fromRGB(255, 70, 70) -- Turns text red when active
    else
        toggleButton.Text = "Black Screen: OFF"
        toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    end
end)
