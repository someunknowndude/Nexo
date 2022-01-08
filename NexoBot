HumanDied = false

plr = game.Players.LocalPlayer
char=plr.Character
hum=char.Humanoid
ct={}
te=table.insert
srv=game:GetService('RunService')
m=plr:GetMouse()

for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
if v:IsA("BasePart") then 
te(ct,game:GetService("RunService").Heartbeat:connect(function()
pcall(function()
v.Velocity = Vector3.new(0,-40,0)
game.Players.LocalPlayer.ReplicationFocus=workspace
sethiddenproperty(game.Players.LocalPlayer,"MaximumSimulationRadius",math.huge)
sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",9e9)
end)
end))
end
end

char.Archivable=true

function nm(p)
for i,v in next, p:GetDescendants() do
if v:IsA('Mesh') or v:IsA('SpecialMesh') then
v:Remove()
end
end
end

function nc(p)
if p:IsA('BasePart') or p:IsA('Part') then
te(ct,srv.RenderStepped:Connect(function()
p.CanCollide=false
end))
te(ct,srv.Stepped:Connect(function()
p.CanCollide=false
end))
else
print('Cannot noclip '..p)
end
end

fl=Instance.new('Folder',char);fl.Name='XenCreation'

local reanim = char:Clone()
reanim.Name='BotReanimate'
reanim.Animate.Disabled=_G.CustomAnimations

hum:ChangeState('Physics') -- Limbs Collider

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

function Pos(part, parent, p)
Instance.new("Attachment",part)
Instance.new("AlignPosition",part)
Instance.new("Attachment",parent)
part.Attachment.Name = part.Name
parent.Attachment.Name = part.Name
part.AlignPosition.Attachment0 = part[part.Name]
part.AlignPosition.Attachment1 = parent[part.Name]
parent[part.Name].Position = p or Vector3.new()
part.AlignPosition.MaxForce = 999999999*10
part.AlignPosition.MaxVelocity = math.huge
part.AlignPosition.ReactionForceEnabled = false
part.AlignPosition.Responsiveness = math.huge
part.AlignPosition.RigidityEnabled = false
end

for i,v in next, reanim:GetDescendants() do
if v:IsA('BasePart') or v:IsA('Decal') then
v.Transparency = 1
end
end

for i,v in next, char:GetDescendants() do
if v:IsA('BasePart') then
nc(v)
end
end

for i,v in next, char:GetDescendants() do
if v:IsA('Accessory') then
v.Handle:BreakJoints()
create(v.Handle,reanim[v.Name].Handle)
end
end

reanim.Parent=fl

for i,v in next, reanim:GetDescendants() do
if v:IsA('BasePart') then
nc(v)
end
end

for i,v in next, char.Humanoid:GetPlayingAnimationTracks() do
v:Stop()
end
char.Animate:Remove()

Parts={
T=reanim['SeeMonkey'].Handle or reanim['HearMonkey'].Handle,
RA=reanim['Pal Hair'].Handle,
LA=reanim['Pink Hair'].Handle,
RL=reanim['LavanderHair'].Handle,
LL=reanim['Hat1'].Handle
}

for _,v in pairs(Parts) do
v.AccessoryWeld.C0=CFrame.Angles(math.rad(90),math.rad(0),math.rad(0))
v.AccessoryWeld.C1=CFrame.new()
nm(char[v.Parent.Name].Handle)
end

Parts.T.AccessoryWeld.Part1=reanim.Torso
Parts.RA.AccessoryWeld.Part1=reanim['Right Arm']
Parts.LA.AccessoryWeld.Part1=reanim['Left Arm']
Parts.RL.AccessoryWeld.Part1=reanim['Right Leg']
Parts.LL.AccessoryWeld.Part1=reanim['Left Leg']

function fix(p)
fixer=Instance.new('BodyPosition',p)
fixer.Name='BP'
fixer.P=9e9
fixer.D=9e9
fixer.MaxForce=Vector3.new(99999,99999,99999)
end

function flinger(p)
f=Instance.new('BodyAngularVelocity',p)
f.AngularVelocity = Vector3.new(9e9*10,9e9*10,9e9*10)
f.MaxTorque=Vector3.new(9e9*10,0,0)
end

tc=Instance.new('Part')
tc.CFrame=char.Torso.CFrame*CFrame.new(0,0,-5)
tc.Anchored=true
tc.Transparency=1
tc.Name='Anchor'
tc.CanCollide=false
tc.Parent=char

if _G.Fling then
click=false
create(char.HumanoidRootPart,tc)
char['Right Arm']:Destroy()
char['Right Leg']:Destroy()
char['Left Leg']:Destroy()
char.Torso['Left Shoulder']:Destroy()
char['Left Arm']:BreakJoints()
fix(char['Left Arm'])
Pos(char['Left Arm'],reanim.Torso)
if _G.ClickFling then
te(ct,m.Button1Down:Connect(function()
click=true
end))
te(ct,m.Button1Up:Connect(function()
click=false
end))
end
te(ct,srv.Heartbeat:Connect(function()
if click == true then
char['Left Arm'].BP.Position=m.Hit.p
char['Left Arm'].Position=m.Hit.p
else
char['Left Arm'].BP.Position=reanim.Torso.Position
char['Left Arm'].Position=reanim.Torso.Position
end
end))
flinger(char['Left Arm'])
else
create(char.HumanoidRootPart,tc)
char['Left Arm']:BreakJoints()
create(char['Left Arm'],reanim['Torso'],Vector3.new(),Vector3.new(0,0,90))
end

chatted=false

if _G.BotChat then
te(ct,plr.Chatted:Connect(function(e)
chatted=true
wait(8)
chatted=false
end))
end

te(ct,srv.Heartbeat:Connect(function()
if chatted then
char.HumanoidRootPart.CFrame=reanim.Torso.CFrame
elseif chatted == false then
char.HumanoidRootPart.CFrame=tc.CFrame
end
end))

if _G.FollowCamera then
te(ct,srv.Stepped:Connect(function()
reanim.Humanoid.CameraOffset = Vector3.new(0, reanim.Torso.Position.Y - reanim.Humanoid.RootPart.Position.Y, 0)
end))
end

plr.Character=reanim
workspace.CurrentCamera.CameraSubject=reanim.Humanoid

old=nil

te(ct,reanim.Humanoid.Died:Connect(function()
reanim.HumanoidRootPart.Anchored=true
old=reanim.HumanoidRootPart.CFrame
reanim.HumanoidRootPart.CFrame=old
wait()
reanim.HumanoidRootPart.CFrame=old
plr.Character=char
char:BreakJoints()
tc:Destroy()
HumanDied=true
game.Players:Chat('-gr')
for i,v in next, ct do v:Disconnect() end
end))
