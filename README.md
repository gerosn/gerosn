local Mercury = loadstring(game:HttpGet("https://raw.githubusercontent.com/deeeity/mercury-lib/master/src.lua"))()

local GUI = Mercury:Create{
    Name = "flee the facility Internal v1.1",
    Size = UDim2.fromOffset(600, 400),
    Theme = Mercury.Themes.Dark,
    Link = "Best Flee the facility GUI"
}

GUI:Notification{
	Title = "Update:",
	Text = "Added Player Stuff WalkSpeed JumpPower Noclip FixCam, Fixed Lag on ESP and on others ,Add on discord for suggestions discord: bedra#0191",
	Duration = 5,
	Callback = function() end
}

GUI:Credit{
	Name = "bedra#0191",
	Description = "Made by",
	V3rm = "bedra45",
	Discord = "bedra#0191"
}

local Tab6 = GUI:Tab{
	Name = "Player Stuff",
	Icon = "rbxassetid://8569322835"
}

Tab6:Button{
	Name = "Respawn",
	Description = nil,
	Callback = function()
local plr = game.Players.LocalPlayer
plr.Character:Destroy()
	    end
}

Tab6:Button{
	Name = "FixCam",
	Description = nil,
	Callback = function()
local player = game.Players.LocalPlayer

	workspace.CurrentCamera.CameraSubject = player.Character:FindFirstChildWhichIsA('Humanoid')
	workspace.CurrentCamera.CameraType = "Custom"
	player.CameraMinZoomDistance = 0.5
	player.CameraMaxZoomDistance = math.huge
	player.CameraMode = "Classic"
	player.Character.Head.Anchored = false
	    end
}

Tab6:Slider{
	Name = "WalkSpeed",
	Default = 50,
	Min = 0,
	Max = 100,
	Callback = function(value)
	    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
	    end
}

Tab6:Slider{
	Name = "JumpPower",
	Default = 50,
	Min = 0,
	Max = 100,
	Callback = function(value)
	    game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
	    end
}

Tab6:Toggle{
	Name = "Noclip (Must Bypass Anti Cheat)",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
getgenv().NoclipLoop = game.RunService.Stepped:Connect(function()
    for i,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
        if v:IsA("BasePart") or v:IsA("Part") or v:IsA("MeshPart") then
            v.CanCollide = false
        end
    end
end)
else
getgenv().NoclipLoop:Disconnect()
end
end
}

Tab6:Toggle{
	Name = "HitBox",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
for i,v in pairs(game.Players:GetChildren()) do
if v:IsA("Player") and v.Name ~= game.Players.LocalPlayer.Name then
pcall(function()
v.Character.HumanoidRootPart.Size = Vector3.new(6.5,6.5,6.5)
v.Character.HumanoidRootPart.Transparency = 0.8
end)
end
end
else
for i,v in pairs(game.Players:GetChildren()) do
if v:IsA("Player") and v.Name ~= game.Players.LocalPlayer.Name then
pcall(function()
v.Character.HumanoidRootPart.Size = Vector3.new(2,2,1)
v.Character.HumanoidRootPart.Transparency = 1
end)
end
end
end
	    end
}

local Tab = GUI:Tab{
	Name = "Visuals",
	Icon = "rbxassetid://8569322835"
}

