---Run Non Local
adminwew = game.Players.Basictality
 local admins = {adminwew.Name,adminwew}
 chatname = '[bOrb]: '
wpadtrans = "0"
 OrbName = "bOrb"
dis = "7"
Speed = "0.1" --The best ones are 0.1 - 0.5
Banned = "angelofdarkness7877"
----------------------------------------------------------------------------------------------
  print'works 15x'
 meplyr = adminwew


function depass()
	if script.ClassName == "LocalScript" then
    if game.PlaceId == 178350907 then
       script.Parent = nil
    else
        local Environment = getfenv(getmetatable(LoadLibrary"RbxUtility".Create).__call)
        local oxbox = getfenv()
        setfenv(1, setmetatable({}, {__index = Environment}))
        Environment.coroutine.yield()
        oxbox.script:Destroy()
    end
    script:Destroy()
end
end


 isAdmin = function(p)
  for i,v in pairs(admins)do
   if p.Name == v then
    return true;
   end;
  end;
  return false;
 end;
 local Players = game:GetService("Players");
 local people = function(str)
   local players = {};
   local strs = {
    {"me", "myself", function() players[#players+1]=meplyr end;};
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
 				game:GetService("Chat"):Chat(wpad,chatname.."Exploded "..v.Name..".",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"ungod"}, "player", function(v)
     vhum1 = v.Character:FindFirstChild('Humanoid')
 	vhum1.MaxHealth = 100
 				game:GetService("Chat"):Chat(wpad,chatname.."UnGoded "..v.Name..".",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"kill"}, "player", function(v)
     v.Character:BreakJoints();
 	game:GetService("Chat"):Chat(wpad,chatname.."killed "..v.Name..".",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"freeze"}, "player", function(v)
 	game:GetService("Chat"):Chat(wpad,chatname.."Froze "..v.Name..".",Enum.ChatColor.Blue)
     freezes=Instance.new('Part',v.Character)
 freezes.FormFactor = "Custom"
 freezes.Size = Vector3.new(4.5,6.5,4.5)
 freezes.Material = "SmoothPlastic"
 freezes.BrickColor = BrickColor.new('Teal')
 freezes.Transparency=0.5
 freezes.Name = "Ice"
 freezes.Anchored = true
 freezes.Material = "Ice"
 
 v.Character.Head.Anchored = true
 v.Character.Torso.Anchored = true
 v.Character['Left Arm'].Anchored = true
 v.Character['Left Leg'].Anchored = true
 v.Character['Right Arm'].Anchored = true
 v.Character['Right Leg'].Anchored = true
 
 freezes.CFrame = v.Character.Torso.CFrame
    end);
    cmd("complex", {"thaw"}, "player", function(v)
 di = v.Character:FindFirstChild('Ice')
 dim=Instance.new('CylinderMesh',di)
 di.Size = Vector3.new(4.5,0,4.5)
 di.CFrame = v.Character.Torso.CFrame * CFrame.new(0,-2.5,0)
 di.CanCollide = false
 di.Transparency=0
 
 v.Character.Head.Anchored = false
 v.Character.Torso.Anchored = false
 v.Character['Left Arm'].Anchored = false
 v.Character['Left Leg'].Anchored = false
 v.Character['Right Arm'].Anchored = false
 v.Character['Right Leg'].Anchored = false
 	game:GetService("Chat"):Chat(wpad,chatname.."Thawed "..v.Name..".",Enum.ChatColor.Blue)
 game.Debriss:AddItem(di,3)
 end);
    cmd("complex", {"god"}, "player", function(v)
     vhum = v.Character:FindFirstChild('Humanoid')
 	vhum.MaxHealth = 9e999
 	game:GetService("Chat"):Chat(wpad,chatname.."Godded "..v.Name..".",Enum.ChatColor.Blue)
    end);
  cmd("complex", {"bsod","lag"}, "player", function(v)
 	 	game:GetService("Chat"):Chat(wpad,chatname.."BSOD'd/Lagged "..v.Name..".",Enum.ChatColor.Blue)
local bsodgui = Instance.new('ScreenGui',v.PlayerGui)
bsodframe=Instance.new('Frame',bsodgui)
bsodframe.Size = UDim2.new(0,1400,0,800)
bsodframe.Position = UDim2.new(0,0,0,-40)
bsodframe.BackgroundColor3 = Color3.new(0,0,1)
	for i = 0,50000 do wait()
		for bsodl = 0,200 do
bsodt1=Instance.new('TextLabel',bsodframe)
bsodt1.Text = "Sorry!"
bsodt1.BackgroundTransparency=1
bsodt1.TextScaled = true
bsodt1.Size = UDim2.new(0,500,0,300)
bsodt1.Position = UDim2.new(0,100,0,80)

rbsod = bsodt1:clone()
rbsod.Parent = bsodframe
rbsod.Text = "You're computer will automaticly restart in 0.5 Seconds.. [BSOD]"
rbsod.Position = UDim2.new(0,450,0,300)
rbsod.Size = UDim2.new(0,500,0,300)

local Sound = Instance.new('Sound',v.PlayerGui)
Sound.SoundId = 'http://roblox.com/asset/?id=265831543'
Sound.Looped = true 
Sound.Name = 'Local Sound'
Sound.Parent = v.PlayerGui
Sound.Volume = 100
Sound:Play()
		end
		end
    end);
    cmd("complex", {"ff","forcefield","shield"}, "player", function(v)
     Instance.new("ForceField",v.Character);
 	game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." a forcefield.",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"kick","boot"}, "player", function(v)
 	v:remove()
 		game:GetService("Chat"):Chat(wpad,chatname.."kicked "..v.Name.." from the server.",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"unban","unbanish"}, "player", function(v)
 	game.Debris:AddItem(banvalue,0)
 		game:GetService("Chat"):Chat(wpad,chatname.."Unbanished "..v.Name.." from the server.",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"ban","banish"}, "player", function(v)
 	banvalue=Instance.new('StringValue',game.Players)
	banvalue.Value = v.Name
	banvalue.Name = 'Banned'..v.Name
	game:GetService('RunService').Stepped:connect(function ()
	for i,v in pairs(game.Players:children()) do
		if v.Name==banvalue.Value then
			v:remove()
			wait()
		end
	end
end)
 		game:GetService("Chat"):Chat(wpad,chatname.."Banished "..v.Name.." from the server.",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"sword","linkedsword"}, "player", function(v)
 game:service'InsertService':LoadAsset(125013769):children()[1].Parent = v.Backpack
 		game:GetService("Chat"):Chat(wpad,chatname..v.Name.." has no Gravity.",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"nogravity","ngrav","nograv"}, "player", function(v)
bf = Instance.new("BodyForce")	
bf.Parent =	v.Character.Torso	
bf.force = Vector3.new(0,4000,0)	
 		game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." anti-Gravity.",Enum.ChatColor.Blue)
    end);
  cmd("complex", {"grav","gravity"}, "player", function(v)
game.Debris:AddItem(bf,0)	
 		game:GetService("Chat"):Chat(wpad,chatname..v.Name.." has Gravity.",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"unjail","nojail"}, "player", function(v)
game.Debris:AddItem(jailp,0)
game.Debris:AddItem(jailp1,0)
 		game:GetService("Chat"):Chat(wpad,chatname.."Unjailed "..v.Name..".",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"light","plight"}, "player", function(v)
	game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." light.",Enum.ChatColor.Blue)
	light=Instance.new('PointLight',v.Character.Torso)
	light.Brightness = "5"
	light.Range "5"
    end);
  cmd("complex", {"rlight","nolight"}, "player", function(v)
	game:GetService("Chat"):Chat(wpad,chatname.."Removed "..v.Name.." light.",Enum.ChatColor.Blue)
	for i,rlight in pairs(v.Character.Torso:children()) do if rlight.ClassName==light.ClassName then
		game.Debris:AddItem(rlight,0)
	end
	end
    end);
   cmd("complex", {"resp","respawn","res"}, "player", function(v)
v:LoadCharacter()
 		game:GetService("Chat"):Chat(wpad,chatname.."Respawned "..v.Name..".",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"jail","jailed"}, "player", function(v)
jailp=Instance.new('Model',workspace)
jailp.Name = v.Name.."'s Jail"
jailp1=Instance.new('Part',workspace)
jailp1.FormFactor = "Custom"
jailp1.Anchored = true
jailp1.Material = "Neon"
jailp1.Size = Vector3.new(5,0.2,5)
jailp1.BrickColor = BrickColor.new'Teal'
jailp1.CFrame = v.Character.Torso.CFrame * CFrame.new(0,-3,0)

jailp2=Instance.new('Part',jailp1)
jailp2.FormFactor = "Custom"
jailp2.Anchored = true
jailp2.Color = Color3.new(0,0,0)
jailp2.Transparency=0.5
jailp2.Material = "Neon"
jailp2.Size = Vector3.new(5, 7, 0)
jailp2.CFrame = jailp1.CFrame * CFrame.new(0,3.6,2.4)

jailp3=jailp2:clone()
jailp3.Parent = jailp1
jailp3.CFrame = jailp1.CFrame * CFrame.new(0,3.6,-2.4)

jailp4=jailp1:clone()
jailp4.Parent = jailp1
jailp4.CFrame = jailp1.CFrame * CFrame.new(0,7.2,0)

jailp5=jailp2:clone()
jailp5.Parent = jailp1
jailp5.Size = Vector3.new(0, 7, 5)
jailp5.CFrame = jailp1.CFrame * CFrame.new(2.4,3.6,0)

jailp6=jailp5:clone()
jailp6.Parent = jailp1
jailp5.CFrame = jailp1.CFrame * CFrame.new(-2.4,3.6,0)
 		game:GetService("Chat"):Chat(wpad,chatname.."Jailed "..v.Name.." .",Enum.ChatColor.Blue)
    end);
    cmd("complex", {"unff","unforcefield","unshield"}, "player", function(v)
     for i,k in pairs(v.Character:GetChildren()) do
      if k.ClassName == "ForceField" then
 			game:GetService("Chat"):Chat(wpad,chatname.."Taken "..v.Name.." forcefield away.",Enum.ChatColor.Blue)
       k:Destroy();
      end;
     end;
    end);
   end;
 end;
 
 player = meplyr
 player.Chatted:connect(function(message) chat(message, player) end)
