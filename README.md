local admins = {"Basictality"}

--prefix is nil
-- so use kill whatever to kill anyone
-- i also fixed thing u wanted me to fix
--have fun

local isAdmin = function(p)
 for i,v in pairs(admins)do
  if p.Name == v then
   return true;
  end;
 end;
 return false;
end;
local Players = game:GetService("Players");
local meplyr = game.Players.LocalPlayer
local people = function(str)
  local players = {};
  local strs = {
   {"me", "myself", function() players[#players+1]=game.Players.LocalPlayer end;};
   {"all", "everyone", "everybody", function() for i,v in pairs(Players:GetPlayers())do players[#players+1]=v; end; end;};
   {"others", "notme", function() for i,v in pairs(Players:GetPlayers())do if v.Name~= meplyr.Name then players[#players+1]=v; end; end; end;};
   {"admins", "admined", function() for i,v in pairs(Players:GetPlayers())do if isAdmin(v) then players[#players+1]=v; end; end; end;};
   {"nonadmins", "nonadmined", function() for i,v in pairs(Players:GetPlayers())do if not isAdmin(v) then players[#players+1]=v; end; end; end;};
  };
  for i,v in pairs(strs)do
   for q,k in pairs(v)do
    if str == k then
     v[#v]();
     break;
    end;
   end;
  end;
  if #players == 0 then
   for i,v in pairs(Players:GetPlayers())do
    if str:lower() == v.Name:lower():sub(1,string.len(str)) then
     players[#players+1]=v;
    end;
   end;
  end;
  return players;
 end;
--   if Prefix..data.Usage..Suffix == sub(lower(Message),1,string.len(Prefix)+string.len(data.Usage)+string.len(Suffix)) then
--    local y,n = ypcall(function()
--      data.Func(sub(Message,string.len(Prefix)+string.len(data.Usage)+string.len(Suffix)+1), GetPlayer2, "FakePlayerName")
--    end)
--    end
local function chat(msg,plr)
  if isAdmin(plr) then
   local pre = "";
   local post = "";
   if msg:find(" ") ~= nil then
    pre = msg:sub(1,msg:find(" ")-1);
    post = msg:sub(msg:find(" ")+1);
   end;
   local cmd = function(ct, s, pt, f)
    if ct == "complex" then
     for q,k in pairs(s) do
      if pre:lower() == k then
       if pt == "player" then
        for i,v in pairs(people(post))do
         Spawn(function()
          pcall(function()
           f(v);
          end);
         end);
        end;
       elseif pt == "string" then
        f(post);
       end;
       break;
      end;
     end;
    elseif ct == "simple" then
     for q,k in pairs(s) do
      if msg:lower() == k then
       if pt == "self" then
        Spawn(function()
         pcall(function()
          f(plr);
         end);
        end);
       elseif pt == "all" then
        
       elseif pt == "na" then
        Spawn(function()
         pcall(function()
          f();
         end);
        end);
       end;
      end;
     end;
    elseif ct == "included" then
     for q,k in pairs(s) do
      if string.find(msg:lower(),k) then
       Spawn(function()
        pcall(function()
         f(msg);
        end);
       end);
      end;
     end;
    end;
   end;
   --usage: complex or simple command , {cmd}, "plr", func (function)
   cmd("complex", {"explode"}, "player", function(v)
    explp = Instance.new("Explosion",v.Character);
	explp.BlastRadius = "1";
	explp.BlastPressure = "500000";
	explp.Position = v.Character.Torso.Position;
   end);
   cmd("complex", {"ungod"}, "player", function(v)
    vhum1 = v.Character:FindFirstChild('Humanoid')
	vhum1.MaxHealth = 100
   end);
   cmd("complex", {"kill"}, "player", function(v)
    v.Character:BreakJoints();
   end);
   cmd("complex", {"god"}, "player", function(v)
    vhum = v.Character:FindFirstChild('Humanoid')
	vhum.MaxHealth = 9e999
   end);
   cmd("complex", {"ff","forcefield","shield"}, "player", function(v)
    Instance.new("ForceField",v.Character);
   end);
   cmd("complex", {"kick","boot"}, "player", function(v)
   v:remove()
    wait(2);
    if v ~= nil
     then
     pcall(function()
     v:remove()
     end)
end
   end);
   cmd("complex", {"unff","unforcefield","unshield"}, "player", function(v)
    for i,k in pairs(v.Character:GetChildren()) do
     if k.ClassName == "ForceField" then
      k:Destroy();
     end;
    end;
   end);
  end;
end;

player = game.Players.Basictality
player.Chatted:connect(function(message) chat(message, player) end)



-- Chat
--
--

script.Name = "Chat"
--[[
local CloneScript = game:GetService("ReplicatedStorage"):FindFirstChild("Chat") or script:Clone()
CloneScript.Parent = game:GetService("ReplicatedStorage")
CloneScript.Disabled = true]]

--script.Parent = nil

local user = game:GetService('Players')['LocalPlayer']
local chats = {}

--

pcall(function() 
	for i,v in next,user.Character.Head:GetChildren() do
		if v.ClassName == "BillboardGui" then
			v:remove()
		end
	end
end)

function color(r,g,b)
	return Color3.new(r/255,g/255,b/255)
end

--

user.CharacterAdded:connect(function()
	for i,v in next,chats do
		v.Removed = true
	end
end)
--[=[
user.Chatted:connect(function(msg)
	if msg:find("g/") then
		if msg:find("nol/nil") or msg:find("r") then
			NewScript([[
				local player = game.Players.]]..user.Name..[[
				repeat wait() until player.Character
					wait(.1)
				local scrip = game:GetService("ReplicatedStorage")["Chat"]:clone()
				scrip.Parent = player.Character
				scrip.Disabled = false
				script.Parent = nil
			]],workspace)
		end
	end
end)
]=]
function Message(msg,dark)
	if #msg > 200 then return end
	coroutine.wrap(function()
		delay(0,function()
			local char = user.Character
			local isDark = dark or false

			local y = -40
			for i = #chats,1,-1 do
				local v = chats[i]
				if v.Removed == false then
					y = y - 40
					v.Message:TweenPosition(UDim2.new(.5,v.Message.Position.X.Offset,1,y),"In","Linear",0.5,true,function()
						if v.Message.Position.Y.Offset <= -40*4 then
							v.Remove = true
						end
					end)
				end
			end

			local bg = Instance.new('BillboardGui',char['Head'])
			bg.Name = 'Chat'
			bg.StudsOffset = Vector3.new(0,7,0)
			bg.Adornee = char['Head']
			bg.Size = UDim2.new(10,0,10,0)
			bg.AlwaysOnTop = true

			local mesg = ""
			for i = 1, #msg do
				mesg = mesg .. msg:sub(i,i) .. "\127"
			end

			local tl = Instance.new('TextLabel',bg)
			tl.Text = mesg
			tl.Name = "Message"
			tl.BorderSizePixel = 0
			tl.ClipsDescendants = true
			tl.BackgroundTransparency = 1
			tl.TextTransparency = 1
			if isDark then
				tl.TextColor = BrickColor.new('Bright red')
			else
				tl.TextColor = BrickColor.new('White')
			end
			tl.FontSize = 6
			tl.Size = UDim2.new(0,tl.TextBounds.X+25,0,0)
			tl.Position = UDim2.new(.5,(-tl.TextBounds.X-25)/2,1,0)

			tl:TweenSizeAndPosition(UDim2.new(0,tl.TextBounds.X+25,0,40),UDim2.new(.5,(-tl.TextBounds.X-25)/2,1,-40),"In","Linear",0.5,true)

			local spot = #chats+1

			chats[spot] = {Message = tl,Removed = false,Remove = false}

			local r,g,b = math.random(1,255),math.random(1,255),math.random(1,255)
			local rr,gr,br = false,false,false
			local removed = false

			delay(0,function()
				for i = 1,.5,-.05 do
					wait(0.05)
					tl.BackgroundTransparency = i
				end
			end)
			delay(0,function()
				for i = 1,0,-.1 do 
					wait(0.05)
					tl.TextTransparency = i
				end
			end)

			delay(0,function()
				while removed == false do
					wait(0.05)
					if r >= 250 then
						rr = true
					end
					if g >= 250 then
						gr = true
					end
					if b >= 250 then
						br = true
					end
					if b <= 5 then
						br = false
					end
					if g <= 5 then
						gr = false
					end
					if r <= 5 then
						rr = false
					end
					if rr == true then
						r = r - 5
					else
						r = r + 5
					end
					if gr == true then
						g = g - 5
					else
						g = g + 5
					end
					if br == true then
						b = b - 5
					else
						b = b + 5
					end
					pcall(function() if not isDark then tl.BackgroundColor3 = color(r,g,b) else tl.BackgroundColor = BrickColor.new("Really black") end end)
				end
			end)

			local remove = false

			delay(0,function()
				wait(15)
				remove = true
			end)

			delay(0,function()
				while remove == false do
					wait()
					if chats[spot].Remove == true then
						remove = true
					end
				end
			end)

			delay(0,function()
				repeat wait() until remove == true
				delay(0,function()
					for i = .5,1,.05 do
						wait(0.05)
						tl.BackgroundTransparency = i
					end
				end)
				delay(0,function()
					for i = 0,1,.1 do 
						wait(0.05)
						tl.TextTransparency = i
					end
					bg:remove()
					removed = true
					chats[spot].Removed = true
				end)
			end)
		end)
	end)()
end

user.Chatted:connect(function(msg)
	if msg:sub(1,3) ~= "/e " and msg:sub(1,1) ~= "!" then
		Message(msg,false)
	end
	if msg:sub(1,1) == "!" then
		Message(msg:sub(2),true)
	end
end)

Message("Thankx for using Basictalty's Admin Commands. =)",false)