Tab:Toggle{
	Name = "Player ESP",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
	for i,v in pairs(game.Players:GetChildren()) do
		if v:IsA("Player") and v.Name ~= game.Players.LocalPlayer.Name then
			pcall(function()
				local transparency = 0.5
				local Folder = Instance.new("Folder",v.Character)
				Folder.Name = v.Name .. "'s ESP"
				--Head
				local Head = Instance.new("BoxHandleAdornment",Folder)
				Head.AlwaysOnTop = true
				Head.Adornee = v.Character.Head
				Head.ZIndex = 1
				Head.Name = "Head"
				Head.Transparency = transparency
				Head.Size = v.Character.Head.Size
				--Torso
				local Torso = Instance.new("BoxHandleAdornment",Folder)
				Torso.AlwaysOnTop = true
				Torso.Adornee = v.Character.Torso
				Torso.ZIndex = 1
				Torso.Name = "Torso"
				Torso.Transparency = transparency
				Torso.Size = v.Character.Torso.Size
				--Left Arm
				local LeftArm = Instance.new("BoxHandleAdornment",Folder)
				LeftArm.AlwaysOnTop = true
				LeftArm.Adornee = v.Character["Left Arm"]
				LeftArm.ZIndex = 1
				LeftArm.Name = "LeftArm"
				LeftArm.Transparency = transparency
				LeftArm.Size = v.Character["Left Arm"].Size
				--Right Arm
				local RightArm = Instance.new("BoxHandleAdornment",Folder)
				RightArm.AlwaysOnTop = true
				RightArm.Adornee = v.Character["Right Arm"]
				RightArm.ZIndex = 1
				RightArm.Name = "RightArm"
				RightArm.Transparency = transparency
				RightArm.Size = v.Character["Right Arm"].Size
				--Right Leg
				local RightLeg = Instance.new("BoxHandleAdornment",Folder)
				RightLeg.AlwaysOnTop = true
				RightLeg.Adornee = v.Character["Right Leg"]
				RightLeg.ZIndex = 1
				RightLeg.Name = "RightLeg"
				RightLeg.Transparency = transparency
				RightLeg.Size = v.Character["Right Leg"].Size
				--Left Leg
				local LeftLeg = Instance.new("BoxHandleAdornment",Folder)
				LeftLeg.AlwaysOnTop = true
				LeftLeg.Name = "LeftLeg"
				LeftLeg.Adornee = v.Character["Left Leg"]
				LeftLeg.ZIndex = 1
				LeftLeg.Transparency = transparency
				LeftLeg.Size = v.Character["Left Leg"].Size
				--Colors if beast or not
				getgenv().LoopBeastColor = game.RunService.Stepped:Connect(function()
				if v.TempPlayerStatsModule.IsBeast.Value == true then
					Head.Color3 = Color3.fromRGB(205, 98, 152)
					Torso.Color3 = Color3.fromRGB(205, 98, 152)
					LeftArm.Color3 = Color3.fromRGB(205, 98, 152)
					RightArm.Color3 = Color3.fromRGB(205, 98, 152)
					RightLeg.Color3 = Color3.fromRGB(205, 98, 152)
					LeftLeg.Color3 = Color3.fromRGB(205, 98, 152)
				elseif v.TempPlayerStatsModule.IsBeast.Value == false then
					Head.Color3 = Color3.new(225,1,1)
					Torso.Color3 = Color3.new(1,1,1)
					LeftArm.Color3 = Color3.new(1,1,1)
					RightArm.Color3 = Color3.new(1,1,1)
					RightLeg.Color3 = Color3.new(1,1,1)
					LeftLeg.Color3 = Color3.new(1,1,1)
				end
				end)
        --[[
        --BillboardGui
        local BillboardGui = Instance.new("BillboardGui",Folder)
        BillboardGui.AlwaysOnTop = true
        BillboardGui.Enabled = true
        BillboardGui.Adornee = v.Character.Head
        BillboardGui.Size = UDim2.new(0,100,0,100)
        --NameTag
        local NameTag = Instance.new("TextLabel",BillboardGui)
        NameTag.BackgroundTransparency = 1
        NameTag.Size = UDim2.new(0,100,0,10)
        if v.TempPlayerStatsModule.IsBeast.Value == true then
        NameTag.TextColor3 = Color3.new(1,0,0)
        elseif v.TempPlayerStatsModule.IsBeast.Value == false then
        NameTag.TextColor3 = Color3.new(1,1,1)
        end
        NameTag.ZIndex = 10
        NameTag.Visible = true
        NameTag.TextSize = 20
        NameTag.Text = "Name: " .. v.Name
        ]]
			end)
		end
	end
else
getgenv().LoopBeastColor:Disconnect()
for i,v in pairs(game.Players:GetChildren()) do
    if v:IsA("Player") then
   for i,e in pairs(v.Character:GetChildren()) do
   if e:IsA("Folder") then
       pcall(function()
       e:Destroy()
       end)
end
end
end
end

end
end
}

