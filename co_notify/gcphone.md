# CONFIGURACION DEL GCPHONE 

Este script esta diseñado para el gcphone más utilizado (Crewphone), si sus desencadenantes tienen un texto diferente en sus nombres, debe encontrar las lineas ustedes mismos. 
 
[client/youtube.lua] CONFIGURACION DE YOUTUBE
"youtube_Play" Buscar el trigger y poner el Siguiente codigo en el
```lua
RegisterNUICallback('youtube_Play', function(data)
    exports['co_notify']:SendNotify('youtube', data, "true") --CODIGO PARA AÑADIR
end)
```

[client/client.lua] CONFIGURACION DE MENSAJE ENTRANTE
"gcPhone:receiveMessage" Buscar el trigger,  if message.owner == 0 then Agregar justo debato
 ```lua
 if message.owner == 0 then
    exports['co_notify']:SendNotify('mesaj', message.transmitter.." Has recibido un Mensaje.", message.message) --CODIGO PARA AÑADIR
```



[server/twitter.lua] CONFIGURACION DE PUBLICACION ENTRANTE DE TWITTER
"gcPhone:twitter_postTweets" Buscar el trigger, local srcIdentifier = getPlayerID(source)' --Agregar los codigos a continuacion despues de.
 ```lua
	local xPlayer = ESX.GetPlayerFromId(source)
	local players = GetPlayers()

    for _, i in ipairs(players) do
	      TriggerClientEvent('co_notify:client:SendNotifys', i, { app = "twitter" , title = "@"..xPlayer.getName(), content = message , source = i })
	end
```
Es necesario mirar directamente en
 ```lua
    local sourcePlayer = tonumber(source)
    local srcIdentifier = getPlayerID(source)
    local xPlayer = ESX.GetPlayerFromId(source)
    local players = GetPlayers()
    for _, i in ipairs(players) do
	      TriggerClientEvent('co_notify:client:SendNotifys', i, { app = "twitter" , title = "@"..xPlayer.getName(), content = message , source = i })
	end
    TwitterPostTweet(message, image, sourcePlayer, srcIdentifier)
```


Haga lo mismo que en Twitter para las Paginas Amarillas, la logica es exactamente la misma, Nombre del trigger a buscar: "gcPhone:yellow_postIlan", dosya [server/yellowpages.lua]
