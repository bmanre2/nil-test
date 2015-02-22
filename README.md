orbp1 = Instance.new("Part",game.Players.LocalPlayer.Character.Torso)
torso = orbp1
orbp1.Size = Vector3.new(1.5,1.5,1.5)
orbp1.Name = "orbp1"
orbp1.Locked = true
orbp1.CanCollide = true
orbp1.Shape = "Ball"
local mes = Instance.new("SpecialMesh",orbp1)
mes.MeshId = "http://www.roblox.com/asset/?id=1185246"
mes.TextureId = "http://www.roblox.com/asset/?id=1193831"
mes.Scale = Vector3.new(1.5,1.5,1.5)

brick = game.Players.LocalPlayer.Character.Torso
orbittingbrick = orbp1
orbittingbrick.Anchored = true
orbittingbrick.CanCollide = true
distancefrombrick = 5

while true do 
for i = 0,360 do
wait()
orbittingbrick.CFrame = CFrame.new(brick.Position) * CFrame.Angles(0,math.rad(i),0) * CFrame.new(0,0,-distancefrombrick)
end
end

Colors = {"Really red", "Really blue", "Lime green", "Hot pink", "Bright red", "Bright blue", "New yeller", "Institutional white", "White", "Pink", "Bright green", "Toothpaste", "Teal"}

game:service'RunService'.Heartbeat:connect(function()
	trail = Instance.new("Part", orbp1)
	game.Debris:AddItem(trail, 2)
	trail.FormFactor = "Custom"
	trail.Size = Vector3.new(2,2,2)
	trail.CanCollide = false
	trail.Transparency = 0
	trail.CFrame = trso.CFrame
	trail.TopSurface = 0
	trail.BottomSurface=0
	local c = math.random(1, #Colors)
	trail.BrickColor = BrickColor.new(Colors[c])
	trail.Anchored = true
	trail.Transparency = 0.2
	local blockmesh = Instance.new("BlockMesh", trail)
	blockmesh.Scale = Vector3.new(1,1,1)
	wait()
	for i = 1, 9 do
		blockmesh.Scale = Vector3.new(blockmesh.Scale.x - 0.1, blockmesh.Scale.y - 0.1, blockmesh.Scale.z - 0.1)
		wait(0.0000001)
	end
	for i = 1, 10 do
	blockmesh.Scale = Vector3.new(blockmesh.Scale.x - 0.01, blockmesh.Scale.y - 0.01, blockmesh.Scale.z - 0.01)
	wait(0.0000007)
	end

end)