Tab:Toggle{
	Name = "Door ESP",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
getgenv().DoorESP = false
	spawn(function()
		--single doors
		for i,v in pairs(workspace:GetDescendants()) do
			if v.Name == "SingleDoor" then
				pcall(function()
					local ESP = Instance.new("Highlight")
					ESP.Parent = v.Door
				end)

			end
		end
		wait(1)

		for i,v in pairs(workspace:GetDescendants()) do
			if v.Name == "SingleDoor" then
				spawn(function()
					while true do
						pcall(function()
							if v.DoorTrigger.ActionSign.Value == 11 then
								v.Door.Highlight.FillColor = Color3.new(0,1,0)
							elseif v.DoorTrigger.ActionSign.Value == 10 then
								v.Door.Highlight.FillColor = Color3.new(1,0,0)
							end
						end)
						if getgenv().DoorESP == true then
						    break;
						end
						wait(0.1)
					end
				end)
				
				
			end
		end
		
	end)
	--double doors
	spawn(function()
		for i,v in pairs(workspace:GetDescendants()) do
			if v.Name == "DoubleDoor" then
				pcall(function()
					local ESP = Instance.new("Highlight")
					ESP.Parent = v
				end)

			end
		end
		wait(1)

		for i,v in pairs(workspace:GetDescendants()) do
			if v.Name == "DoubleDoor" then
				spawn(function()
					while true do
						pcall(function()
							if v.DoorTrigger.ActionSign.Value == 11 then
								v.Highlight.FillColor = Color3.new(0,1,0)
							elseif v.DoorTrigger.ActionSign.Value == 10 then
								v.Highlight.FillColor = Color3.new(1,0,0)
							end
						end)
                        if getgenv().DoorESP == true then
                             print("Stopped itLop!2")
                             break;
                        end
                        wait(0.1)
					end
				end)
			end
		end
	end)
else
getgenv().DoorESP = true
	--signle door
	for i,v in pairs(workspace:GetDescendants()) do
		if v.Name == "SingleDoor" then
			pcall(function()
				v.Door.Highlight:Destroy()
			end)

		end
	end

	--double doors
	for i,v in pairs(workspace:GetDescendants()) do
		if v.Name == "DoubleDoor" then
			pcall(function()
				v.Highlight:Destroy()
			end)

		end
	end
end
    end
}

Tab:Toggle{
	Name = "Computer ESP",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
getgenv().StopComputerESP = false
for i,v in pairs(workspace:GetDescendants()) do 
    if v.Name == "ComputerTable" then
        pcall(function()
        local ESP = Instance.new("Highlight",v)
        end)
    end
end

spawn(function()
while true do
for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "ComputerTable" then
        if v.Screen.BrickColor == BrickColor.new("Bright blue") then
            pcall(function()
          v.Highlight.FillColor = Color3.new(0,0,1)
            end)
        elseif v.Screen.BrickColor == BrickColor.new("Dark green") then
            pcall(function()
          v.Highlight.FillColor = Color3.new(0,1,0)
            end)
        end
        if getgenv().StopComputerESP == true then
          print("Stopped itLop!PC")
          break;
        end
    end
end
wait(1)
end
end)
else
getgenv().StopComputerESP = true
for i,v in pairs(workspace:GetDescendants()) do 
    if v.Name == "ComputerTable" then
        pcall(function()
        v.Highlight:Destroy()
        end)
    end
end
end
	    end
}

Tab:Toggle{
	Name = "FreezePod ESP",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
for i,v in pairs(workspace:GetDescendants()) do 
    if v.Name == "FreezePod" then
        pcall(function()
        local ESP = Instance.new("Highlight",v)
        end)
    end
end
else
for i,v in pairs(workspace:GetDescendants()) do 
    if v.Name == "FreezePod" then
        pcall(function()
        v.Highlight:Destroy()
        end)
    end
end
end
	    end
}



