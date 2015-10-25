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
   cmd("complex", {"freeze"}, "player", function(v)
    freezes=Instance.new('Part',v.Character)
freezes.FormFactor = "Custom"
freezes.Size = Vector3.new(4.5,6.5,4.5)
freezes.Material = "SmoothPlastic"
freezes.BrickColor = BrickColor.new('Navy blue')
freezes.Transparency=0.5
freezes.Name = "Ice"
freezes.Anchored = true

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
di:remove()

v.Character.Head.Anchored = false
v.Character.Torso.Anchored = false
v.Character['Left Arm'].Anchored = false
v.Character['Left Leg'].Anchored = false
v.Character['Right Arm'].Anchored = false
v.Character['Right Leg'].Anchored = false
print'does it work'
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
