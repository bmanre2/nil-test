
    
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245

adminwew = game.Players.LocalPlayer.Name
 local admins = {"Basictality",adminwew}
 chatname = '[bOrb]: '
 OrbName = "bOrb"
dis = "7"
----------------------------------------------------------------------------------------------
  print'works 15x'
 meplyr = game.Players.LocalPlayer

 local isAdmin = function(p)
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
 		game:GetService("Chat"):Chat(wpad,chatname.."Gave "..v.Name.." a sword.",Enum.ChatColor.Blue)
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
 wpadmod.Name = player.Name.."'s "..OrbName
 wpad=Instance.new('Part',wpadmod)
 wpad.Name = "bOrb"
 wpad.Anchored = true
 wpadpointlight=Instance.new('PointLight',wpad)
 wpad.CanCollide = false
 wpad.FormFactor = "Custom"
 wpad.Shape = "Ball"
 wpad.CanCollide = false
 wpad.Size = Vector3.new(1,1,1)
 wpad.Material = "SmoothPlastic"
 wpad.BrickColor = BrickColor.new'Teal'
game:GetService("Chat"):Chat(wpad,chatname.."Welcome "..meplyr.Name..", the current prefix is  none!",Enum.ChatColor.Blue)
 end

Spawnorb()
--------------------------------Player Joining And Player Leaving------------------------------
game.Players.PlayerAdded:connect(function(player)
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has joined!',Enum.ChatColor.Blue)
end)

game.Players.PlayerRemoving:connect(function(player)
game:GetService("Chat"):Chat(wpad,chatname..player.Name..' has left!',Enum.ChatColor.Blue)
end)
-----------------------------------------Rot---------------------------------------------------
 while true do wait()
 	for i = 0,360 do wait()
 	wpad.CFrame = CFrame.new(workspace[admin].Torso.Position) * CFrame.fromEulerAnglesXYZ(math.rad(i),math.rad(i),math.rad(i)) * CFrame.new(0,0,-dis)
end
end