local Tab2 = GUI:Tab{
	Name = "Beast",
	Icon = "rbxassetid://8569322835"
}
Tab2:Button{
	Name = "Inf Stamina",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
game.UserInputService.InputBegan:Connect(function(key)
if key.KeyCode == Enum.KeyCode.Q then
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 30
end
end)

game.UserInputService.InputEnded:Connect(function(key)
if key.KeyCode == Enum.KeyCode.Q then
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
end
end)

pcall(function()
game.Players.LocalPlayer.Character.PowersLocalScript:Destroy()    
end)
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast >:((",
	Duration = 5,
	Callback = function() end
}
end
	    end
}

Tab2:Button{
	Name = "No Slow",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
pcall(function()
game.Players.LocalPlayer.Character.PowersLocalScript:Destroy()
end)
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast >:((",
	Duration = 5,
	Callback = function() end
}
end
	end
}

Tab2:Button{
	Name = "Enable Crawl",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
game:GetService("Players").LocalPlayer.TempPlayerStatsModule.DisableCrawl.Value = false
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast >:((",
	Duration = 5,
	Callback = function() end
}
end
	end
}

Tab2:Button{
	Name = "Remove Sounds and Glow",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
for i,v in pairs(game.Players.LocalPlayer.Character.Hammer.Handle:GetChildren()) do
    if v:IsA("Sound") then
        pcall(function()
        v:Destroy()
        end)
    end
end

pcall(function()
game.Players.LocalPlayer.Character.Gemstone.Handle.PointLight:Destroy()
end)
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast >:((",
	Duration = 5,
	Callback = function() end
}
end
end
}

Tab2:Button{
	Name = "Bug Game Forever",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
game.Players.LocalPlayer.Character:Destroy()
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast >:((",
	Duration = 5,
	Callback = function() end
}
end
	end
}

Tab2:Toggle{
	Name = "Auto tie",
	StartingState = false,
	Description = nil,
	Callback = function(state)
if state == true then
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
getgenv().StopTheShit = false
while wait() do
if game:GetService("Players").LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
local Players = game:GetService("Players")
local lp = Players.LocalPlayer

local function GetClosestPlayer()
   local target = nil
   local distance = math.huge
 
   for i,v in next, Players:GetPlayers() do
       if v and v ~= lp and v.Character and v.Character:FindFirstChildOfClass('Humanoid') and v.Character:FindFirstChildOfClass('Humanoid').RootPart then
           local plrdist = lp:DistanceFromCharacter(v.Character:FindFirstChildOfClass('Humanoid').RootPart.CFrame.p)
           if plrdist < distance then
               target = v
               distance = plrdist
           end
       end
   end
 
   return target
end

print(GetClosestPlayer().Name)
local args = {
    [1] = "HammerTieUp",
    [2] = GetClosestPlayer().Character.Torso,
    [3] = GetClosestPlayer().Character.HumanoidRootPart.Position
}

game:GetService("Players").LocalPlayer.Character.Hammer.HammerEvent:FireServer(unpack(args))
end
if getgenv().StopTheShit == true then
    break;
end
end
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not the beast>:(",
	Duration = 3,
	Callback = function() end
}
end
else
getgenv().StopTheShit = true
end
	    end
}

local Tab3 = GUI:Tab{
	Name = "Non Beast",
	Icon = "rbxassetid://8569322835"
}
Tab3:Button{
	Name = "Q to sprint forever",
	Description = nil,
	Callback = function()
game.UserInputService.InputBegan:Connect(function(key)
if key.KeyCode == Enum.KeyCode.Q then
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 30
end
end)

game.UserInputService.InputEnded:Connect(function(key)
if key.KeyCode == Enum.KeyCode.Q then
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
end
end)

pcall(function()
game.Players.LocalPlayer.Character.PowersLocalScript:Destroy()    
end)
	    end
}

Tab3:Button{
	Name = "No error on hack",
	Description = nil,
	Callback = function()
spawn(function()
while wait() do
game.ReplicatedStorage.RemoteEvent:FireServer("SetPlayerMinigameResult",true)
end
end)
	    end
}

local Tab4 = GUI:Tab{
	Name = "Tp to pcs",
	Icon = "rbxassetid://8569322835"
}


Tab4:Button{
	Name = "Bypass Anti Cheat (dont if beast)",
	Description = nil,
	Callback = function()
if game.Players.LocalPlayer.TempPlayerStatsModule.IsBeast.Value == true then
GUI:Notification{
	Title = "Alert!",
	Text = "Your the beast dont bypass anti cheat if ur the beast>:((",
	Duration = 3,
	Callback = function() end
}
else
local character = game.Players.LocalPlayer.Character
    local torso = character:FindFirstChild("Torso") or character:FindFirstChild("UpperTorso")
    local root = character:FindFirstChild("HumanoidRootPart")
    local head = character:FindFirstChild("Head")
    character.Parent = nil
    root.Parent = nil 
    wait(0.5)
    local fake = torso:Clone()
    fake.Parent = character
    torso.Name = "HumanoidRootPart"
    torso.Transparency = 1
    getgenv().Torsoo = torso
    character.Parent = workspace
    end
	    end
}

local MyDropdown = Tab4:Dropdown{
	Name = "Pcs (Must bypass anti cheat)",
	StartingText = "Select...",
	Description = nil,
	Items = {
		{"Pc1",1}, 		-- {name, value}
		{"Pc2",2},
		{"Pc3",3},
		{"Pc4",4},
		{"Pc5",5},-- or just value, which is also automatically taken as name
		{"Pc6",6}
	},
	Callback = function(item)
if item == 1 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable1.ComputerTrigger3.CFrame
    end
end
elseif item == 2 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable2.ComputerTrigger3.CFrame
    end
end
elseif item == 3 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable3.ComputerTrigger3.CFrame
    end
end
elseif item == 4 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable4.ComputerTrigger3.CFrame
    end
end
elseif item == 5 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable5.ComputerTrigger3.CFrame
    end
end
elseif item == 6 then
    for i,v in pairs(workspace:GetDescendants()) do
    if v.Name == "FreezePod" then
        local map = v.Parent
        pcall(function()
        map.ComputerTable.Name = "ComputerTable1"
        map.ComputerTable.Name = "ComputerTable2"
        map.ComputerTable.Name = "ComputerTable3"
        map.ComputerTable.Name = "ComputerTable4"
        map.ComputerTable.Name = "ComputerTable5"
        map.ComputerTable.Name = "ComputerTable6"
        end)
        
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = map.ComputerTable6.ComputerTrigger3.CFrame
    end
end
end
return
end
}

Tab4:Button{
	Name = "Visible and Invisible (Must bypass anti cheat Keybind: f)",
	Description = nil,
	Callback = function()
local Global = getgenv and getgenv()
local First = true
local Restart = true
local SoundService = game:GetService("SoundService")
local StoredCF
local SafeZone
if Global.SafeZone ~= nil then
	if type(Global.SafeZone) ~= "userdata" then return error("CFrame must be a userdata (CFrame.new(X, X, X)") end
	SafeZone = Global.SafeZone
else
	SafeZone = CFrame.new(0,-300,0)       
end

local ScriptStart = true
local Reset = false
local DeleteOnDeath = {}
local Activate
local Noclip
if Global.Key == nil then
	Activate = "F"
else
	Activate = tostring(Global.Key)     
end

if Global.Noclip == nil then
	Noclip = false
else
	Noclip = Global.Noclip        
end

if type(Noclip) ~= "boolean" then return error("Noclip value isn't a boolean") end

function notify(Message)
	game:GetService("StarterGui"):SetCore("SendNotification", { 
		Title = "FE Invisible";
		Text = Message;
		Icon = "rbxthumb://type=Asset&id=5107182114&w=150&h=150"})
	local sound = Instance.new("Sound")
	sound.SoundId = "rbxassetid://7046168694"
	SoundService:PlayLocalSound(sound)
end

if Global.Running then
	return notify("Script is already running")
else
	Global.Running = true
end

local IsInvisible = false
local WasInvisible = false
local Died = false
local LP = game:GetService("Players").LocalPlayer
local UserInputService = game:GetService("UserInputService")
repeat wait() until LP.Character
repeat wait() until LP.Character:FindFirstChild("Humanoid")
local RealChar = LP.Character or LP.CharacterAdded:Wait()
RealChar.Archivable = true
local FakeChar = RealChar:Clone()
FakeChar:WaitForChild("Humanoid").DisplayDistanceType = Enum.HumanoidDisplayDistanceType.None
FakeChar.Parent = game:GetService("Workspace")

for _, child in pairs(FakeChar:GetDescendants()) do
	if child:IsA("BasePart") and child.CanCollide == true then
		child.CanCollide = false
	end
end

FakeChar:SetPrimaryPartCFrame(SafeZone * CFrame.new(0, 5, 0))

local Part
Part = Instance.new("Part", workspace)
Part.Anchored = true
Part.Size = Vector3.new(200, 1, 200)
Part.CFrame = SafeZone
Part.CanCollide = true


for i, v in pairs(FakeChar:GetDescendants()) do
	if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
		v.Transparency = 0.7
	end
end

for i, v in pairs(RealChar:GetChildren()) do
	if v:IsA("LocalScript") then
		local clone = v:Clone()
		clone.Disabled = true
		clone.Parent = FakeChar
	end
end

function StopScript()
	if ScriptStart == false then return end
	if Died == false then
		if Restart == true then
			notify("The character used died!\nStopping...")
		else
			notify("Script successfuly ended !")
		end
		Part:Destroy()
		if IsInvisible and RealChar:FindFirstChild("HumanoidRootPart") then
			Visible() 
			WasInvisible = true
		end
		
		if IsInvisible == false and LP.Character:WaitForChild("Humanoid").Health == 0 then
			WasInvisible = true
		end
		if not RealChar:FindFirstChild("Humanoid") then
			Reset = true
			print("a")
		end
		
		game:GetService("Workspace").CurrentCamera.CameraSubject = RealChar:WaitForChild("Humanoid")

		if FakeChar then
			FakeChar:Destroy()
		end

		if WasInvisible then
			local char = LP.Character
			if char:FindFirstChildOfClass("Humanoid") then char:FindFirstChildOfClass("Humanoid"):ChangeState(15) end
			char:ClearAllChildren()
			local newChar = Instance.new("Model")
			newChar.Parent = workspace
			LP.Character = newChar
			wait()
			LP.Character = char
			newChar:Destroy()
			for _,v in pairs(DeleteOnDeath) do
				v:Destroy()
			end
			
		else
			for _,v in pairs(DeleteOnDeath) do
				v.ResetOnSpawn = true
			end
		end
		Global.Running = false
		ScriptStart = false
		if Restart == true then
		loadstring(game:HttpGet('https://raw.githubusercontent.com/Error-Cezar/Roblox-Scripts/main/FE-Invisible.lua'))()
		end
		
			LP.CharacterAdded:Connect(function()
				if Reset == false then return end
			loadstring(game:HttpGet('https://raw.githubusercontent.com/Error-Cezar/Roblox-Scripts/main/FE-Invisible.lua'))()
		end)
		
	end
end

RealChar:WaitForChild("Humanoid").Died:Connect(function()
	StopScript()
end)


FakeChar:WaitForChild("Humanoid").Died:Connect(function()
	StopScript()
end)

function Invisible()
	StoredCF = RealChar:GetPrimaryPartCFrame()
	
if First == true then
		First = false
		for _,v in pairs(LP:WaitForChild("PlayerGui"):GetChildren()) do 
		if v:IsA("ScreenGui") then
			if v.ResetOnSpawn == true then
				v.ResetOnSpawn = false
				table.insert(DeleteOnDeath, v)
			end
		end
	end
	end
	
	if Noclip == true then
	for _, child in pairs(FakeChar:GetDescendants()) do
		if child:IsA("BasePart") and child.CanCollide == true then
			child.CanCollide = false
		end
		end
	end
	FakeChar:SetPrimaryPartCFrame(StoredCF)
	FakeChar:WaitForChild("HumanoidRootPart").Anchored = false
	LP.Character = FakeChar
	game:GetService("Workspace").CurrentCamera.CameraSubject = FakeChar:WaitForChild("Humanoid")
		for _, child in pairs(RealChar:GetDescendants()) do
			if child:IsA("BasePart") and child.CanCollide == true then
				child.CanCollide = false
			end
		end

	RealChar:SetPrimaryPartCFrame(SafeZone * CFrame.new(0, 5, 0))
	--	RealChar:WaitForChild("HumanoidRootPart").Anchored = true
	RealChar:WaitForChild("Humanoid"):UnequipTools()

	for i, v in pairs(FakeChar:GetChildren()) do
		if v:IsA("LocalScript") then
			v.Disabled = false
		end
	end
end

function Visible()
	StoredCF = FakeChar:GetPrimaryPartCFrame()
	for _, child in pairs(RealChar:GetDescendants()) do
		if child:IsA("BasePart") and child.CanCollide == true then
			child.CanCollide = true
		end
	end
	RealChar:WaitForChild("HumanoidRootPart").Anchored = false
	RealChar:SetPrimaryPartCFrame(StoredCF)
	LP.Character = RealChar
	FakeChar:WaitForChild("Humanoid"):UnequipTools()
	game:GetService("Workspace").CurrentCamera.CameraSubject = RealChar:WaitForChild("Humanoid")
	for _, child in pairs(FakeChar:GetDescendants()) do
		if child:IsA("BasePart") and child.CanCollide == true then
			child.CanCollide = false
		end
	end
	FakeChar:SetPrimaryPartCFrame(SafeZone * CFrame.new(0, 5, 0))
		FakeChar:WaitForChild("HumanoidRootPart").Anchored = true
	for i, v in pairs(FakeChar:GetChildren()) do
		if v:IsA("LocalScript") then
			v.Disabled = true
		end
	end
end


UserInputService.InputBegan:Connect(function(input, gameProcessed)
	if ScriptStart == false then return end
	if gameProcessed then return end
	if input.KeyCode.Name:lower() ~= Activate:lower() then return end
	if IsInvisible == false then
		Invisible()
		IsInvisible = true
	else
		Visible()
		IsInvisible = false
	end
end)
	    end
}


local Tab5 = GUI:Tab{
	Name = "Misc",
	Icon = "rbxassetid://8569322835"
}

Tab5:Button{
	Name = "Close trade GUI",
	Description = nil,
	Callback = function()
if game.PlaceId == 1738581510 then
	    game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.TradingMenuWindow.Visible = false

GUI:Notification{
	Title = "Alert!",
	Text = "Visual scam wont work if u close the gui while doing the visual scam.",
	Duration = 5,
	Callback = function() end
}
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not in the trading server Join it!! >:(",
	Duration = 3,
	Callback = function() end
}
end
	    end
}

Tab5:Button{
	Name = "Visual Scam",
	Description = nil,
	Callback = function()
if game.PlaceId == 1738581510 then
wait(0)
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.TradingMenuWindow.Visible = true
else
GUI:Notification{
	Title = "Alert!",
	Text = "Your not in the trading server Join it!! >:(",
	Duration = 3,
	Callback = function() end
}
end
	    end
}

Tab5:Button{
	Name = "Inf Credits (Only works on Bundles)",
	Description = nil,
	Callback = function()
	    print("This only works on bundles")
while wait() do
game:GetService("Players").LocalPlayer.SavedPlayerStatsModule.Credits.Value = 10000000000
end
	    end
}

local MyDropdown = Tab5:Dropdown{
	Name = "Buy unavailable bundles (go to shop to buy it)",
	StartingText = "Select...",
	Description = nil,
	Items = {
		{"2ndAniversaryBundle (Rarest)",1},
		{"AnniversaryClassicBundle",2},	
		{"SpookySweetsBundle",3}
	},
	Callback = function(item)
if item == 1 then
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.LocalScript.Enabled = true
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.Visible = true

local hi = require(game:GetService("ReplicatedStorage").DeveloperProductIds);

hi["RedNutcrackerBundle"] = 592709755
elseif item == 2 then
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.LocalScript.Enabled = true
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.Visible = true

local hi = require(game:GetService("ReplicatedStorage").DeveloperProductIds);

hi["RedNutcrackerBundle"] = 307455363
elseif item == 3 then
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.LocalScript.Enabled = true
game:GetService("Players").LocalPlayer.PlayerGui.MenusScreenGui.ShopMenuWindow.Body.SideBarTabsFrame.BuyBundleButton2.Visible = true

local hi = require(game:GetService("ReplicatedStorage").DeveloperProductIds);

hi["RedNutcrackerBundle"] = 1111394671
end
	    return
	    end
}
