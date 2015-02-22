Colors = {"Really red", "Really blue", "Lime green", "Hot pink", "Bright red", "Bright blue", "New yeller", "Institutional white", "White", "Pink", "Bright green", "Toothpaste", "Teal"}

local plr = game.Players.LocalPlayer
local chr = plr.Character
local trso = chr.Torso

game:service'RunService'.Heartbeat:connect(function()
	trail = Instance.new("Part", trso)
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
