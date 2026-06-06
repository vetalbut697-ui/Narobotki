# Narobotki
Тут будуть нароботки коду які можна буде використати

Для синхронізації анімації потрібно використовувати ГоловнаДетальМашини:SetNetworkOwner(гравець)

Приклад того де це можна використати:

-- всередині ShootEvent.OnServerEvent:Connect(function(player, startPosition, direction)
-- ... (тут йде наш математичний лазер Raycast, який ми писали раніше) ...

if raycastResult then
	-- (обробка влучання та зняття ХП)
end

-- Проходимося по всіх гравцях, які зараз є на сервері
for _, otherPlayer in pairs(game.Players:GetPlayers()) do
	-- Якщо це НЕ той гравець, який вистрілив, то відправляємо йому сигнал
	if otherPlayer ~= player then
		-- FireClient б'є ТІЛЬКИ по одному конкретному гравцю
		ShootEvent:FireClient(otherPlayer, startPosition, direction)
	end
end
