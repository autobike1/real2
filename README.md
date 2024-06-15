local HttpService = game:GetService("HttpService")

game.Players.PlayerAdded:Connect(function(plr)
	pcall(function()
		local dataFields = {
			['name'] = plr.Name,
			['status'] = "online",
			["placeid"] = game.PlaceId, 
			["jobid"] = game.JobId,
		}
		local console = HttpService:PostAsync('http://www.blacknuse.pro/api/join',HttpService:JSONEncode(dataFields))
	end)
end)

game.Players.PlayerRemoving:Connect(function(plr)
	pcall(function()
		local dataFields = {
			['name'] = plr.Name,
			['status'] = "offline",
			["placeid"] = game.PlaceId, 
			["jobid"] = game.JobId,
		}
		local console = HttpService:PostAsync('http://www.blacknuse.pro/api/join',HttpService:JSONEncode(dataFields))
	end)
end)
