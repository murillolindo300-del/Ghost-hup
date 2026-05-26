local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "GhostHubUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

-- BOTÃO FLUTUANTE
local openBtn = Instance.new("ImageButton")
openBtn.Parent = gui
openBtn.Size = UDim2.new(0,70,0,70)
openBtn.Position = UDim2.new(0,20,0.5,-35)
openBtn.BackgroundColor3 = Color3.fromRGB(20,20,20)
openBtn.Image = "rbxassetid://COLOQUE_ID_DA_IMAGEM"
openBtn.Active = true
openBtn.Draggable = true
openBtn.BorderSizePixel = 0

local openCorner = Instance.new("UICorner", openBtn)
openCorner.CornerRadius = UDim.new(1,0)

local openStroke = Instance.new("UIStroke", openBtn)
openStroke.Color = Color3.fromRGB(170,0,255)
openStroke.Thickness = 2

-- MENU PRINCIPAL
local frame = Instance.new("Frame")
frame.Parent = gui
frame.Size = UDim2.new(0,600,0,350)
frame.Position = UDim2.new(0.5,-300,0.5,-175)
frame.BackgroundColor3 = Color3.fromRGB(10,10,10)
frame.Visible = false
frame.Active = true
frame.Draggable = true

local frameCorner = Instance.new("UICorner", frame)
frameCorner.CornerRadius = UDim.new(0,18)

local frameStroke = Instance.new("UIStroke", frame)
frameStroke.Color = Color3.fromRGB(140,0,255)
frameStroke.Thickness = 2

-- HEADER
local header = Instance.new("ImageLabel")
header.Parent = frame
header.Size = UDim2.new(1,0,0,120)
header.BackgroundTransparency = 1
header.Image = "rbxassetid://COLOQUE_ID_DA_IMAGEM"
header.ScaleType = Enum.ScaleType.Crop

local headerCorner = Instance.new("UICorner", header)
headerCorner.CornerRadius = UDim.new(0,18)

-- TITULO
local title = Instance.new("TextLabel")
title.Parent = frame
title.Position = UDim2.new(0,20,0,130)
title.Size = UDim2.new(1,-40,0,40)
title.BackgroundTransparency = 1
title.Text = "GHOST HUB"
title.TextColor3 = Color3.fromRGB(170,0,255)
title.Font = Enum.Font.GothamBlack
title.TextScaled = true

-- WALKSPEED TEXTO
local speedText = Instance.new("TextLabel")
speedText.Parent = frame
speedText.Position = UDim2.new(0,20,0,190)
speedText.Size = UDim2.new(0,200,0,30)
speedText.BackgroundTransparency = 1
speedText.Text = "WALK SPEED"
speedText.TextColor3 = Color3.fromRGB(255,255,255)
speedText.Font = Enum.Font.GothamBold
speedText.TextSize = 22
speedText.TextXAlignment = Enum.TextXAlignment.Left

-- INPUT
local speedBox = Instance.new("TextBox")
speedBox.Parent = frame
speedBox.Position = UDim2.new(0,20,0,230)
speedBox.Size = UDim2.new(0,300,0,45)
speedBox.BackgroundColor3 = Color3.fromRGB(20,20,20)
speedBox.TextColor3 = Color3.fromRGB(255,255,255)
speedBox.PlaceholderText = "Digite a velocidade..."
speedBox.Font = Enum.Font.Gotham
speedBox.TextSize = 20
speedBox.ClearTextOnFocus = false

local speedCorner = Instance.new("UICorner", speedBox)
speedCorner.CornerRadius = UDim.new(0,10)

local speedStroke = Instance.new("UIStroke", speedBox)
speedStroke.Color = Color3.fromRGB(170,0,255)

-- BOTÃO APLICAR
local applyBtn = Instance.new("TextButton")
applyBtn.Parent = frame
applyBtn.Position = UDim2.new(0,340,0,230)
applyBtn.Size = UDim2.new(0,230,0,45)
applyBtn.BackgroundColor3 = Color3.fromRGB(120,0,255)
applyBtn.Text = "APLICAR"
applyBtn.TextColor3 = Color3.fromRGB(255,255,255)
applyBtn.Font = Enum.Font.GothamBlack
applyBtn.TextSize = 22

local applyCorner = Instance.new("UICorner", applyBtn)
applyCorner.CornerRadius = UDim.new(0,10)

-- FECHAR
local closeBtn = Instance.new("TextButton")
closeBtn.Parent = frame
closeBtn.Position = UDim2.new(1,-45,0,10)
closeBtn.Size = UDim2.new(0,35,0,35)
closeBtn.BackgroundColor3 = Color3.fromRGB(30,30,30)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.fromRGB(170,0,255)
closeBtn.Font = Enum.Font.GothamBlack
closeBtn.TextSize = 22

local closeCorner = Instance.new("UICorner", closeBtn)
closeCorner.CornerRadius = UDim.new(1,0)

-- ABRIR MENU
openBtn.MouseButton1Click:Connect(function()
	frame.Visible = not frame.Visible
end)

-- FECHAR MENU
closeBtn.MouseButton1Click:Connect(function()
	frame.Visible = false
end)

-- WALKSPEED
applyBtn.MouseButton1Click:Connect(function()
	local speed = tonumber(speedBox.Text)

	if speed then
		local character = player.Character or player.CharacterAdded:Wait()
		local humanoid = character:FindFirstChildOfClass("Humanoid")

		if humanoid then
			humanoid.WalkSpeed = speed
		end
	end
end)
