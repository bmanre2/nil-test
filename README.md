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


game:service'RunService'.Heartbeat:connect(function()
torso = workspace.Basictality.Torso.orbp1
while wait() do p=Instance.new("Part",workspace) p.FormFactor = "Custom" p.Color = Color3.new(0,0,0) p.Size = Vector3.new(0.1,0.1,0.1)p.CFrame=torso.CFrame*CFrame.new(0.5,0,0) p.Transparency = 0.5 p.Anchored=true game.Debris:AddItem(p,1) end
end)
