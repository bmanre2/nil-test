---Run Non Local
adminwew = game.Players.Basictality
 local admins = {adminwew.Name,adminwew}
 chatname = '[bOrb]: '
wpadtrans = "0"
 OrbName = "bOrb"
dis = "7"
Speed = "0.1" --The best ones are 0.1 - 0.5
Banned = "angelofdarkness7877"
Chat = true
----------------------------------------------------------------------------------------------
  print'works 15x'
 meplyr = adminwew

----------cmds gui-----------
for i,v in pairs(game.Players:children()) do
function OnChatted(cmds)
	    if cmds:lower():sub(1,6) == "cmds" then
cmdgui=Instance.new('ScreenGui',v.PlayerGui)
cmdframe=Instance.new('Frame',cmdgui)
cmdframe.Size = UDim2.new(0,500,0,350)
cmdframe.Position = UDim2.new(0,430,0,-300)
cmdframe:TweenPosition(UDim2.new(0,430,0,200),'Out','Quad',0.35)
cmdframe.BackgroundTransparency=0.5
cmdframe.BackgroundColor3 = Color3.new(0,0,0)

cmdtl=Instance.new('TextLabel',cmdframe)
cmdtl.Text = "Commands [22]"
cmdtl:TweenSize(UDim2.new(0,500,0,50),'Out','Quad',0.35)
cmdtl.TextScaled = true
cmdtl.BackgroundTransparency=1
cmdtl.TextColor3 = Color3.new(255,255,255)
cmdtl.TextStrokeTransparency = 0

cmdbutton=Instance.new('TextButton',cmdframe)
cmdbutton.TextScaled = true
cmdbutton.Text = "X"
cmdbutton.BackgroundTransparency = 1
cmdbutton.TextColor3 = Color3.new(1,0,0)
cmdbutton.Size = UDim2.new(0,50,0,50)
cmdbutton:TweenPosition(UDim2.new(0,450,0,0),'Out','Quad',0.35)

function onClick()
	cmdframe:TweenPosition(UDim2.new(0,430,0,700),'Out','Quad',0.35)
	game.Debris:AddItem(cmdframe,2)
end

cmdbutton.MouseButton1Down:connect(onClick)

sf=Instance.new('ScrollingFrame',cmdframe)
sf:TweenSize(UDim2.new(0,480,0,260),'Out','Quad',0.35)
sf:TweenPosition(UDim2.new(0,10,0,50),'Out','Quad',0.35)
sf.BackgroundTransparency = 0.5
sf.BackgroundColor3 = Color3.new(0,0,0)

fc=Instance.new('TextLabel',sf)
fc.TextColor3 = Color3.new(255,255,255)
fc.TextScaled = true
fc.Text = "Explode <plyr>"
fc.BackgroundColor = BrickColor.new'Dark blue'
fc:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
fc.BackgroundTransparency=0

sc=fc:Clone()
sc.Parent = sf
sc.Text = "kill <plyr>"
sc:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
sc:TweenPosition(UDim2.new(0,0,0,35),'Out','Quad',0.35)

tc=sc:clone()
tc.Parent = sf
tc.Text = "UnGod <plyr>"
tc:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
tc:TweenPosition(UDim2.new(0,0,0,70),'Out','Quad',0.35)

fc=sc:clone()
fc.Parent = sf
fc.Text = "Freeze <plyr>"
fc:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
fc:TweenPosition(UDim2.new(0,0,0,105),'Out','Quad',0.35)

fic=sc:clone()
fic.Parent = sf
fic.Text = "Thaw <plyr>"
fic:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
fic:TweenPosition(UDim2.new(0,0,0,140),'Out','Quad',0.35)

sic=sc:clone()
sic.Parent = sf
sic.Text = "resp/respawn/res <plyr>"
sic:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
sic:TweenPosition(UDim2.new(0,0,0,175),'Out','Quad',0.35)

sec=sc:clone()
sec.Parent = sf
sec.Text = "God <plyr>"
sec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
sec:TweenPosition(UDim2.new(0,0,0,210),'Out','Quad',0.35)

