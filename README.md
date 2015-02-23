wait() 
z=Instance.new("Tool",game.Players.LocalPlayer.Backpack)
tool = z
lineconnect = tool.LineConnect
object = nil
mousedown = false
found = false
BP = Instance.new("BodyPosition")
BP.maxForce = Vector3.new(math.huge*math.huge,math.huge*math.huge,math.huge*math.huge) --pwns everyone elses bodyposition
BP.P = BP.P*8 --faster movement. less bounceback.
dist = nil
point = Instance.new("Part")
point.Locked = true
point.Anchored = true
point.formFactor = 0
point.Shape = 0
point.BrickColor = BrickColor.Black() 
point.Size = Vector3.new(1,1,1)
point.CanCollide = false
local mesh = Instance.new("SpecialMesh")
mesh.MeshType = "Sphere"
mesh.Scale = Vector3.new(.7,.7,.7)
mesh.Parent = point
handle = tool.Handle
front = tool.Handle
color = tool.Handle
objval = nil
local hooked = false 
local hookBP = BP:clone() 
hookBP.maxForce = Vector3.new(30000,30000,30000) 

function LineConnect(part1,part2,parent)
	local p1 = Instance.new("ObjectValue")
	p1.Value = part1
	p1.Name = "Part1"
	local p2 = Instance.new("ObjectValue")
	p2.Value = part2
	p2.Name = "Part2"
	local par = Instance.new("ObjectValue")
	par.Value = parent
	par.Name = "Par"
	local col = Instance.new("ObjectValue")
	col.Value = color
	col.Name = "Color"
	local s = lineconnect:clone()
	s.Disabled = false
	p1.Parent = s
	p2.Parent = s
	par.Parent = s
	col.Parent = s
	s.Parent = workspace
	if (part2==object) then
		objval = p2
	end
end

function onButton1Down(mouse)
	if (mousedown==true) then return end
	mousedown = true
	coroutine.resume(coroutine.create(function()
		local p = point:clone()
		p.Parent = tool
		LineConnect(front,p,workspace)
		while (mousedown==true) do
			p.Parent = tool
			if (object==nil) then
				if (mouse.Target==nil) then
					local lv = CFrame.new(front.Position,mouse.Hit.p)
					p.CFrame = CFrame.new(front.Position+(lv.lookVector*1000))
				else
					p.CFrame = CFrame.new(mouse.Hit.p)
				end
			else
				LineConnect(front,object,workspace)
				break
			end
			wait()
		end
		p:remove()
	end))
	while (mousedown==true) do
		if (mouse.Target~=nil) then
			local t = mouse.Target
			if (t.Anchored==false) then
				object = t
				dist = (object.Position-front.Position).magnitude
				break
			end
		end
		wait()
	end
	while (mousedown==true) do
		if (object.Parent==nil) then break end
		local lv = CFrame.new(front.Position,mouse.Hit.p)
		BP.Parent = object
		BP.position = front.Position+lv.lookVector*dist
		wait()
	end
	BP:remove()
	object = nil
	objval.Value = nil
end

