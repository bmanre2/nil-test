Position = {} --For the function if you die you can go back to your position instead of going back to the middle of the baseplate.
Player = Game.Players.LocalPlayer
Char = Player.Character
Char.Archivable = true
NilChar = Char:Clone()
pcall(function() NilChar.Animate:Destroy() end)
Player:Destroy()
function LoadNil()
	Animation = Game:GetService("InsertService"):LoadAsset(68452456):GetChildren()[1]:findFirstChild("Animate")
	Clone = NilChar:Clone()
	table.insert(Position,NilChar.Torso.CFrame)
	Clone.Parent = Workspace
	Clone:MakeJoints()
	Player.Character = Clone
	Player = Clone
	Workspace.Camera.CameraSubject = Clone["Humanoid"]
	Workspace.Camera.CameraType = "Custom"
	Clone.Torso.CFrame = Position[#Position]
	Animation.Parent = Clone
	Workspace.Changed:connect(function()
		if Workspace:findFirstChild(Player.Name) == nil then
			LoadNil()
			Clone.Parent = Workspace
		end
	end)
	Game.Players.LocalPlayer.Chatted:connect(function(msg)
		Game:GetService("Chat"):Chat(Clone.Head, msg, Red)
	end)
	Clone.Humanoid.Changed:connect(function()
		Clone.Humanoid.Health = 100
	end)
end
LoadNil()
Clone.Parent = Workspace
--[[
	Position = {} --For the function if you die you can go back to your position instead of going back to the middle of the baseplate.
Player = Game.Players.LocalPlayer
Char = Player.Character
Char.Archivable = true
NilChar = Char:Clone()
NilChar.Parent = Game:GetService("Geometry")
Char.Animate:Destroy()
Player:remove()
function LoadNil()
	WorkingAround = Game:GetService("InsertService"):LoadAsset(68452456):children()[1]
	WorkingAround.Parent = Game.Lighting
	Clone = NilChar:Clone()
	table.insert(Position,Clone.Torso.CFrame)
	Clone.Parent = Workspace
	Clone:MakeJoints()
	Player.Character = Clone
	Workspace.Camera.CameraSubject = Clone["Humanoid"]
	Workspace.Camera.CameraType = "Custom"
	Clone:findFirstChild("Animate"):Destroy()
	Clone.Torso.CFrame = Position[#Position]
	Anim = WorkingAround.Animate:Clone()
	Anim.Parent = Clone
	Clone.Humanoid.Changed:connect(function()
		Clone.Humanoid.Health = 100
	Game:GetService("Players").LocalPlayer.Chatted:connect(function(msg) --Thanks terminal *from the orb script. c:
		Game:GetServic
--]]