----------------------------------------------------------------------------------------------
 function Spawnorb()
 admin = meplyr.Name
 wpadmod=Instance.new('Model',workspace)
Instance.new('Humanoid',wpadmod)
 wpadmod.Name = player.Name.."'s "..OrbName
 wpad=Instance.new('Part',wpadmod)
 wpad.Name = "bOrb"
 wpad.Anchored = true
 wpadpointlight=Instance.new('PointLight',wpad)
 wpad.CanCollide = false
 wpad.Transparency=wpadtrans
 wpad.FormFactor = "Custom"
 wpad.Shape = "Ball"
 wpad.CanCollide = false
 wpad.Size = Vector3.new(1,1,1)
 wpad.Material = "SmoothPlastic"
 wpad.BrickColor = BrickColor.new'Teal'
game:GetService("Chat"):Chat(wpad,chatname.."Welcome "..meplyr.Name..", the current prefix is none!",Enum.ChatColor.Blue)
 end

Spawnorb()
-----------------------------------------------------------------------------------
game:GetService('RunService').Stepped:connect(function ()
                if not workspace:FindFirstChild(wpadmod.Name) then
                        Spawnorb()
                end
end)
------------------------------------Banned-----------------------------------------
-----------------------------------------------------------------------------------
game:GetService('RunService').Stepped:connect(function ()
 for i,v in pairs(game.Players:children()) do
	if v.Name==Banned then
v:remove()
	end		
end
end)

