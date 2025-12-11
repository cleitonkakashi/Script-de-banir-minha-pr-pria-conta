--== SUBMUNDO BLACKTZ ==--

-- Criar GUI ----------------------------------------------------

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "SubMundoGUI"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local botao = Instance.new("TextButton")
botao.Size = UDim2.new(0,150,0,50)
botao.Position = UDim2.new(0,20,0.8,0)
botao.BackgroundColor3 = Color3.fromRGB(0,0,0)
botao.TextColor3 = Color3.fromRGB(255,255,255)
botao.Font = Enum.Font.GothamBold
botao.Text = "SUB MUNDO"
botao.TextSize = 20
botao.Parent = ScreenGui

local voltar = Instance.new("TextButton")
voltar.Size = UDim2.new(0,150,0,50)
voltar.Position = UDim2.new(0,20,0.88,0)
voltar.BackgroundColor3 = Color3.fromRGB(0,0,0)
voltar.TextColor3 = Color3.fromRGB(255,255,255)
voltar.Font = Enum.Font.GothamBold
voltar.Text = "VOLTAR"
voltar.TextSize = 20
voltar.Visible = false
voltar.Parent = ScreenGui

-- Criar Submundo ----------------------------------------------------

local submundoFolder = Instance.new("Folder")
submundoFolder.Name = "SubMundoBlackTZ"
submundoFolder.Parent = workspace

-- Plataforma
local plataforma = Instance.new("Part")
plataforma.Size = Vector3.new(300, 2, 300)
plataforma.Position = Vector3.new(0, 5000, 0)
plataforma.Anchored = true
plataforma.Material = Enum.Material.Slate
plataforma.Color = Color3.fromRGB(40,40,40) -- NÃO FICA ESCURO DEMAIS
plataforma.Parent = submundoFolder

-- Luz ambiente no trono
local luzTrono = Instance.new("PointLight")
luzTrono.Brightness = 6
luzTrono.Range = 30
luzTrono.Color = Color3.fromRGB(150,0,150)

-- Trono ------------------------------------------------------------

local trono = Instance.new("Part")
trono.Size = Vector3.new(6,8,6)
trono.Position = plataforma.Position + Vector3.new(0,5,0)
trono.Anchored = true
trono.Color = Color3.fromRGB(20,20,20)
trono.Material = Enum.Material.Marble
trono.Parent = submundoFolder

luzTrono.Parent = trono

-- Nome no trono
local nameBill = Instance.new("BillboardGui")
nameBill.Size = UDim2.new(0,200,0,50)
nameBill.StudsOffset = Vector3.new(0,4,0)
nameBill.Adornee = trono
nameBill.Parent = trono

local texto = Instance.new("TextLabel")
texto.Size = UDim2.new(1,0,1,0)
texto.BackgroundTransparency = 1
texto.Text = "BLACKTZ"
texto.Font = Enum.Font.GothamBlack
texto.TextScaled = true
texto.TextColor3 = Color3.fromRGB(150,0,150)
texto.Parent = nameBill

-- Aura preta --------------------------------------------------------

local function adicionarAura(char)
	local hum = char:WaitForChild("HumanoidRootPart")
	
	local aura = Instance.new("ParticleEmitter")
	aura.Color = ColorSequence.new(Color3.new(0,0,0))
	aura.LightEmission = 0
	aura.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,1), NumberSequenceKeypoint.new(1,4)})
	aura.Texture = "rbxassetid://258128463" 
	aura.Rate = 30
	aura.Speed = NumberRange.new(0.5,1.5)
	aura.LockedToPart = false
	aura.Parent = hum
end

-- Raios caindo ------------------------------------------------------

task.spawn(function()
	while true do
		task.wait(math.random(3,7))

		local raio = Instance.new("Part")
		raio.Size = Vector3.new(1,40,1)
		raio.Anchored = true
		raio.CanCollide = false
		raio.Color = Color3.fromRGB(150,0,150)
		raio.Material = Enum.Material.Neon
		raio.Parent = submundoFolder

		local X = math.random(-120,120)
		local Z = math.random(-120,120)

		raio.Position = Vector3.new(X, plataforma.Position.Y + 40, Z)

		game:GetService("Debris"):AddItem(raio, 0.3)
	end
end)

-- Teleporte ---------------------------------------------------------

local function irSubmundo()
	local plr = game.Players.LocalPlayer
	if not plr.Character then return end

	adicionarAura(plr.Character)
	plr.Character:MoveTo(plataforma.Position + Vector3.new(0,4,0))

	botao.Visible = false
	voltar.Visible = true
end

local function voltarJogo()
	local plr = game.Players.LocalPlayer
	if not plr.Character then return end

	plr.Character:MoveTo(Vector3.new(0,5,0)) -- Posição inicial do mapa

	botao.Visible = true
	voltar.Visible = false
end

botao.MouseButton1Click:Connect(irSubmundo)
voltar.MouseButton1Click:Connect(voltarJogo)
