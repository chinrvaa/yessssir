local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()
local TextService = game:GetService("TextService")
local library = {flags = {}}

local function tweenObject(object, data, time)
	local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Sine, Enum.EasingDirection.Out)
	local tween = TweenService:Create(object, tweenInfo, data)
	tween:Play()
	return tween
end

local http = game:GetService("HttpService")

if not isfile("epicthing.config") then 
    writefile("epicthing.config", tostring(http:JSONEncode({})))
end

local function GetSetting(name)
    if not isfile("epicthing.config") then 
        writefile("epicthing.config", tostring(http:JSONEncode({})))
    end
    local content = readfile("epicthing.config")
    local parsed = http:JSONDecode(content)
	name = name:gsub("%s+", "")
    if parsed[tostring(game.GameId)] and parsed[tostring(game.GameId)][name] then 
		return parsed[tostring(game.GameId)][name] 
    end
end

local function AddSetting(name, value)
    if not isfile("epicthing.config") then 
        writefile("epicthing.config", tostring(http:JSONEncode({})))
    end
	
    local content = readfile("epicthing.config")
    local parsed = http:JSONDecode(content)
    if not parsed[tostring(game.GameId)] then 
        parsed[tostring(game.GameId)] = {}
    end 
    parsed[tostring(game.GameId)][name:gsub("%s+", "")] = value 
    writefile("epicthing.config", tostring(http:JSONEncode(parsed)))
end

