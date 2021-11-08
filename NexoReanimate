HumanDied = false
for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
if v:IsA("BasePart") then 
game:GetService("RunService").Heartbeat:connect(function()
v.Velocity = Vector3.new(0,-30,0)
sethiddenproperty(game.Players.LocalPlayer,"MaximumSimulationRadius",math.huge)
sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",999999999)
end)
end
end

local plr = game.Players.LocalPlayer
local char = plr.Character
local srv = game:GetService('RunService')
local ct = {}

char.Archivable = true
local reanim = char:Clone()
reanim.Name = 'Nexo '..plr.Name..''
reanim.Parent = workspace
char.HumanoidRootPart:Destroy()

for i,v in next, char.Humanoid:GetPlayingAnimationTracks() do
v:Stop()
char.Animate:Remove()
end

function create(part, parent, p, r)
Instance.new("Attachment",part)
Instance.new("AlignPosition",part)
Instance.new("AlignOrientation",part)
Instance.new("Attachment",parent)
part.Attachment.Name = part.Name
parent.Attachment.Name = part.Name
part.AlignPosition.Attachment0 = part[part.Name]
part.AlignOrientation.Attachment0 = part[part.Name]
part.AlignPosition.Attachment1 = parent[part.Name]
part.AlignOrientation.Attachment1 = parent[part.Name]
parent[part.Name].Position = p or Vector3.new()
part[part.Name].Orientation = r or Vector3.new()
part.AlignPosition.MaxForce = 999999999
part.AlignPosition.MaxVelocity = math.huge
part.AlignPosition.ReactionForceEnabled = false
part.AlignPosition.Responsiveness = math.huge
part.AlignOrientation.Responsiveness = math.huge
part.AlignPosition.RigidityEnabled = false
part.AlignOrientation.MaxTorque = 999999999
end

for i,v in next, char:GetDescendants() do
if v:IsA('Accessory') then
v.Handle.AccessoryWeld:Remove()
create(v.Handle,reanim[v.Name].Handle)
end
end

char.Torso['Left Shoulder']:Destroy()
char.Torso['Right Shoulder']:Destroy()
char.Torso['Left Hip']:Destroy()
char.Torso['Right Hip']:Destroy()

create(char['Torso'],reanim['Torso'])
create(char['Left Arm'],reanim['Left Arm'])
create(char['Right Arm'],reanim['Right Arm'])
create(char['Left Leg'],reanim['Left Leg'])
create(char['Right Leg'],reanim['Right Leg'])

for i,v in next, reanim:GetDescendants() do if v:IsA('BasePart') or v:IsA('Decal') then v.Transparency = 1 end end

table.insert(ct,srv.RenderStepped:Connect(function()
for i,v in next, reanim:GetDescendants() do
if v:IsA('BasePart') then
v.CanCollide = false
end
end
end))

table.insert(ct,srv.Stepped:Connect(function()
for i,v in next, reanim:GetDescendants() do
if v:IsA('BasePart') then
v.CanCollide = false
end
end
end))

table.insert(ct,srv.RenderStepped:Connect(function()
for i,v in next, char:GetDescendants() do
if v:IsA('BasePart') then
v.CanCollide = false
end
end
end))

table.insert(ct,srv.Stepped:Connect(function()
for i,v in next, char:GetDescendants() do
if v:IsA('BasePart') then
v.CanCollide = false
end
end
end))

table.insert(ct,reanim.Humanoid.Died:Connect(function()
plr.Character = char
char:BreakJoints()
reanim:Destroy()
HumanDied = true
for _,v in pairs(ct) do v:Disconnect() end
end))

plr.Character = reanim
workspace.CurrentCamera.CameraSubject = reanim.Humanoid
