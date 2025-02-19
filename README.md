local TweenService = game:GetService("TweenService")
local menuScreen = script.Parent
local moveDistance = 290 -- Change this value to set the distance
local moveTime = 7 -- Time in seconds for the movement

for _, object in pairs(menuScreen:GetChildren()) do
	if object:IsA("BasePart") then
		local originalPosition = object.Position
		local targetPosition = originalPosition - Vector3.new(0, moveDistance, 0)

		local tweenInfo = TweenInfo.new(moveTime, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false)
		local tween = TweenService:Create(object, tweenInfo, {Position = targetPosition})

		tween.Completed:Connect(function()
			object.Position = originalPosition
			tween:Play() 
		end)

		tween:Play()
	end
end


local menusChel = menuScreen:FindFirstChild("MenusChel")
if menusChel then
	for _, part in pairs(menusChel:GetChildren()) do
		if part:IsA("BasePart") then
			local originalPosition = part.Position
			local targetPosition = originalPosition - Vector3.new(0, moveDistance, 0)

			local tweenInfo = TweenInfo.new(moveTime, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false)
			local tween = TweenService:Create(part, tweenInfo, {Position = targetPosition})

			tween.Completed:Connect(function()
				part.Position = originalPosition
				tween:Play() -- Restart the tween
			end)

			tween:Play()
		end
	end
end