eec=sc:clone()
eec.Parent = sf
eec.Text = "BSOD/Lag <plyr>"
eec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
eec:TweenPosition(UDim2.new(0,0,0,245),'Out','Quad',0.35)

nec=sc:clone()
nec.Parent = sf
nec.Text = "ff/shield/forcefield <plyr>"
nec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
nec:TweenPosition(UDim2.new(0,0,0,280),'Out','Quad',0.35)

tec=sc:clone()
tec.Parent = sf
tec.Text = "kick/boot <plyr>"
tec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
tec:TweenPosition(UDim2.new(0,0,0,315),'Out','Quad',0.35)

elec=sc:clone()
elec.Parent = sf
elec.Text = "ban/banish <plyr>"
elec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
elec:TweenPosition(UDim2.new(0,0,0,350),'Out','Quad',0.35)

twec=sc:clone()
twec.Parent = sf
twec.Text = "unban/unbanish <plyr>"
twec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twec:TweenPosition(UDim2.new(0,0,0,385),'Out','Quad',0.35)

thec=sc:clone()
thec.Parent = sf
thec.Text = "sword <plyr>"
thec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
thec:TweenPosition(UDim2.new(0,0,0,420),'Out','Quad',0.35)

foec=sc:clone()
foec.Parent = sf
foec.Text = "ngrav/nograv/nogravity <plyr>"
foec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
foec:TweenPosition(UDim2.new(0,0,0,455),'Out','Quad',0.35)

fiec=sc:clone()
fiec.Parent = sf
fiec.Text = "grav/gravity <plyr>"
fiec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
fiec:TweenPosition(UDim2.new(0,0,0,490),'Out','Quad',0.35)

sixec=sc:clone()
sixec.Parent = sf
sixec.Text = "unjail/nojail <plyr>"
sixec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
sixec:TweenPosition(UDim2.new(0,0,0,525),'Out','Quad',0.35)

sitec=sc:clone()
sitec.Parent = sf
sitec.Text = "light/plight <plyr>"
sitec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
sitec:TweenPosition(UDim2.new(0,0,0,560),'Out','Quad',0.35)

enitec=sc:clone()
enitec.Parent = sf
enitec.Text = "rlight/nolight/unlight <plyr>"
enitec:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
enitec:TweenPosition(UDim2.new(0,0,0,595),'Out','Quad',0.35)

nineteen=sc:clone()
nineteen.Parent = sf
nineteen.Text = "jail/jailed <plyr>"
nineteen:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
nineteen:TweenPosition(UDim2.new(0,0,0,630),'Out','Quad',0.35)

twenty=sc:clone()
twenty.Parent = sf
twenty.Text = "unff/unforcefield/unshield <plyr>"
twenty:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twenty:TweenPosition(UDim2.new(0,0,0,630),'Out','Quad',0.35)

twenty1=sc:clone()
twenty1.Parent = sf
twenty1.Text = "jail <plyr>"
twenty1:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twenty1:TweenPosition(UDim2.new(0,0,0,665),'Out','Quad',0.35)

twenty2=sc:clone()
twenty2.Parent = sf
twenty2.Text = "sit <plyr>"
twenty2:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twenty2:TweenPosition(UDim2.new(0,0,0,0),'Out','Quad',0.35)
twenty2.TextTransparency=1
twenty2.BackgroundTransparency=1

twenty3=sc:clone()
twenty3.Parent = sf
twenty3.Text = "jump <plyr>"
twenty3:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twenty3:TweenPosition(UDim2.new(0,0,0,35),'Out','Quad',0.35)
twenty3.TextTransparency=1
twenty3.BackgroundTransparency=1

twenty4=sc:clone()
twenty4.Parent = sf
twenty4.Text = "Commands/Cmds"
twenty4:TweenSize(UDim2.new(0,475,0,30),'Out','Quad',0.35)
twenty4:TweenPosition(UDim2.new(0,0,0,70),'Out','Quad',0.35)
twenty4.TextTransparency=1
twenty4.BackgroundTransparency=1

