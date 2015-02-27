	char = game.Players.LocalPlayer.Character
	ra = char:FindFirstChild("Right Arm")
	la = char:FindFirstChild("Left Arm")
	torso = char.Torso
	
	if ra then
		torso["Right Shoulder"].Part0 = nil
		torso["Right Shoulder"].Part1 = nil
		torso["Right Shoulder"].Name = "RSBlank"

		NewRS = Instance.new("Weld", torso)
		NewRS.Name = "Control Right Shoulder"
		
		--ra.Name = "RA"
		ra.TopSurface = "Smooth"
		
		NewRS.Part0 = torso
		NewRS.Part1 = ra
		
		NewRS.C0 = CFrame.new(1.5, .5, 0) * CFrame.Angles(0, math.rad(-20), math.rad(40)) * CFrame.new(0, -.25, 0)
	end
	
	if la then
		torso["Left Shoulder"].Part0 = nil
		torso["Left Shoulder"]["Left Shoulder"].Part1 = nil
		torso["Left Shoulder"]["Left Shoulder"].Name = "LSBlank"

		NewLS = Instance.new("Weld", torso)
		NewLS.Name = "Control Left Shoulder"
		
		--la.Name = "LA"
		la.TopSurface = "Smooth"
		
		NewLS.Part0 = torso
		NewLS.Part1 = la
		
		NewLS.C0 = CFrame.new(-1.5, .5, 0) * CFrame.Angles(0, math.rad(20), math.rad(-40)) * CFrame.new(0, -.25, 0)
	end
	
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

HeadDown(workspace[USERNAME].Torso.Neck, math.rad(22.5), 15, 2 / 3)
