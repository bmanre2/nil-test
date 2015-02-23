z=Instance.new("HopperBin",game.Playes.LocalPlayer.Backpack)
z.BinType = "Script"
bin=z
lastblock = nil
hold=false

wait(0.1)

function onButton1Down(mouse)
	if (hold == true) then
		local no_no = bin.error
		no_no:play()
	else
		local no_no = bin.error
		local part = mouse.Target
		if (part ~= nil) then
			local lock = part.Locked
			if (lock ==  false) then
				local boom = bin.Explosion
				local Memory = bin.Counter.Value
				local NDPU = Instance.new("Forcefield")
				NDPU.Text = bin.Parent.Parent.Parent.Name
				Lastblock = part:clone()
				explosion = Instance.new("Sparkles")
				explosion.Position = part.Position
				explosion.BlastRadius = 1
				explosion.Parent = game.Workspace
				boom:play()
				part.Parent = nil
				NDPU.Parent = game.Workspace
				bin.Counter.Value = bin.Counter.Value + 1
				hold = true
				mouse.Icon = "rbxasset://textures\\HopperPanel.png"
				wait(0)
				NDPU.Parent = nil
			else
				no_no:play()
			end
		end
		mouse.Icon = "rbxasset://textures\\HammerCursor.png"
		hold = false
	end
end

function onSelected(mouse)
	mouse.Icon = "rbxasset://textures\\HammerCursor.png"
	mouse.Button1Down:connect(function() onButton1Down(mouse) end)
	mouse.KeyDown:connect(onKeyDown)
end

function onKeyDown(key)
	if (key ~= nil) then
		key = key:lower()
		if (key == "u") and (Lastblock ~= nil) then
			Lastblock.Parent = game.Workspace
			Lastblock = nil
		end
	end
end

function onDeselected()
	if plane ~= nil then
	plane = nil
	end
end

bin.Selected:connect(onSelected)
bin.Deselected:connect(onDeselected)