newp=Instance.new('TextButton',cmdframe)
newp.Text = ">"
newp.TextColor3 = Color3.new(255,255,255)
newp.TextScaled = true
newp:TweenSize(UDim2.new(0,100,0,30),'Out','Quad',0.35)
newp:TweenPosition(UDim2.new(0,370,0,315),'Out','Quad',0.35)

function onClick()
	for i,v in pairs(sf:children()) do if v.ClassName=="TextLabel" then
		v.TextTransparency = 1
		v.BackgroundTransparency = 1
		twenty2.TextTransparency=0
		twenty2.BackgroundTransparency=0
		twenty3.TextTransparency=0
		twenty3.BackgroundTransparency=0
		twenty4.TextTransparency=0
		twenty4.BackgroundTransparency=0
	end
	pgtl.Text = "Page 2/2"
	end
	end

newp.MouseButton1Down:connect(onClick)


oldp=Instance.new('TextButton',cmdframe)
oldp.Text = "<"
oldp.TextColor3 = Color3.new(255,255,255)
oldp.TextScaled = true
oldp:TweenSize(UDim2.new(0,100,0,30),'Out','Quad',0.35)
oldp:TweenPosition(UDim2.new(0,25,0,315),'Out','Quad',0.35)

function onClick()
	for i,v in pairs(sf:children()) do if v.ClassName=="TextLabel" then
		v.TextTransparency = 0
		v.BackgroundTransparency = 0
	end
	pgtl.Text = "Page 1/2"
		twenty2.TextTransparency=1
		twenty2.BackgroundTransparency=1
		twenty3.TextTransparency=1
		twenty3.BackgroundTransparency=1
		twenty4.TextTransparency=1
		twenty4.BackgroundTransparency=1
	end
	end

oldp.MouseButton1Down:connect(onClick)

pgtl=Instance.new('TextLabel',cmdframe)
pgtl.Text = "Page 1/2"
pgtl:TweenSize(UDim2.new(0,100,0,30),'Out','Quad',0.35)
pgtl.TextScaled = true
pgtl.BackgroundTransparency=1
pgtl.TextColor3 = Color3.new(255,255,255)
pgtl.TextStrokeTransparency = 0
pgtl:TweenPosition(UDim2.new(0,200,0,315),'Out','Quad',0.35)
	end
