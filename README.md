local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()

local X = Material.Load({
	Title = "💗 Anime Girl RNG 💫",
	Style = 2,
	SizeX = 350,
	SizeY = 380,
	Theme = "Dark",
	ColorOverrides = {
		MainFrame = Color3.fromRGB(0,9,55)
	}
})

local Roll = X.New({
	Title = "Main"
})
Roll.Toggle({
Text = "Auto Fast Summon",
Callback = function(Value)
_G.roll = Value
while _G.roll do
task.wait(0.1)
local args = {
    [1] = math.huge
}

game:GetService("ReplicatedStorage"):WaitForChild("CORE_RemoteEvents"):WaitForChild("SendSummonRequest"):FireServer(unpack(args))
end
end,
Enabled = false
})
local Pot = X.New({
	Title = "Potion"
})
Pot.Dropdown({
	Text = "Select Potion!",
	Callback = function(t)
        potion = t
	end,
	Options = {
		"Petal Ooze",
		"Gilster Glow",
		"Rosy Rapture",
		"Azure Mist",
		"Weak Starpurge",
		"Plum Purity",
		"Ruby Respite",
		"De Nago",
		"Buttermilk",
		"Ashen Silver",
		"De Nesaria",
		"Starpurge",
		"Fuchsia Fizz",
		"Cerulean",
		"Ray Remedy",
		"Blossom Burst",
		"Viridian Veil",
		"Hyper Haze",
		"Vermillion",
		"Radiance",
		"Isis Ambrosia",
		"Death Wish",
		"Verdant Vigor",
		"Sunburst",
		"Shimmer",
		"Broken Dreams",
		"Mega Shimmer",
		"Devil's Deal",
		"Mega Sunburst",
		
	},
})
Pot.Toggle({
Text = "Auto [Buy And Use]",
Callback = function(Value)
_G.Ro = Value
while _G.Ro do
task.wait(1)
local args = {
    [1] = potion
}

game:GetService("ReplicatedStorage"):WaitForChild("CORE_RemoteEvents"):WaitForChild("SendPurchaseRequest"):FireServer(unpack(args))
wait(0.1)
local args = {
    [1] = "use_potion",
    [2] = potion
}

game:GetService("ReplicatedStorage"):WaitForChild("CORE_RemoteEvents"):WaitForChild("SendEquipRequest"):FireServer(unpack(args))
end
end,
Enabled = false
})
