# Cross-server-Matchmaking
GUI SCRIPT OF JOINING AND LEAVING : 
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

local player = Players.LocalPlayer
local gui = script.Parent

-- Get UI elements
local joinBtn = gui:WaitForChild("JoinButton")
local leaveBtn = gui:WaitForChild("LeaveButton")
local statusLabel = gui:WaitForChild("Status")

-- RemoteEvents
local JoinEvent = ReplicatedStorage:WaitForChild("JoinMatchmaking")
local LeaveEvent = ReplicatedStorage:WaitForChild("LeaveMatchmaking")
local TeleportEvent = ReplicatedStorage:WaitForChild("TeleportPlayers")

joinBtn.MouseButton1Click:Connect(function()
	statusLabel.Text = "Searching for match..."
	JoinEvent:FireServer()
end)

leaveBtn.MouseButton1Click:Connect(function()
	statusLabel.Text = "Left the queue"
	LeaveEvent:FireServer()
end)

TeleportEvent.OnClientEvent:Connect(function()
	statusLabel.Text = "Teleporting..."
end)