end
v.Chatted:connect(OnChatted)
end
-----------------------------------------------------------------

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
if Chat == true then
 				game:GetService("Chat"):Chat(wpad,chatname.."Exploded "..v.Name..".",Enum.ChatColor.Blue)
  end
  end);
    cmd("complex", {"ungod"}, "player", function(v)
     vhum1 = v.Character:FindFirstChild('Humanoid')
 	vhum1.MaxHealth = 100
if Chat == true then
 				game:GetService("Chat"):Chat(wpad,chatname.."UnGoded "..v.Name..".",Enum.ChatColor.Blue)
  end
  end);
    cmd("complex", {"kill"}, "player", function(v)
     v.Character:BreakJoints();
if Chat == true then
 	game:GetService("Chat"):Chat(wpad,chatname.."killed "..v.Name..".",Enum.ChatColor.Blue)
    end
end);
    cmd("complex", {"freeze"}, "player", function(v)
	if Chat == true then
 	game:GetService("Chat"):Chat(wpad,chatname.."Froze "..v.Name..".",Enum.ChatColor.Blue)
     end
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
if Chat == true then
 	game:GetService("Chat"):Chat(wpad,chatname.."Thawed "..v.Name..".",Enum.ChatColor.Blue)
 end
game.Debriss:AddItem(di,3)
 end);
    cmd("complex", {"god"}, "player", function(v)
     vhum = v.Character:FindFirstChild('Humanoid')
 	vhum.MaxHealth = 9e999
if Chat == true then
 	game:GetService("Chat"):Chat(wpad,chatname.."Godded "..v.Name..".",Enum.ChatColor.Blue)
   end
 end);
  cmd("complex", {"bsod","lag"}, "player", function(v)
	if Chat == true then
 	 	game:GetService("Chat"):Chat(wpad,chatname.."BSOD'd/Lagged "..v.Name..".",Enum.ChatColor.Blue)
end
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
if Chat == true then
 	game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." a forcefield.",Enum.ChatColor.Blue)
   end
 end);
    cmd("complex", {"kick","boot"}, "player", function(v)
 	v:remove()
if Chat == true then
 		game:GetService("Chat"):Chat(wpad,chatname.."kicked "..v.Name.." from the server.",Enum.ChatColor.Blue)
 end
   end);
    cmd("complex", {"unban","unbanish"}, "player", function(v)
	for i,unban in pairs(game.Players:children()) do
		if unban.ClassName=="StringValue" then
			game.Debris:AddItem(unban,0)
		end
	end
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
	if Chat == true then
 		game:GetService("Chat"):Chat(wpad,chatname.."Banished "..v.Name.." from the server.",Enum.ChatColor.Blue)
  end
  end);
   cmd("complex", {"sword","linkedsword"}, "player", function(v)
 game:service'InsertService':LoadAsset(125013769):children()[1].Parent = v.Backpack
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname..v.Name.." has no Gravity.",Enum.ChatColor.Blue)
   end
 end);
   cmd("complex", {"nogravity","ngrav","nograv"}, "player", function(v)
bf = Instance.new("BodyForce")	
bf.Parent =	v.Character.Torso	
bf.force = Vector3.new(0,4000,0)	
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." anti-Gravity.",Enum.ChatColor.Blue)
    end
end);
  cmd("complex", {"grav","gravity"}, "player", function(v)
for i,rbf in pairs(v.Character.Torso:children()) do if rbf.ClassName=="BodyForce" then
		game.Debris:AddItem(rbf,0)
	end
	end
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname..v.Name.." has Gravity.",Enum.ChatColor.Blue)
   end
 end);
   cmd("complex", {"unjail","nojail"}, "player", function(v)
game.Debris:AddItem(jailp,0)
game.Debris:AddItem(jailp1,0)
 		game:GetService("Chat"):Chat(wpad,chatname.."Unjailed "..v.Name..".",Enum.ChatColor.Blue)
    end);
   cmd("complex", {"light","plight"}, "player", function(v)
	if Chat == true then
	game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." light.",Enum.ChatColor.Blue)
	end
	light=Instance.new('PointLight',v.Character.Torso)
	light.Brightness = "5"
	light.Range "5"
    end);
  cmd("complex", {"rlight","nolight","unlight"}, "player", function(v)
	if Chat == true then
	game:GetService("Chat"):Chat(wpad,chatname.."Removed "..v.Name.." light.",Enum.ChatColor.Blue)
	end
	for i,rlight in pairs(v.Character.Torso:children()) do if rlight.ClassName=="PointLight" then
		game.Debris:AddItem(rlight,0)
	end
	end
    end);
   cmd("complex", {"resp","respawn","res"}, "player", function(v)
v:LoadCharacter()
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Respawned "..v.Name..".",Enum.ChatColor.Blue)
    end
end);
  cmd("complex", {"sit"}, "player", function(v)
v.Character.Humanoid.Sit = true
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Made "..v.Name.." sit.",Enum.ChatColor.Blue)
end
    end);
 cmd("complex", {"jump"}, "player", function(v)
v.Character.Humanoid.Jump = true
 		if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Made "..v.Name.." Jump.",Enum.ChatColor.Blue)
    end
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
 			if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Taken "..v.Name.." forcefield away.",Enum.ChatColor.Blue)
end
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
if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname.."Welcome "..meplyr.Name..", the current prefix is none!",Enum.ChatColor.Blue)
 end
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
if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has joined!',Enum.ChatColor.Blue)
end
end)

game.Players.PlayerRemoving:connect(function(player)
	if Chat == true then
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has left!',Enum.ChatColor.Blue)
end
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
