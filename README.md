Move1 = "Blaster Meteor"
Move2 = "Sudden Storm"
Move3 = "Chain Destructo Disk"
Move4 = "Spirit Ball"
Move5 = "Crusher Ball"
Move6 = "Flash Skewer"
Move7 = "Super Volley"
Move8 = "Big Bang Kamehameha"
Move9 = "Demon Flash"

if game.PlaceId == 536102540 then game:GetService("TeleportService"):Teleport(3565304751) end

function Twn(HRP,Place,Length)
    local Twn = game:GetService("TweenService"):Create(HRP,
    TweenInfo.new(Length,Enum.EasingStyle.Quad,Enum.EasingDirection.InOut),{CFrame = Place})
    Twn:Play()
    Twn.Completed:Wait()
end
local Live = game:WaitForChild("Workspace").Live
local Char = Live:WaitForChild(game.Players.LocalPlayer.Name)
if game.PlaceId == 3565304751 then
	game:GetService("StarterGui"):SetCore("SendNotification", {
		Title = "AutoBroly Premium";
		Text = "by Jeiser";
	})
	local Bounce = false
	Twn(Char.HumanoidRootPart,CFrame.new(-2500, 238, -85),1)
	wait(1)
	Char.LowerTorso:Destroy()
	local TeleBounce = false
	local CollideBounce = false
	local CollideBounce2 = false
	function FindPad(Time)
		for i,v in pairs(game.Workspace:GetChildren()) do
			if v.Name:find("BrolyTeleport") and v:FindFirstChild("15") then
				if TeleBounce == false then 
					TeleBounce = true
					Twn(Char.HumanoidRootPart,v.PrimaryPart.CFrame + Vector3.new(0,3,0),1)
					TeleBounce = false
					break
				end
			end
		end
	end 
	for i,v in pairs(Char:GetChildren()) do if v.Name:find("Lvl") then v:Destroy() end end
		FindPad(3)
		Char.HumanoidRootPart.Size = Vector3.new(25,2,50)
		Char.HumanoidRootPart.CanCollide = false
		Char.HumanoidRootPart.Touched:Connect(function(Collide)
		if Collide.Parent:FindFirstChild("Humanoid") and Collide.Parent:FindFirstChild("HumanoidRootPart") then
			if Collide.Parent.Name == game.Players.LocalPlayer.Name then 
			else
				if CollideBounce == true then
					FindPad(.6)
				end 
				if CollideBounce2 == false then
					CollideBounce2 = true
					CollideBounce = false
					wait(1)
					CollideBounce = true
					wait(1)
					CollideBounce = false
					CollideBounce2 = false
				end
			end
		end
	end)
	wait(45)
	game:GetService("TeleportService"):Teleport(536102540)
elseif game.PlaceId == 2050207304 then
	wait(1)
	local B = Live:WaitForChild("Broly BR")
	if game.Players.NumPlayers > 1 then game:GetService("TeleportService"):Teleport(3565304751) end	
	if Char.Race.Value == "Android" then game.Players.LocalPlayer.Backpack.ServerTraits.Transform:FireServer("g") 
	else
		game.Players.LocalPlayer.Backpack.ServerTraits.Input:FireServer({[1] = "x"},CFrame.new(0,0,0),InputObject)
		wait(4)
		game.Players.LocalPlayer.Backpack.ServerTraits.Transform:FireServer("h")
		wait(2)
		game.Players.LocalPlayer.Backpack.ServerTraits.Input:FireServer({[1] = "xoff"},CFrame.new(0,0,0),InputObject)		
	end
	Twn(Char.HumanoidRootPart,B.HumanoidRootPart.CFrame,1)
	Char.HumanoidRootPart.Anchored = false
	game:GetService("RunService").RenderStepped:connect(function()
		Char.Humanoid:ChangeState(11)
		game.Workspace.CurrentCamera.CFrame = CFrame.new(Char.HumanoidRootPart.Position,B.HumanoidRootPart.Position) * CFrame.new(0,2,10)
		if Char:FindFirstChild("Attacking") then Char.Attacking:Destroy() end
		if Char:FindFirstChild("Action") then Char.Action:Destroy() end
		if Char:FindFirstChild("Slow") then Char.Slow:Destroy() end
		if Char:FindFirstChild("Using") then Char.Using:Destroy() end
		if Char:FindFirstChild("MoveStart") then Char.MoveStart:Destroy() end
		if Char.Humanoid.Health < 1.5 then game:GetService("TeleportService"):Teleport(3565304751) end
		game.Players.LocalPlayer.Backpack.ServerTraits.EatSenzu:FireServer("Reds")
		if Char.Humanoid.Health < 50 then game.Players.LocalPlayer.Backpack.ServerTraits.Transform:FireServer("h") end
		Char.HumanoidRootPart.CFrame = B.HumanoidRootPart.CFrame + B.HumanoidRootPart.CFrame.lookVector * -6
	end)
	wait(1)
	repeat game:GetService("RunService").RenderStepped:Wait()
		if Char.Ki.Value > Char.Ki.MaxValue/20 then 
			for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do 
				if v.Name == Move1 or v.Name == Move2 or v.Name == Move3 or v.Name == Move4 or v.Name == Move5 or v.Name == Move6 or v.Name == Move7 or v.Name == Move8 or v.Name == Move9 then
					v.Parent = game:GetService("Workspace").Live[game.Players.LocalPlayer.Name]
					wait()
					v:Activate() 
					v:Deactivate() 
					v.Parent = game.Players.LocalPlayer.Backpack 
				end 
			end
		elseif Char.Ki.Value < Char.Ki.MaxValue/20 then
			game.Players.LocalPlayer.Backpack.ServerTraits.Input:FireServer({[1] = "m2"},CFrame.new(0,0,0),nil,false)
		end
	until B.Humanoid.Health < .1
	game:GetService("TeleportService"):Teleport(3565304751)
end
