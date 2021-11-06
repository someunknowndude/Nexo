HumanDied = false
for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
if v:IsA("BasePart") then 
game:GetService("RunService").Heartbeat:connect(function()
v.Velocity = Vector3.new(0,-25.05,0)
sethiddenproperty(game.Players.LocalPlayer,"MaximumSimulationRadius",math.huge)
sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",1.0000000331814e+32)
end)
end
end

local plr = game.Players.LocalPlayer
local Character = plr.Character
local Camera = workspace.CurrentCamera
local RunService = game:GetService("RunService")

Character.Archivable = true

RunService.Stepped:Connect(function()
for i,v in pairs(Character:GetChildren()) do
if v:IsA("BasePart") then
v.CanCollide = false
end
end
end)

local Rig = game:GetObjects("rbxassetid://5088298388")[1]
Rig.Parent = Character
Rig.HumanoidRootPart.CFrame = Character.HumanoidRootPart.CFrame
Rig.Name = "R6"

for i,v in next, Character.Humanoid:GetPlayingAnimationTracks() do
v:Stop()
Character.Animate:Remove()
end

for _, RigLimbs in next, Rig:GetDescendants() do
if RigLimbs:IsA("BasePart") then
RigLimbs.Transparency = 1
end
end

Character.LeftUpperArm.LeftShoulder:Remove()
Character.RightUpperArm.RightShoulder:Remove()
Character.LeftUpperLeg.LeftHip:Remove()
Character.RightUpperLeg.RightHip:Remove()

function create(part, parent, p, r)
Instance.new("Attachment",part)
Instance.new("AlignPosition",part)
Instance.new("AlignOrientation",part)
Instance.new("Attachment",parent)
part.Attachment.Name = "n"..part.Name
parent.Attachment.Name = "n"..part.Name
part.AlignPosition.Attachment0 = part["n"..part.Name]
part.AlignOrientation.Attachment0 = part["n"..part.Name]
part.AlignPosition.Attachment1 = parent["n"..part.Name]
part.AlignOrientation.Attachment1 = parent["n"..part.Name]
parent["n"..part.Name].Position = p or Vector3.new()
part["n"..part.Name].Orientation = r or Vector3.new()
part.AlignPosition.MaxForce = 999999999
part.AlignPosition.MaxVelocity = math.huge
part.AlignPosition.ReactionForceEnabled = false
part.AlignPosition.Responsiveness = math.huge
part.AlignOrientation.Responsiveness = math.huge
part.AlignPosition.RigidityEnabled = false
part.AlignOrientation.MaxTorque = 999999999
end

create(Character.UpperTorso,Rig['Torso'],Vector3.new(0,0.3,0))
create(Character.LeftUpperArm,Rig['Left Arm'],Vector3.new(0,0.5,0))
create(Character.RightUpperArm,Rig['Right Arm'],Vector3.new(0,0.5,0))
create(Character.LeftUpperLeg,Rig['Left Leg'],Vector3.new(0,0.6,0))
create(Character.RightUpperLeg,Rig['Right Leg'],Vector3.new(0,0.6,0))

for i,v in next, Character:GetDescendants() do
if v:IsA('Accessory') then
hatclone=v:Clone()
hatclone.Parent = Rig
hatclone.Handle.Transparency = 1
v.Handle:BreakJoints()
create(v.Handle,Rig[v.Name].Handle)
if hatclone.Handle.AccessoryWeld.Part0 == Character.Head then
hatclone.Handle.AccessoryWeld.Part0 = Rig.Head
end
end
end

local ct = {}

table.insert(ct,Rig.Humanoid.Died:Connect(function()
for i,v in pairs(ct) do v:Disconnect() end
plr.Character = Character
plr.Character.Head:Remove()
Camera.CameraSubject = Character.Humanoid
reanimated = false
HumanDied = true
end))

table.insert(ct,Character.Humanoid.Died:Connect(function()
for i,v in pairs(ct) do v:Disconnect() end
plr.Character = Character
plr.Character.Head:Remove()
Camera.CameraSubject = Character.Humanoid
reanimated = false
HumanDied = true
end))

plr.Character = Rig
Camera.CameraSubject = Rig.Humanoid
