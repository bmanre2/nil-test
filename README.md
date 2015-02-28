        char = game.Players.LocalPlayer.Character
        ra = char:FindFirstChild("Right Arm")
        la = char:FindFirstChild("Left Arm")
        torso = char.Torso
        char.Shirt:remove()
        char.Pants:remove()
char.Head.face.Texture = "http://www.roblox.com/asset/?id=136823537"
shirt=Instance.new("Shirt",char)
shirt.ShirtTemplate="http://www.roblox.com/asset/?id=217219377"
pants=Instance.new("Pants",char)
pants.PantsTemplate="http://www.roblox.com/asset/?id=217219599"

local USERNAME = game.Players.LocalPlayer.Name
local RunService = Game:GetService("RunService")

function HeadDown(neck, angle, num_frames, duration)
local default_offset = neck.C0
for frame_index = 1, num_frames do
neck.C0 = default_offset * CFrame.Angles(frame_index / num_frames * angle, 0, 0)
RunService.Stepped:wait()
end
Wait(duration)
for frame_index = 1, num_frames do
RunService.Stepped:wait()
end
end

HeadDown(workspace[USERNAME].Torso["Right Shoulder"], math.rad(-5.5), 19, 15 / 15)

local USERNAME = game.Players.LocalPlayer.Name
local RunService = Game:GetService("RunService")

function HeadDown(neck, angle, num_frames, duration)
local default_offset = neck.C0
for frame_index = 1, num_frames do
neck.C0 = default_offset * CFrame.Angles(frame_index / num_frames * angle, 0, 0)
RunService.Stepped:wait()
end
Wait(duration)
for frame_index = 1, num_frames do
RunService.Stepped:wait()
end
end

HeadDown(workspace[USERNAME].Torso["Left Shoulder"], math.rad(-5.5), 19, 15 / 15)



local USERNAME = game.Players.LocalPlayer.Name
local RunService = Game:GetService("RunService")

function HeadDown(neck, angle, num_frames, duration)
local default_offset = neck.C0
for frame_index = 1, num_frames do
neck.C0 = default_offset * CFrame.Angles(frame_index / num_frames * angle, 0, 0)
RunService.Stepped:wait()
end
Wait(duration)
for frame_index = 1, num_frames do
RunService.Stepped:wait()
end
end

HeadDown(workspace[USERNAME].Torso["Left Hip"], math.rad(-5.5), 19, 15 / 15)



local USERNAME = game.Players.LocalPlayer.Name
local RunService = Game:GetService("RunService")

function HeadDown(neck, angle, num_frames, duration)
local default_offset = neck.C0
for frame_index = 1, num_frames do
neck.C0 = default_offset * CFrame.Angles(frame_index / num_frames * angle, 0, 0)
RunService.Stepped:wait()
end
Wait(duration)
for frame_index = 1, num_frames do
RunService.Stepped:wait()
end
end

HeadDown(workspace[USERNAME].Torso["Right Hip"], math.rad(-5.5), 19, 15 / 15)

















































plr = game:service'Players'.LocalPlayer
char = plr.Character
mouse = plr:GetMouse()
humanoid = char:findFirstChild("Humanoid")
torso = char:findFirstChild("Torso")
head = char.Head
ra = char:findFirstChild("Right Arm")
la = char:findFirstChild("Left Arm")
rl = char:findFirstChild("Right Leg")
ll = char:findFirstChild("Left Leg")
rs = torso:findFirstChild("Right Shoulder")
ls = torso:findFirstChild("Left Shoulder")
rh = torso:findFirstChild("Right Hip")
lh = torso:findFirstChild("Left Hip")
neck = torso:findFirstChild("Neck")
rj = char:findFirstChild("HumanoidRootPart"):findFirstChild("RootJoint")
anim = char:findFirstChild("Animate")
rootpart = char:findFirstChild("HumanoidRootPart")
camera = workspace.CurrentCamera
if anim then
anim:Destroy()
end

local rm = Instance.new("Motor", torso)
rm.C0 = CFrame.new(1.5, 0.5, 0)
rm.C1 = CFrame.new(0, 0.5, 0)
rm.Part0 = torso
rm.Part1 = ra
local lm = Instance.new("Motor", torso)
lm.C0 = CFrame.new(-1.5, 0.5, 0)
lm.C1 = CFrame.new(0, 0.5, 0)
lm.Part0 = torso
lm.Part1 = la

local rlegm = Instance.new("Motor", torso)
rlegm.C0 = CFrame.new(0.5, -1, 0)
rlegm.C1 = CFrame.new(0, 1, 0)
rlegm.Part0 = torso
rlegm.Part1 = rl
local llegm = Instance.new("Motor", torso)
llegm.C0 = CFrame.new(-0.5, -1, 0)
llegm.C1 = CFrame.new(0, 1, 0)
llegm.Part0 = torso
llegm.Part1 = ll

rsc0 = rm.C0
lsc0 = lm.C0
llc0 = llegm.C0
rlc0 = rlegm.C0
neckc0 = neck.C0
rootc0 = rj.C0

local count = 0
local countspeed = 1

while wait() do
count = (count % 100) + countspeed
angle = math.pi * math.sin(math.pi*2/100*count)
if Vector3.new(torso.Velocity.x, 0, torso.Velocity.z).magnitude < 2 then
countspeed = 1
--Idle anim
rlegm.C0 = rlc0 * CFrame.Angles(angle*0.025, 0, 0)
llegm.C0 = llc0 * CFrame.Angles(-angle*0.025, 0, 0)
rm.C0 = rsc0 * CFrame.Angles(-angle*0.05, 0, 0)
lm.C0 = lsc0 * CFrame.Angles(angle*0.05, 0, 0)
elseif Vector3.new(torso.Velocity.x, 0, torso.Velocity.z).magnitude > 2 then
countspeed = 4
--Walk anim
rlegm.C0 = rlc0 * CFrame.Angles(angle*0.27, 0, angle*0.080)
llegm.C0 = llc0 * CFrame.Angles(-angle*0.27, 0, angle*0.080)
rm.C0 = rsc0 * CFrame.Angles(-angle*0.245, 0, angle*0.080)
lm.C0 = lsc0 * CFrame.Angles(angle*0.245, 0, angle*0.080)
end
end


