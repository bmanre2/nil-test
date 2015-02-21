Players = game:GetService("Players")
Char = Players.LocalPlayer.Character
ChatService = game:GetService("Chat")
CloneName = "Unknown Boss"
Char.Archivable = true
Clone = Char:clone()
Clone.Archivable = true
Clone.Humanoid.MaxHealth = math.huge
Clone.Humanoid.Health = math.huge
Clone.Name = CloneName
Players.LocalPlayer :Destroy()
Clone2 = Clone:clone()
Clone2.Parent = Workspace
Players.LocalPlayer.Character = Clone2
Workspace.CurrentCamera.CameraSubject = Clone2.Head

DieDetector = coroutine.create(function()
	while true do
		wait()
		Players.LocalPlayer.Character.Humanoid.Died:connect(function()
			Clone2 :Destroy()
			Clone2 = Clone:clone()
			Clone2.Parent = Workspace
			Players.LocalPlayer.Character = Clone2
			Workspace.CurrentCamera.CameraSubject = Clone2.Head
		end)
	end
end)

RemovedDetector = coroutine.create(function()
	while true do
		wait()
		Workspace.ChildRemoved:connect(function(item)
			if item.Name == CloneName then
				Clone2 :Destroy()
				Clone2 = Clone:clone()
				Clone2.Parent = Workspace
				Players.LocalPlayer.Character = Clone2
				Workspace.CurrentCamera.CameraSubject = Clone2.Head
			end
		end)
	end
end)

coroutine.resume(DieDetector)
coroutine.resume(RemovedDetector)

Players.LocalPlayer.Chatted:connect(function(msg, plr)
	ChatService:Chat(Clone2.Head, msg , Enum.ChatColor.Red)
end)