function onKeyDown(key,mouse) 
	local key = key:lower() 
	local yesh = false 
	if (key=="q") then 
		if (dist>=5) then 
			dist = dist-5 
		end 
	end 
	if key == "l" then 
	if (object==nil) then return end 
	for _,v in pairs(object:children()) do 
	if v.className == "BodyGyro" then 
	return nil 
	end 
	end 
	BG = Instance.new("BodyGyro") 
	BG.maxTorque = Vector3.new(math.huge,math.huge,math.huge) 
	BG.cframe = CFrame.new(object.CFrame.p) 
	BG.Parent = object 
	repeat wait() until(object.CFrame == CFrame.new(object.CFrame.p)) 
	BG.Parent = nil 
	if (object==nil) then return end 
	for _,v in pairs(object:children()) do 
	if v.className == "BodyGyro" then 
	v.Parent = nil 
	end 
	end 
	object.Velocity = Vector3.new(0,0,0) 
	object.RotVelocity = Vector3.new(0,0,0) 
	end 
	if (key=="e") then
		dist = dist+5
	end
	if (string.byte(key)==27) then 
		if (object==nil) then return end
		local e = Instance.new("Explosion")
		e.Parent = workspace
		e.Position = object.Position
		color.BrickColor = BrickColor.Black()
		point.BrickColor = BrickColor.White() 
		wait(.48)
		color.BrickColor = BrickColor.White() 
		point.BrickColor = BrickColor.Black() 
	end
	if (key=="") then 
		if not hooked then 
		if (object==nil) then return end 
		hooked = true 
		hookBP.position = object.Position 
		if tool.Parent:findFirstChild("Torso") then 
		hookBP.Parent = tool.Parent.Torso 
		if dist ~= (object.Size.x+object.Size.y+object.Size.z)+5 then 
		dist = (object.Size.x+object.Size.y+object.Size.z)+5 
		end 
		end 
		else 
		hooked = false 
		hookBP.Parent = nil 
		end 
	end 
	if (key=="") then 
		if (object==nil) then return end 
		color.BrickColor = BrickColor.new(104) 
		point.BrickColor = BrickColor.new(11) 
		object.Parent = nil 
		wait(.48) 
		color.BrickColor = BrickColor.White() 
		point.BrickColor = BrickColor.Black() 
	end 
	if (key=="c") then 
	if (object==nil) then return end 
	local New = object:clone() 
	New.Parent = object.Parent 
	for _,v in pairs(New:children()) do 
	if v.className == "BodyPosition" or v.className == "BodyGyro" then 
	v.Parent = nil 
	end 
	end 
	object = New 
	mousedown = false 
	mousedown = true 
	LineConnect(front,object,workspace) 
		while (mousedown==true) do
		if (object.Parent==nil) then break end
		local lv = CFrame.new(front.Position,mouse.Hit.p)
		BP.Parent = object
		BP.position = front.Position+lv.lookVector*dist
		wait()
	end
	BP:remove()
	object = nil
	objval.Value = nil
	end 
	if (key=="") then 
		local Cube = Instance.new("Part") 
		Cube.Locked = true 
		Cube.Size = Vector3.new(4,4,4) 
		Cube.formFactor = 0 
		Cube.TopSurface = 0 
		Cube.BottomSurface = 0 
		Cube.Name = "WeightedStorageCube" 
		Cube.Parent = workspace 
		Cube.CFrame = CFrame.new(mouse.Hit.p) + Vector3.new(0,2,0) 
		for i = 0,5 do 
			local Decal = Instance.new("Decal") 
			Decal.Texture = "http://www.roblox.com/asset/?id=2662260" 
			Decal.Face = i 
			Decal.Name = "WeightedStorageCubeDecal" 
			Decal.Parent = Cube 
		end 
	end 
	if (key=="") then 
		if dist ~= 15 then 
			dist = 15 
		end 
	end 
end

function onEquipped(mouse)
	keymouse = mouse
	local char = tool.Parent
	human = char.Humanoid
	human.Changed:connect(function() if (human.Health==0) then mousedown = false BP:remove() point:remove() tool:remove() end end)
	mouse.Button1Down:connect(function() onButton1Down(mouse) end)
	mouse.Button1Up:connect(function() mousedown = false end)
	mouse.KeyDown:connect(function(key) onKeyDown(key,mouse) end)
	mouse.Icon = "rbxasset://textures\\GunCursor.png"
end

tool.Equipped:connect(onEquipped)


wait()
local check = script.Part2
local part1 = script.Part1.Value
local part2 = script.Part2.Value
local parent = script.Par.Value
local color = script.Color
local line = Instance.new("Part")
line.TopSurface = 0
line.BottomSurface = 0
line.Reflectance = .5
line.Name = "Laser"
line.Locked = true
line.CanCollide = false
line.Anchored = true
line.formFactor = 0
line.Size = Vector3.new(1,1,1)
local mesh = Instance.new("BlockMesh")
mesh.Parent = line
while true do
	if (check.Value==nil) then break end
	if (part1==nil or part2==nil or parent==nil) then break end
	if (part1.Parent==nil or part2.Parent==nil) then break end
	if (parent.Parent==nil) then break end
	local lv = CFrame.new(part1.Position,part2.Position)
	local dist = (part1.Position-part2.Position).magnitude
	line.Parent = parent
	line.BrickColor = color.Value.BrickColor
	line.Reflectance = color.Value.Reflectance
	line.Transparency = color.Value.Transparency
	line.CFrame = CFrame.new(part1.Position+lv.lookVector*dist/2)
	line.CFrame = CFrame.new(line.Position,part2.Position)
	mesh.Scale = Vector3.new(.25,.25,dist)
	wait()
end
line:remove()
script:remove() 
