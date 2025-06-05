-- Interface de Teleporte - Dead Rails com movimentação (sem fundo vermelho sólido)
local TeleportLocations = {
    Lab = Vector3.new(100, 10, 100),
    End = Vector3.new(500, 10, -300),
    Casttle = Vector3.new(-200, 10, 250)
}

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Interface principal
local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screenGui.Name = "TeleportUI"
screenGui.ResetOnSpawn = false

-- Fundo com imagem de rosas (sem cor sólida por baixo)
local bgImage = Instance.new("ImageLabel", screenGui)
bgImage.Size = UDim2.new(1, 0, 1, 0)
bgImage.Position = UDim2.new(0, 0, 0, 0)
bgImage.BackgroundTransparency = 1 -- Totalmente transparente
bgImage.Image = "rbxassetid://6034317805" -- Rosas vermelhas
bgImage.ImageTransparency = 0.2
bgImage.ZIndex = 0

-- Frame central com os botões
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Size = UDim2.new(0, 240, 0, 320)
mainFrame.Position = UDim2.new(0.05, 0, 0.3, 0)
mainFrame.BackgroundTransparency = 0.25 -- Levemente transparente
mainFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0) -- Preto translúcido
mainFrame.BorderSizePixel = 4
mainFrame.BorderColor3 = Color3.fromRGB(128, 0, 128)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.ZIndex = 1

-- Título
local titulo = Instance.new("TextLabel", mainFrame)
titulo.Size = UDim2.new(1, 0, 0, 40)
titulo.Position = UDim2.new(0, 0, 0, 0)
titulo.Text = "Teleportes"
titulo.Font = Enum.Font.SourceSansBold
titulo.TextSize = 28
titulo.TextColor3 = Color3.fromRGB(255, 255, 255)
titulo.BackgroundColor3 = Color3.fromRGB(128, 0, 128)

-- Função para criar botões
local function criarBotao(nome, ordem, destino)
    local btn = Instance.new("TextButton", mainFrame)
    btn.Size = UDim2.new(0.8, 0, 0, 50)
    btn.Position = UDim2.new(0.1, 0, 0, 50 + (ordem - 1) * 70)
    btn.BackgroundColor3 = Color3.fromRGB(128, 0, 128)
    btn.Text = "Teleport " .. nome
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.SourceSansBold
    btn.TextSize = 24
    btn.BorderSizePixel = 2
    btn.BorderColor3 = Color3.fromRGB(255, 255, 255)
end

-- Criar botões
criarBotao("Lab", 1, TeleportLocations.Lab)
criarBotao("End", 2, TeleportLocations.End)
criarBotao("Casttle", 3, TeleportLocations.Casttle)
