adminwew = game.Players.LocalPlayer.Name
local admins = {"Basictality",adminwew}
print'works 1'
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
   cmd("complex", {"freeze"}, "player", function(v)
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
game.Debriss:AddItem(3,di)
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

player = game.Players.LocalPlayer
player.Chatted:connect(function(message) chat(message, player) end)

admin = game.Players.LocalPlayer.Name
wpad = Instance.new('Part',workspace)
wpad.Name = "Pad"
wpad.Anchored = true
wpad.CanCollide = false
wpad.FormFactor = "Custom"
wpad.Size = Vector3.new(2.5,3.5,0)
wpad.Material = "SmoothPlastic"
wpad.BrickColor = BrickColor.new'Lime green'
wpads=Instance.new('SelectionBox',wpad)
wpads.Adornee=wpad
wpad.Transparency=0.3
wpads.LineThickness = "0.0.1"
wpads.Color = BrickColor.new'Really black'
dis = "7"

		guiw=Instance.new("BillboardGui")
		guiw.Parent=wpad
		guiw.Adornee=wpad
		guiw.Size=UDim2.new(3,0,4,0)
		guiw.StudsOffset=Vector3.new(0,2,0)
		textw=Instance.new("TextLabel")
		textw.Text = "Welcome to Bas Pads, "..game.Players.LocalPlayer.Name..'!'
		textw.Size=UDim2.new(1.25,0,0.75,0)
		textw.Position=UDim2.new(-0.125,0,-0.25,0)
		textw.BackgroundTransparency = 1
		textw.FontSize = "Size28"
		textw.TextColor3 = Color3.new(255,255,255)
		textw.BorderSizePixel = 0
		textw.Parent=guiw
		
		cd=Instance.new("ClickDetector",wpad)
function onClicked(Player) do
if Player.Name == "Basictality"  then
wpad:remove()
end
end
end

while true do wait()
	for i = 0,360 do wait()
	wpad.CFrame = CFrame.new(workspace[admin].Torso.Position) * CFrame.fromEulerAnglesXYZ(0,math.rad(i),0) * CFrame.new(0,0,-dis) * CFrame.Angles(math.rad(i),math.rad(i),math.rad(i))
	end
	end