function library:Window(TitleWhite)
	if game.CoreGui:FindFirstChild("BloxburgUi") then
		game.CoreGui:FindFirstChild("BloxburgUi"):Destroy()
	end
	local BloxburgUi = Instance.new("ScreenGui")
	local MainUIFrame = Instance.new("ImageLabel")
	local Cool = Instance.new("ImageLabel")
	local BloxburgCool = Instance.new("Frame")
	local TabsHolder = Instance.new("ImageLabel")
	local UIListLayout = Instance.new("UIListLayout")
	local UIPadding = Instance.new("UIPadding")
	local BloxburgTitle1 = Instance.new("Frame")
	local BloxburgTitle = Instance.new("TextLabel")
	local BloxburgHubTitle = Instance.new("TextLabel")
	BloxburgUi.Name = "BloxburgUi"
	BloxburgUi.Parent = game:GetService("CoreGui")
	BloxburgUi.DisplayOrder = 1
	MainUIFrame.Name = "MainUIFrame"
	MainUIFrame.Parent = BloxburgUi
	MainUIFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	MainUIFrame.BackgroundTransparency = 1.000
	MainUIFrame.Position = UDim2.new(0.252025217, 0, 0.226720661, 0)
	MainUIFrame.Size = UDim2.new(0, 551, 0, 404)
	MainUIFrame.Image = "rbxassetid://3570695787"
	MainUIFrame.ImageColor3 = Color3.fromRGB(22, 22, 22)
	MainUIFrame.ScaleType = Enum.ScaleType.Slice
	MainUIFrame.SliceCenter = Rect.new(100, 100, 100, 100)
	MainUIFrame.SliceScale = 0.050
	Cool.Name = "Cool"
	Cool.Parent = MainUIFrame
	Cool.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Cool.BackgroundTransparency = 1.000
	Cool.Position = UDim2.new(0.065, 0, 0.025, 0)
	Cool.Size = UDim2.new(0, 55, 0, 55)
	Cool.ZIndex = 2
	Cool.Image = "rbxassetid://166652117"
	BloxburgCool.Name = "BloxburgCool"
	BloxburgCool.Parent = MainUIFrame
	BloxburgCool.BackgroundColor3 = Color3.fromRGB(24, 24, 24)
	BloxburgCool.BorderSizePixel = 0
	BloxburgCool.Size = UDim2.new(0, 125, 0, 97)
	TabsHolder.Name = "TabsHolder"
	TabsHolder.Parent = MainUIFrame
	TabsHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	TabsHolder.BackgroundTransparency = 1.000
	TabsHolder.Position = UDim2.new(0, 0, 0.25, 0)
	TabsHolder.Size = UDim2.new(0, 125, 0, 300)
	TabsHolder.Image = "rbxassetid://3570695787"
	TabsHolder.ImageColor3 = Color3.fromRGB(24, 24, 24)
	TabsHolder.ScaleType = Enum.ScaleType.Slice
	TabsHolder.SliceCenter = Rect.new(100, 100, 100, 100)
	TabsHolder.SliceScale = 0.050
	BloxburgTitle1.Name = "BloxburgTitle"
	BloxburgTitle1.Parent = MainUIFrame
	BloxburgTitle1.BackgroundColor3 = Color3.fromRGB(19, 19, 19)
	BloxburgTitle1.BorderSizePixel = 0
	BloxburgTitle1.Position = UDim2.new(0.226860255, 0, 0, 0)
	BloxburgTitle1.Size = UDim2.new(0, 426, 0, 35)
	BloxburgTitle.Name = "BloxburgTitle"
	BloxburgTitle.Parent = BloxburgTitle1
	BloxburgTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	BloxburgTitle.BackgroundTransparency = 1.000
	BloxburgTitle.BorderColor3 = Color3.fromRGB(27, 42, 53)
	BloxburgTitle.Position = UDim2.new(0.0148883378, 0, 0, 0)
	BloxburgTitle.Size = UDim2.new(0, 420, 0, 35)
	BloxburgTitle.Font = Enum.Font.GothamBold
	BloxburgTitle.Text = TitleWhite
	BloxburgTitle.TextColor3 = Color3.fromRGB(233, 233, 233)
	BloxburgTitle.TextSize = 15.000
	BloxburgTitle.TextXAlignment = Enum.TextXAlignment.Left
	BloxburgHubTitle.Name = "BloxburgHubTitle"
	BloxburgHubTitle.Parent = MainUIFrame
	BloxburgHubTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	BloxburgHubTitle.BackgroundTransparency = 1.000
	BloxburgHubTitle.Position = UDim2.new(0.038, 0, 0.16, 0)
	BloxburgHubTitle.Size = UDim2.new(0, 372, 0, 35)
	BloxburgHubTitle.Font = Enum.Font.GothamBold
	BloxburgHubTitle.Text = "chims autoplayer"
	BloxburgHubTitle.TextColor3 = Color3.fromRGB(84, 116, 224)
	BloxburgHubTitle.TextSize = 15.000
	BloxburgHubTitle.TextXAlignment = Enum.TextXAlignment.Left
	UIListLayout.Parent = TabsHolder
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIPadding.Parent = TabsHolder
	local MainUITabPickedHolder = Instance.new("Frame")
	MainUITabPickedHolder.Name = "MainUITabPickedHolder"
	MainUITabPickedHolder.Parent = MainUIFrame
	MainUITabPickedHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	MainUITabPickedHolder.BackgroundTransparency = 1.000
	MainUITabPickedHolder.Position = UDim2.new(0.226860255, 0, 0.0866336599, 0)
	MainUITabPickedHolder.Size = UDim2.new(0, 426, 0, 369)
	local connections = {}

	MainUIFrame.InputBegan:connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 then
			local InitialPos = input.Position
			local InitialFramePos = MainUIFrame.Position
			connections.MouseMoved = UserInputService.InputChanged:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseMovement then
					local delta = input.Position - InitialPos
					tweenObject(MainUIFrame, {
						Position = UDim2.new(InitialFramePos.X.Scale, InitialFramePos.X.Offset + delta.X, InitialFramePos.Y.Scale, InitialFramePos.Y.Offset + delta.Y)
					}, 0.1)
				end
			end)
			MainUIFrame.InputEnded:connect(function(Input)
				if Input.UserInputType == Enum.UserInputType.MouseButton1 then
					connections.MouseMoved:Disconnect()
				end
			end)
		end
	end)

	local opened = true

	UserInputService.InputBegan:Connect(function(input)
		if input.KeyCode == Enum.KeyCode.RightControl then
			if opened == true then
				if MainUIFrame.Parent ~= nil then
					MainUIFrame.ClipsDescendants = true
					MainUIFrame:TweenSize(UDim2.new(0, 0, 0, 404), Enum.EasingDirection.In, Enum.EasingStyle.Linear, 0.5, true)
					opened = false
					wait(0.5)
				end
			elseif opened == false then
				if MainUIFrame.Parent ~= nil then
					MainUIFrame:TweenSize(UDim2.new(0, 551, 0, 404), Enum.EasingDirection.Out, Enum.EasingStyle.Linear, 0.5, true)
					opened = true
					wait(0.5)
					MainUIFrame.ClipsDescendants = false
				end
			end
		end
	end)

	local window = {}
	function window:Notification(Type, content, callback)
		if Type == "Message" then
			local NotificationMain = Instance.new("ImageLabel")
			local NotificationDropShadow = Instance.new("ImageLabel")
			local NotificationTitleHodler = Instance.new("Frame")
			local NotificationTitle = Instance.new("TextLabel")
			local NotificationCool = Instance.new("ImageLabel")
			local NotificationText = Instance.new("TextLabel")
			local NotificationOkay = Instance.new("TextButton")
			NotificationMain.Name = "NotificationMain"
			NotificationMain.Parent = BloxburgUi
			NotificationMain.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			NotificationMain.BackgroundTransparency = 1.000
			NotificationMain.Position = UDim2.new(-0.3, 0, 0.775, 0)
			tweenObject(NotificationMain, {
				Position = UDim2.new(0.015, 0, 0.775, 0)
			}, 0.5)
			NotificationMain.Size = UDim2.new(0, 268, 0, 124)
			NotificationMain.Image = "rbxassetid://3570695787"
			NotificationMain.ImageColor3 = Color3.fromRGB(22, 22, 22)
			NotificationMain.ScaleType = Enum.ScaleType.Slice
			NotificationMain.SliceCenter = Rect.new(100, 100, 100, 100)
			NotificationMain.SliceScale = 0.050
			NotificationDropShadow.Name = "NotificationDropShadow"
			NotificationDropShadow.Parent = NotificationMain
			NotificationDropShadow.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			NotificationDropShadow.BackgroundTransparency = 1.000
			NotificationDropShadow.Position = UDim2.new(-0.315028518, 0, -0.540322602, 0)
			NotificationDropShadow.Size = UDim2.new(0, 442, 0, 258)
			NotificationDropShadow.ZIndex = -1
			NotificationDropShadow.Image = "rbxassetid://5089202498"
			NotificationTitleHodler.Name = "NotificationTitleHodler"
			NotificationTitleHodler.Parent = NotificationMain
			NotificationTitleHodler.BackgroundColor3 = Color3.fromRGB(14, 14, 14)
			NotificationTitleHodler.BorderSizePixel = 0
			NotificationTitleHodler.Size = UDim2.new(0, 268, 0, 31)
			NotificationTitle.Name = "NotificationTitle"
			NotificationTitle.Parent = NotificationTitleHodler
			NotificationTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			NotificationTitle.BackgroundTransparency = 1.000
			NotificationTitle.Position = UDim2.new(0.0261194035, 0, 0, 0)
			NotificationTitle.Size = UDim2.new(0, 261, 0, 31)
			NotificationTitle.Font = Enum.Font.GothamSemibold
			NotificationTitle.Text = "Notification"
			NotificationTitle.TextColor3 = Color3.fromRGB(233, 233, 233)
			NotificationTitle.TextSize = 14.000
			NotificationTitle.TextXAlignment = Enum.TextXAlignment.Left
			NotificationCool.Name = "NotificationCool"
			NotificationCool.Parent = NotificationTitleHodler
			NotificationCool.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			NotificationCool.BackgroundTra…