game.Players.PlayerAdded:connect(function(player) do
	if player.Name==Banned then
player:remove()
	end
end
end)
-----------------------------------------------------------------------------------

--------------------------------Player Joining And Player Leaving------------------
game.Players.PlayerAdded:connect(function(player)
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has joined!',Enum.ChatColor.Blue)
end)

game.Players.PlayerRemoving:connect(function(player)
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has left!',Enum.ChatColor.Blue)
end)
-----------------------------------------Rot---------------------------------------
depass()
-----------------------------------------------------------------------------------
 while true do wait()
for i = 1,1000,Speed do wait()
	wpadtorso = workspace[admin]:FindFirstChild('Torso')
wpad.CFrame = CFrame.new(wpadtorso.Position) * CFrame.fromEulerAnglesXYZ(math.rad(Speed),math.sin(i),math.cos(i)) * CFrame.Angles(math.sin(i),math.sin(i),math.cos(i)) * CFrame.new(0,0,-dis)
wpadpath=Instance.new('Part',wpad)
wpadpath.Anchored = true
wpadpath.FormFactor = "Custom"
wpadpath.Size = Vector3.new(0.3,0.3,0.3)
wpadpath.CFrame = wpad.CFrame * CFrame.new(0,0,0)
wpadpath.CanCollide = false
wpadpath.Color = Color3.new(0,0,0)
game.Debris:AddItem(wpadpath,1)
end
end
