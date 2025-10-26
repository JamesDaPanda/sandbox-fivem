![Logo](https://i.ibb.co/Tm01NWq/banner.png)

# Sandbox RP Framework

This is a heavily modified version of the Mythic Framework for Sandbox RP. It used to have  a custom component-based system - but now its using a fully custom exports system written from the bottom up with major improvements to make the framework run better, with all UIs built in React. This codebase is released with full permissions from the original Mythic Framework authors, Alzar & Dr. Nick.

---

## Dependencies

Ensure the following packages are installed:

| Package          | Download Link                                                                 |
| ---------------- | ---------------------------------------------------------------------------- |
| Node.js          | [Download Here](https://nodejs.org/en/download)                              |
| MariaDB          | [Download Here](https://mariadb.org/download/?t=mariadb&p=mariadb&r=12.0.2) (v12.0.2) |
| HeidiSQL         | [Download Here](https://www.heidisql.com/download.php) (**can be installed via MariaDB**) |
| Git for Windows  | [Download Here](https://git-scm.com/download/win)                            |
| Bun              | [Download Here](https://bun.sh)                                              |

---

## Prerequisites & Setup

1. **Download the Source Code**  
   Clone or download the repository from GitHub.

2. **Extract Files**  
   Extract the `sandbox-fivem` folder and open it.

3. **Download FiveM Artifact**  
   Download the latest FiveM Windows Artifact: [Download Here](https://artifacts.jgscripts.com).

4. **Set Up Artifact Folder**  
   - Create a new `artifact` folder in the root directory.
   - Move the downloaded artifact files into the `artifact` folder.

5. **Configure Database**  
   - Update `database.cfg` with the correct **HeidiSQL** information.

6. **Add CFX Key**  
   Add your `cfx` key to the `sv_licenseKey` field in the configuration.

---

## Importing Database

1. Open **HeidiSQL**.
2. Import the `database.sql` file.

---

## Launching the Server

1. **First-Time Setup**  
   - Launch the server using `./artifact/FXServer.exe`.
   - Follow the prompts to create a **txAdmin** username/password and link your FiveM account.

2. **Project Setup**  
   - Link the project to an existing project.
   - Set the file paths for the `.cfg` files.

3. **Enable OneSync**  
   - In **txAdmin**, enable `OneSync` for proper server functionality.
   - Restart the server.

4. **Errors**  
   - If you encounter any **errors** after completing the setup steps:  
     1. Restart the server.  
     2. Verify all configurations and file paths.  

![txAdmin](https://i.ibb.co/0yfp7Qt/txadmin.jpg)

---

## Admin Permissions

1. **Assign Roles**  
   Edit the `./config/permissions.cfg` file to assign roles such as `management`, `dev`, `admin`, or `operations`.

2. **Grant Global Admin**  
   To grant `management` permissions to all players, set `danger_everyone_is_admin` to `1` in `./config/core.ptr.cfg`.  
   **Warning:** This is highly discouraged for production environments as it poses significant security risks.

3. **Access Admin Tools**  
   Use `/admin` or `/staff` to access the admin tool.

---

## Logging

- **Discord Logging**  
  Logging works only in `production` mode. To enable logs on a development server, set the environment to `prod` in `core.ptr.cfg`.

---

## Support

If you enjoy this project and would like to support its continued development, any contribution is greatly appreciated! Your support helps keep this project alive and allows me to spend more time on it, as I've already invested countless hours into making this the best framework possible.

[![ko-fi](https://img.shields.io/badge/Support%20on%20Ko--fi-ff5e5b?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/autlaaw)

## Sandbox Exports List - Below is just a WIP - finished list coming soon
Rewrote Fetch Component > Exports
Client side:

COMPONENTS.Fetch:Player() > exports['sandbox-base']:FetchPlayer()
COMPONENTS.Fetch:Character() > exports['sandbox-base']:FetchCharacter()

Server side:

Fetch:Source(source) > exports['sandbox-base']:FetchSource(source)
Fetch:PlayerData(key, value) > exports['sandbox-base']:FetchPlayerData(key, value)
Fetch:Website(type, id) > exports['sandbox-base']:FetchWebsite(type, id)
Fetch:All() > exports['sandbox-base']:FetchAll()
Fetch:Count() > exports['sandbox-base']:FetchCount()

Other:

exports["sandbox-base"]:FetchComponent("Fetch"):Source(source) > exports['sandbox-base']:FetchSource(source)
exports["sandbox-base"]:FetchComponent("Fetch"):PlayerData(key, value) > exports['sandbox-base']:FetchPlayerData(key, value)
exports["sandbox-base"]:FetchComponent("Fetch"):Website(type, id) > exports['sandbox-base']:FetchWebsite(type, id)
exports["sandbox-base"]:FetchComponent("Fetch"):All() > exports['sandbox-base']:FetchAll()
exports["sandbox-base"]:FetchComponent("Fetch"):Count() > exports['sandbox-base']:FetchCount()

Character component extension:

Fetch:CharacterSource(source) > exports['sandbox-characters']:FetchCharacterSource(source)
Fetch:AllCharacters() > exports['sandbox-characters']:FetchAllCharacters()
Fetch:CharacterData(key, value) > exports['sandbox-characters']:FetchCharacterData(key, value)
Fetch:CountCharacters() > exports['sandbox-characters']:FetchCountCharacters()
Fetch:ID(value) > exports['sandbox-characters']:FetchByID(value)
Fetch:SID(value) > exports['sandbox-characters']:FetchBySID(value)
Fetch:GetOfflineData(stateId, key) > exports['sandbox-characters']:FetchGetOfflineData(stateId, key)

Rewrote Database Component > Exports
Game database:

Database.Game:isConnected() > exports['sandbox-base']:DatabaseGameIsConnected()
Database.Game:insert(params, callback) > exports['sandbox-base']:DatabaseGameInsert(params, callback)
Database.Game:insertOne(params, callback) > exports['sandbox-base']:DatabaseGameInsertOne(params, callback)
Database.Game:find(params, callback) > exports['sandbox-base']:DatabaseGameFind(params, callback)
Database.Game:findOne(params, callback) > exports['sandbox-base']:DatabaseGameFindOne(params, callback)
Database.Game:update(params, callback) > exports['sandbox-base']:DatabaseGameUpdate(params, callback)
Database.Game:updateOne(params, callback) > exports['sandbox-base']:DatabaseGameUpdateOne(params, callback)
Database.Game:delete(params, callback) > exports['sandbox-base']:DatabaseGameDelete(params, callback)
Database.Game:deleteOne(params, callback) > exports['sandbox-base']:DatabaseGameDeleteOne(params, callback)
Database.Game:findOneAndUpdate(params, callback) > exports['sandbox-base']:DatabaseGameFindOneAndUpdate(params, callback)
Database.Game:count(params, callback) > exports['sandbox-base']:DatabaseGameCount(params, callback)
Database.Game:aggregate(params, callback, stupidFlag) > exports['sandbox-base']:DatabaseGameAggregate(params, callback, stupidFlag)

Auth database:

Database.Auth:isConnected() > exports['sandbox-base']:DatabaseAuthIsConnected()
Database.Auth:insert(params, callback) > exports['sandbox-base']:DatabaseAuthInsert(params, callback)
Database.Auth:insertOne(params, callback) > exports['sandbox-base']:DatabaseAuthInsertOne(params, callback)
Database.Auth:find(params, callback) > exports['sandbox-base']:DatabaseAuthFind(params, callback)
Database.Auth:findOne(params, callback) > exports['sandbox-base']:DatabaseAuthFindOne(params, callback)
Database.Auth:update(params, callback) > exports['sandbox-base']:DatabaseAuthUpdate(params, callback)
Database.Auth:updateOne(params, callback) > exports['sandbox-base']:DatabaseAuthUpdateOne(params, callback)
Database.Auth:delete(params, callback) > exports['sandbox-base']:DatabaseAuthDelete(params, callback)
Database.Auth:deleteOne(params, callback) > exports['sandbox-base']:DatabaseAuthDeleteOne(params, callback)
Database.Auth:findOneAndUpdate(params, callback) > exports['sandbox-base']:DatabaseAuthFindOneAndUpdate(params, callback)
Database.Auth:count(params, callback) > exports['sandbox-base']:DatabaseAuthCount(params, callback)
Database.Auth:aggregate(params, callback) > exports['sandbox-base']:DatabaseAuthAggregate(params, callback)

Rewrote Callbacks Component > Exports
Client side:
Register Client Callback:

Callbacks:RegisterClientCallback("EventName", function(data, cb)
    -- callback logic
    cb(result)
end)
>
exports["sandbox-base"]:RegisterClientCallback("EventName", function(data, cb)
    -- callback logic
    cb(result)
end)

Call server from client:

Callbacks:ServerCallback("EventName", data, function(result)
    -- handle result
end)
>
exports["sandbox-base"]:ServerCallback("EventName", data, function(result)
    -- handle result
end)

Server side:
Register server callback:

Callbacks:RegisterServerCallback("EventName", function(source, data, cb)
    -- callback logic
    cb(result)
end)
>
exports["sandbox-base"]:RegisterServerCallback("EventName", function(source, data, cb)
    -- callback logic
    cb(result)
end)

Call client from server:

Callbacks:ClientCallback(source, "EventName", data, function(result)
    -- handle result
end)
>
exports["sandbox-base"]:ClientCallback(source, "EventName", data, function(result)
    -- handle result
end)

Rewrote Logger Component > Exports
Client side:
Logger:Trace(component, log, flags, data) > exports['sandbox-base']:LoggerTrace(component, log, flags, data)
Logger:Info(component, log, flags, data) > exports['sandbox-base']:LoggerInfo(component, log, flags, data)
Logger:Warn(component, log, flags, data) > exports['sandbox-base']:LoggerWarn(component, log, flags, data)
Logger:Error(component, log, flags, data) > exports['sandbox-base']:LoggerError(component, log, flags, data)
Logger:Critical(component, log, flags, data) > exports['sandbox-base']:LoggerCritical(component, log, flags, data)

Server side:
Logger:Trace(component, log, flags, data) > exports['sandbox-base']:LoggerTrace(component, log, flags, data)
Logger:Info(component, log, flags, data) > exports['sandbox-base']:LoggerInfo(component, log, flags, data)
Logger:Warn(component, log, flags, data) > exports['sandbox-base']:LoggerWarn(component, log, flags, data)
Logger:Error(component, log, flags, data) > exports['sandbox-base']:LoggerError(component, log, flags, data)
Logger:Critical(component, log, flags, data) > exports['sandbox-base']:LoggerCritical(component, log, flags, data)

Removed Logger:Log, shouldn't be used anymore

Rewrote Utils Component > Exports
Shared:

Utils:Print(t, s) > exports['sandbox-base']:UtilsPrint(t, s)
Utils:GetTableLength(t) > exports['sandbox-base']:UtilsGetTableLength(t)
Utils:GetTableKeys(t) > exports['sandbox-base']:UtilsGetTableKeys(t)
Utils:DoesTableHaveValue(t, val) > exports['sandbox-base']:UtilsDoesTableHaveValue(t, val)
Utils:Round(n, precision) > exports['sandbox-base']:UtilsRound(n, precision)
Utils:WeightedRandom(pool) > exports['sandbox-base']:UtilsWeightedRandom(pool)

Rewrote Game Component > Exports
Client side:

Game.Players:GetPlayerPeds() > exports['sandbox-base']:GamePlayersGetPlayerPeds()
Game.Players:GetClosestPlayer(coords) > exports['sandbox-base']:GamePlayersGetClosestPlayer(coords)
Game.Objects:GetAll() > exports['sandbox-base']:GameObjectsGetAll()
Game.Objects:GetInArea(coords, radius) > exports['sandbox-base']:GameObjectsGetInArea(coords, radius)
Game.Objects:Spawn(coords, modelName, heading, cb) > exports['sandbox-base']:GameObjectsSpawn(coords, modelName, heading, cb)
Game.Objects:SpawnLocal(coords, modelName, heading, cb) > exports['sandbox-base']:GameObjectsSpawnLocal(coords, modelName, heading, cb)
Game.Objects:SpawnLocalNoOffset(coords, modelName, heading, cb) > exports['sandbox-base']:GameObjectsSpawnLocalNoOffset(coords, modelName, heading, cb)
Game.Objects:Delete(obj) > exports['sandbox-base']:GameObjectsDelete(obj)
Game.Vehicles:Spawn(coords, modelName, heading, cb) > exports['sandbox-base']:GameVehiclesSpawn(coords, modelName, heading, cb)
Game.Vehicles:SpawnLocal(coords, modelName, heading, cb) > exports['sandbox-base']:GameVehiclesSpawnLocal(coords, modelName, heading, cb)
Game.Vehicles:Delete(vehicle) > exports['sandbox-base']:GameVehiclesDelete(vehicle)

Server side:

Game.Objects:Spawn(coords, modelName, heading) > exports['sandbox-base']:GameObjectsSpawn(coords, modelName, heading)
Game.Objects:Delete(obj) > exports['sandbox-base']:GameObjectsDelete(obj)

Rewrote Stream Component > Exports
COMPONENTS.Stream.RequestModel(model) > exports['sandbox-base']:StreamRequestModel(model)

COMPONENTS.Stream.RequestAnimDict()dictName > exports['sandbox-base']:StreamRequestAnimDict(dictName)

COMPONENTS.Stream.RequestAnimSet > exports['sandbox-base']:StreamRequestAnimSet(setName)

Rewrote Execute Component > Exports
Execute:Client(source, component, method, ...) > exports['sandbox-base']:ExecuteClient(source, component, method, ...)

Rewrote Middleware Component > Exports
Middleware:TriggerEvent(event, source, ...) > exports['sandbox-base']:MiddlewareTriggerEvent(event, source, ...)
Middleware:TriggerEventWithData(event, source, ...) > exports['sandbox-base']:MiddlewareTriggerEventWithData(event, source, ...)
Middleware:Add(event, callback, priority) > exports['sandbox-base']:MiddlewareAdd(event, callback, priority)

Rewrote Keybinds Component > Exports
Keybinds:Add(id, key, pad, desc, keydownCb, keyupCb, global) > exports["sandbox-kbs"]:Add(id, key, pad, desc, keydownCb, keyupCb, global)
Keybinds:Enable() > exports["sandbox-kbs"]:Enable()
Keybinds:Disable(keys) > exports["sandbox-kbs"]:Disable(keys)
Keybinds:IsDisabled(key) > exports["sandbox-kbs"]:IsDisabled(key)
Keybinds:GetKey(id) > exports["sandbox-kbs"]:GetKey(id)

Rewrote Sounds Component > Exports
Client side:

Sounds.Play:One(soundFile, soundVolume) > exports["sandbox-sounds"]:PlayOne(soundFile, soundVolume)
Sounds.Play:Distance(maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayDistance(maxDistance, soundFile, soundVolume)
Sounds.Play:Location(location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayLocation(location, maxDistance, soundFile, soundVolume)
Sounds.Loop:One(soundFile, soundVolume) > exports["sandbox-sounds"]:LoopOne(soundFile, soundVolume)
Sounds.Loop:Distance(maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopDistance(maxDistance, soundFile, soundVolume)
Sounds.Loop:Location(location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopLocation(location, maxDistance, soundFile, soundVolume)
Sounds.Stop:One(soundFile) > exports["sandbox-sounds"]:StopOne(soundFile)
Sounds.Stop:Distance(pNet, soundFile) > exports["sandbox-sounds"]:StopDistance(pNet, soundFile)
Sounds.Stop:Location(pNet, soundFile) > exports["sandbox-sounds"]:StopLocation(pNet, soundFile)
Sounds.Fade:One(soundFile) > exports["sandbox-sounds"]:FadeOne(soundFile)
Sounds.Do.Play:One(soundFile, soundVolume) > exports["sandbox-sounds"]:PlayOne(soundFile, soundVolume)
Sounds.Do.Play:Distance(playerNetId, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayDistance(maxDistance, soundFile, soundVolume)
Sounds.Do.Play:Location(playerNetId, location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayLocation(location, maxDistance, soundFile, soundVolume)
Sounds.Do.Loop:One(soundFile, soundVolume) > exports["sandbox-sounds"]:LoopOne(soundFile, soundVolume)
Sounds.Do.Loop:Distance(playerNetId, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopDistance(maxDistance, soundFile, soundVolume)
Sounds.Do.Loop:Location(playerNetId, location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopLocation(location, maxDistance, soundFile, soundVolume)
Sounds.Do.Stop:One(soundFile) > exports["sandbox-sounds"]:StopOne(soundFile)
Sounds.Do.Stop:Distance(playerNetId, soundFile) > exports["sandbox-sounds"]:StopDistance(playerNetId, soundFile)
Sounds.Do.Fade:One(soundFile) > exports["sandbox-sounds"]:FadeOne(soundFile)

Server side:

Sounds.Play:One(clientNetId, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayOne(clientNetId, soundFile, soundVolume)
Sounds.Play:Distance(clientNetId, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayDistance(clientNetId, maxDistance, soundFile, soundVolume)
Sounds.Play:Location(clientNetId, Location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayLocation(clientNetId, Location, maxDistance, soundFile, soundVolume)
Sounds.Play:All(clientNetId, soundFile, soundVolume) > exports["sandbox-sounds"]:PlayAll(clientNetId, soundFile, soundVolume)
Sounds.Play:Job(clientNetId, soundFile, job, soundVolume) > exports["sandbox-sounds"]:PlayJob(clientNetId, soundFile, job, soundVolume)
Sounds.Loop:One(clientNetId, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopOne(clientNetId, soundFile, soundVolume)
Sounds.Loop:Distance(clientNetId, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopDistance(clientNetId, maxDistance, soundFile, soundVolume)
Sounds.Loop:Location(clientNetId, Location, maxDistance, soundFile, soundVolume) > exports["sandbox-sounds"]:LoopLocation(clientNetId, Location, maxDistance, soundFile, soundVolume)
Sounds.Stop:One(clientNetId, soundFile) > exports["sandbox-sounds"]:StopOne(clientNetId, soundFile)
Sounds.Stop:Distance(clientNetId, soundFile) > exports["sandbox-sounds"]:StopDistance(clientNetId, soundFile)
Sounds.Stop:Location(clientNetId, location, soundFile) > exports["sandbox-sounds"]:StopLocation(clientNetId, location, soundFile)

Rewrote VOIP Component > Exports
Client side:

VOIP:Cycle(num) > exports["sandbox-voip"]:Cycle(num)
VOIP:ToggleVoice(plySource, enabled, voiceType, volume) > exports["sandbox-voip"]:ToggleVoice(plySource, enabled, voiceType, volume)
VOIP:MicClicks(on, isLocal) > exports["sandbox-voip"]:MicClicks(on, isLocal)
VOIP:SetPlayerTargets(...) > exports["sandbox-voip"]:SetPlayerTargets(...)
VOIP.Settings.Volumes.Radio:Set(val) > exports["sandbox-voip"]:SetRadioVolume(val)
VOIP.Settings.Volumes.Radio:Get() > exports["sandbox-voip"]:GetRadioVolume()
VOIP.Settings.Volumes.RadioClicks:Set(val) > exports["sandbox-voip"]:SetRadioClickVolume(val)
VOIP.Settings.Volumes.RadioClicks:Get() > exports["sandbox-voip"]:GetRadioClickVolume()
VOIP.Settings.Volumes.Phone:Set(val) > exports["sandbox-voip"]:SetCallVolume(val)
VOIP.Settings.Volumes.Phone:Get() > exports["sandbox-voip"]:GetCallVolume()

Server side:

VOIP:AddPlayer(source) > exports["sandbox-voip"]:AddPlayer(source)
VOIP:RemovePlayer(source) > exports["sandbox-voip"]:RemovePlayer(source)

Radio server side changes:

VOIP.Radio:AddToChannel(source, radioChannel) > exports["sandbox-voip"]:RadioAddToChannel(source, radioChannel)
VOIP.Radio:RemoveFromChannel(source, radioChannel) > exports["sandbox-voip"]:RadioRemoveFromChannel(source, radioChannel)
VOIP.Radio:SetChannel(source, radioChannel) > exports["sandbox-voip"]:RadioSetChannel(source, radioChannel)
VOIP.Radio:SetTalking(source, talking, extendo) > exports["sandbox-voip"]:RadioSetTalking(source, talking, extendo)

Phone server side changes:

VOIP.Phone:AddToCall(source, callChannel) > exports["sandbox-voip"]:PhoneAddToCall(source, callChannel)
VOIP.Phone:RemoveFromCall(source, callChannel) > exports["sandbox-voip"]:PhoneRemoveFromCall(source, callChannel)
VOIP.Phone:SetCall(source, callChannel) > exports["sandbox-voip"]:PhoneSetCall(source, callChannel)
VOIP.Phone:SetTalking(source, talking) > exports["sandbox-voip"]:PhoneSetTalking(source, talking)

Rewrote Netsync Component > Exports
NetSync:DeleteVehicle(vehicle) > exports["sandbox-base"]:DeleteVehicle(vehicle)
NetSync:DeletePed(ped) > exports["sandbox-base"]:DeletePed(ped)
NetSync:DeleteObject(object) > exports["sandbox-base"]:DeleteObject(object)
NetSync:DeleteEntity(entity) > exports["sandbox-base"]:DeleteEntity(entity)
NetSync:SetVehicleTyreBurst(vehicle, index, onRim, dmg) > exports["sandbox-base"]:SetVehicleTyreBurst(vehicle, index, onRim, dmg)
NetSync:SetVehicleDoorShut(vehicle, doorIndex, closeInstantly) > exports["sandbox-base"]:SetVehicleDoorShut(vehicle, doorIndex, closeInstantly)
NetSync:SetVehicleDoorOpen(vehicle, doorIndex, loose, openInstantly) > exports["sandbox-base"]:SetVehicleDoorOpen(vehicle, doorIndex, loose, openInstantly)
NetSync:SetVehicleDoorBroken(vehicle, doorIndex, deleteDoor) > exports["sandbox-base"]:SetVehicleDoorBroken(vehicle, doorIndex, deleteDoor)
NetSync:SetVehicleTyreFixed(vehicle, wheelIndex) > exports["sandbox-base"]:SetVehicleTyreFixed(vehicle, wheelIndex)
NetSync:SetVehicleEngineHealth(vehicle, health) > exports["sandbox-base"]:SetVehicleEngineHealth(vehicle, health)
NetSync:SetVehicleBodyHealth(vehicle, health) > exports["sandbox-base"]:SetVehicleBodyHealth(vehicle, health)
NetSync:SetVehicleDeformationFixed(vehicle) > exports["sandbox-base"]:SetVehicleDeformationFixed(vehicle)
NetSync:SetVehicleFixed(vehicle) > exports["sandbox-base"]:SetVehicleFixed(vehicle)
NetSync:NetworkExplodeVehicle(vehicle, isAudible, isInvisible) > exports["sandbox-base"]:NetworkExplodeVehicle(vehicle, isAudible, isInvisible)
NetSync:TaskWanderInArea(ped, x, y, z, radius, minimalLength, timeBetweenWalks) > exports["sandbox-base"]:TaskWanderInArea(ped, x, y, z, radius, minimalLength, timeBetweenWalks)
NetSync:TaskFollowNavMeshToCoord(ped, x, y, z, speed, timeout, stoppingRange, persistFollowing, unk) > exports["sandbox-base"]:TaskFollowNavMeshToCoord(ped, x, y, z, speed, timeout, stoppingRange, persistFollowing, unk)
NetSync:TaskGoToCoordAnyMeans(ped, x, y, z, speed, p5, p6, walkingStyle, p8) > exports["sandbox-base"]:TaskGoToCoordAnyMeans(ped, x, y, z, speed, p5, p6, walkingStyle, p8)
NetSync:SetEntityAsNoLongerNeeded(ped) > exports["sandbox-base"]:SetEntityAsNoLongerNeeded(ped)
NetSync:SetPedKeepTask(ped, state) > exports["sandbox-base"]:SetPedKeepTask(ped, state)

Rewrote DataStore Component > Exports
Shared:
DataStore:CreateStore(Owner, Key, data) > exports["sandbox-base"]:CreateStore(Owner, Key, Data)
DataStore:DeleteStore(Owner, Key) > exports["sandbox-base"]:DeleteStore(Owner, Key)
exports["sandbox-base"]:FetchComponent("DataStore"):CreateStore(1, "Character", data) > exports["sandbox-base"]:CreateStore(1, "Character", data)

Rewrote Chat Component > Exports
Client side:

Chat.Refresh:Commands() > exports["sandbox-chat"]:RefreshCommands()
Chat.Refresh:Themes() > exports["sandbox-chat"]:RefreshThemes()

Server side:

Chat:RegisterCommand(command, callback, suggestion, arguments, job) > exports["sandbox-chat"]:RegisterCommand(command, callback, suggestion, arguments, job)
Chat:RegisterAdminCommand(command, callback, suggestion, arguments) > exports["sandbox-chat"]:RegisterAdminCommand(command, callback, suggestion, arguments)
Chat:RegisterStaffCommand(command, callback, suggestion, arguments) > exports["sandbox-chat"]:RegisterStaffCommand(command, callback, suggestion, arguments)
Chat.Refresh:Commands(source) > exports["sandbox-chat"]:RefreshCommands(source)
Chat.ClearAll() > exports["sandbox-chat"]:ClearAll()
Chat.Send.OOC(source, message) > exports["sandbox-chat"]:SendOOC(source, message)
Chat.Send.Server:All(message) > exports["sandbox-chat"]:SendServerAll(message)
Chat.Send.Server:Single(source, message) > exports["sandbox-chat"]:SendServerSingle(source, message)
Chat.Send.Broadcast:All(author, message) > exports["sandbox-chat"]:SendBroadcastAll(author, message)
Chat.Send.System:All(message) > exports["sandbox-chat"]:SendSystemAll(message)
Chat.Send.System:Single(source, message) > exports["sandbox-chat"]:SendSystemSingle(source, message)
Chat.Send.System:Broadcast(message) > exports["sandbox-chat"]:SendSystemBroadcast(message)
Chat.Send.Services:Emergency(source, message) > exports["sandbox-chat"]:SendEmergency(source, message)
Chat.Send.Services:EmergencyAnonymous(source, message) > exports["sandbox-chat"]:SendEmergencyAnonymous(source, message)
Chat.Send.Services:EmergencyRespond(source, target, message) > exports["sandbox-chat"]:SendEmergencyRespond(source, target, message)
Chat.Send.Services:NonEmergency(source, message) > exports["sandbox-chat"]:SendNonEmergency(source, message)
Chat.Send.Services:NonEmergencyAnonymous(source, message) > exports["sandbox-chat"]:SendNonEmergencyAnonymous(source, message)
Chat.Send.Services:NonEmergencyRespond(source, target, message) > exports["sandbox-chat"]:SendNonEmergencyRespond(source, target, message)
Chat.Send.Services:Dispatch411(message) > exports["sandbox-chat"]:SendDispatch411(message)
Chat.Send.Services:DispatchDOC(message) > exports["sandbox-chat"]:SendDispatchDOC(message)
Chat.Send.Services:Dispatch(source, message) > exports["sandbox-chat"]:SendDispatch(source, message)
Chat.Send.Services:TestResult(source, message) > exports["sandbox-chat"]:SendTestResult(source, message)

Rewrote Core Component > Exports
Server side:

Core:Shutdown(reason) > exports["sandbox-base"]:Shutdown(reason)
Core:DropAll() > exports["sandbox-base"]:DropAll()

Rewrote Convar Component > Exports
Client side:

COMPONENTS.Convar.DISCORD_APP.value > exports["sandbox-base"]:GetDiscordApp()
COMPONENTS.Convar.MAX_CLIENTS.value > exports["sandbox-base"]:GetMaxClients()
COMPONENTS.Convar.LOGGING.value > exports["sandbox-base"]:GetLogging()
COMPONENTS.Convar.SBFW_VERSION.value > exports["sandbox-base"]:GetSbfwVersion()

Server side:

COMPONENTS.Convar.ENVIRONMENT.value > exports["sandbox-base"]:GetEnvironment()
COMPONENTS.Convar.ACCESS_ROLE.value > exports["sandbox-base"]:GetAccessRole()
COMPONENTS.Convar.API_ADDRESS.value > exports["sandbox-base"]:GetApiAddress()
COMPONENTS.Convar.API_ID.value > exports["sandbox-base"]:GetApiId()
COMPONENTS.Convar.API_SECRET.value > exports["sandbox-base"]:GetApiSecret()
COMPONENTS.Convar.BOT_TOKEN.value > exports["sandbox-base"]:GetDiscordBotToken()
COMPONENTS.Convar.AUTH_URL.value > exports["sandbox-base"]:GetAuthUrl()
COMPONENTS.Convar.AUTH_DB.value > exports["sandbox-base"]:GetAuthDb()
COMPONENTS.Convar.GAME_URL.value > exports["sandbox-base"]:GetGameUrl()
COMPONENTS.Convar.GAME_DB.value > exports["sandbox-base"]:GetGameDb()
COMPONENTS.Convar.LOGGING.value > exports["sandbox-base"]:GetLogging()
COMPONENTS.Convar.SBFW_VERSION.value > exports["sandbox-base"]:GetSbfwVersion()

Rewrote Routing Component > Exports
Server side:

Routing:GetPlayerRoute(source) > exports["sandbox-base"]:GetPlayerRoute(source)
Routing:AddPlayerToRoute(source, route, force) > exports["sandbox-base"]:AddPlayerToRoute(source, route, force)
Routing:RoutePlayerToHiddenRoute(source) > exports["sandbox-base"]:RoutePlayerToHiddenRoute(source)
Routing:RoutePlayerToGlobalRoute(source) > exports["sandbox-base"]:RoutePlayerToGlobalRoute(source)
Routing:RequestRouteId(name, population) > exports["sandbox-base"]:RequestRouteId(name, population)
Routing:CreateRouteId(name, population) > exports["sandbox-base"]:CreateRouteId(name, population)
Routing:GetRouteId(name, population) > exports["sandbox-base"]:GetRouteId(name, population)
Routing:RemoveRouteId(name) > exports["sandbox-base"]:RemoveRouteId(name)
Routing:MoveEntityToGlobalRoute(entityId) > exports["sandbox-base"]:MoveEntityToGlobalRoute(entityId)

Rewrote Player Component > Exports
Client side:

COMPONENTS.Player.LocalPlayer > exports["sandbox-base"]:GetLocalPlayer()
COMPONENTS.Player.LocalPlayer:GetData(key) > exports["sandbox-base"]:GetPlayerData(key)
COMPONENTS.Player.LocalPlayer:SetData(key, value) > exports["sandbox-base"]:SetPlayerData(key, value)

Server side:

COMPONENTS.Player:CheckTokens(source, accountId, existing) > exports["sandbox-base"]:CheckTokens(source, accountId, existing)
COMPONENTS.Players[source] > exports["sandbox-base"]:GetPlayer(source)
COMPONENTS.Players > exports["sandbox-base"]:GetAllPlayers()
COMPONENTS.RecentDisconnects > exports["sandbox-base"]:GetRecentDisconnects()

Rewrote Blips Component > Exports
Client side:
Blips:Add(id, name, coords, sprite, colour, scale, display, category, flashes) > exports["sandbox-blips"]:Add(id, name, coords, sprite, colour, scale, display, category, flashes)
Blips:Remove(id) > exports["sandbox-blips"]:Remove(id)
Blips:RemoveAll() > exports["sandbox-blips"]:RemoveAll()
Blips:SetMarker(id) > exports["sandbox-blips"]:SetMarker(id)

Rewrote Sync Component > Exports
Client side:

Sync:Start(params) > exports["sandbox-sync"]:Start(params)
Sync:Stop(hour) > exports["sandbox-sync"]:Stop(hour)
Sync:IsSyncing() > exports["sandbox-sync"]:IsSyncing()
Sync:GetTime() > exports["sandbox-sync"]:GetTime()
Sync:GetWeather() > exports["sandbox-sync"]:GetWeather()

Server side:

Sync:GetTimeFrozen() > exports["sandbox-sync"]:GetTimeFrozen()
Sync:GetWeatherFrozen() > exports["sandbox-sync"]:GetWeatherFrozen()
Sync:GetBlackout() > exports["sandbox-sync"]:GetBlackout()
Sync:GetNight() > exports["sandbox-sync"]:GetNight()
Sync:GetTime() > exports["sandbox-sync"]:GetTime()
Sync:GetWeather() > exports["sandbox-sync"]:GetWeather()
Sync:GetWinter() > exports["sandbox-sync"]:GetWinter()
Sync:FreezeWeather(state) > exports["sandbox-sync"]:FreezeWeather(state)
Sync:FreezeTime(state) > exports["sandbox-sync"]:FreezeTime(state)
Sync:SetWinter(state) > exports["sandbox-sync"]:SetWinter(state)
Sync:SetBlackout(state) > exports["sandbox-sync"]:SetBlackout(state)
Sync:SetWeather(wtype) > exports["sandbox-sync"]:SetWeather(wtype)
Sync:SetTimeType(type) > exports["sandbox-sync"]:SetTimeType(type)
Sync:SetTime(hour, minute) > exports["sandbox-sync"]:SetTime(hour, minute)
Sync:NextWeatherStage() > exports["sandbox-sync"]:NextWeatherStage()
Sync.Get:TimeFrozen() > exports["sandbox-sync"]:GetTimeFrozen()
Sync.Get:WeatherFrozen() > exports["sandbox-sync"]:GetWeatherFrozen()
Sync.Get:Blackout() > exports["sandbox-sync"]:GetBlackout()
Sync.Get:Night() > exports["sandbox-sync"]:GetNight()
Sync.Get:Time() > exports["sandbox-sync"]:GetTime()
Sync.Get:Weather() > exports["sandbox-sync"]:GetWeather()
Sync.Get:Winter() > exports["sandbox-sync"]:GetWinter()
Sync.Set:Winter(state) > exports["sandbox-sync"]:SetWinter(state)
Sync.Set:Blackout(state) > exports["sandbox-sync"]:SetBlackout(state)
Sync.Set:Weather(wtype) > exports["sandbox-sync"]:SetWeather(wtype)
Sync.Set:TimeType(type) > exports["sandbox-sync"]:SetTimeType(type)
Sync.Set:Time(hour, minute) > exports["sandbox-sync"]:SetTime(hour, minute)

Rewrote Default Component > Exports
Server side:

Default:Add(collection, date, data) > exports['sandbox-base']:DefaultAdd(collection, date, data)
Default:AddAuth(collection, date, data) > exports['sandbox-base']:DefaultAddAuth(collection, date, data)

Rewrote Sequence Component > Exports
Server side:

Sequence:Get(key) > exports['sandbox-base']:SequenceGet(key)
Sequence:Save() > exports['sandbox-base']:SequenceSave()

Rewrote Scaleform Component > Exports
Client side:

Scaleform:Request(Name) > exports['sandbox-base']:ScaleformRequest(Name)
Scaleform:RequestHud(id) > exports['sandbox-base']:ScaleformRequestHud(id)

Rewrote WaitList Component > Exports
Client side:

WaitList:IsInQueue(id) > exports['sandbox-base']:WaitListIsInQueue(id)

Server side:

WaitList:PrintQueue(id) > exports['sandbox-base']:WaitListPrintQueue(id)
WaitList:Create(id, type, options) > exports['sandbox-base']:WaitListCreate(id, type, options)
WaitList:Pause(id) > exports['sandbox-base']:WaitListPause(id)
WaitList:Unpause(id) > exports['sandbox-base']:WaitListUnpause(id)
WaitList.Interact:Add(id, source, data) > exports['sandbox-base']:WaitListInteractAdd(id, source, data)
WaitList.Interact:Remove(id, source) > exports['sandbox-base']:WaitListInteractRemove(id, source)
WaitList.Interact:Pop(id) > exports['sandbox-base']:WaitListInteractPop(id)
WaitList.Interact:Inactive(id, source) > exports['sandbox-base']:WaitListInteractInactive(id, source)
WaitList.Interact:Active(id, source) > exports['sandbox-base']:WaitListInteractActive(id, source)

Rewrote Tasks Component > Exports
Server side:

Tasks:Register(id, timer, cb, data, firstTick) > exports['sandbox-base']:TasksRegister(id, timer, cb, data, firstTick)
Tasks:Delete(id) > exports['sandbox-base']:TasksDelete(id)
Tasks:Pause(id) > exports['sandbox-base']:TasksPause(id)
Tasks:Resume(id) > exports['sandbox-base']:TasksResume(id)
Tasks:Skip(id) > exports['sandbox-base']:TasksSkip(id)

Rewrote WebAPI Component > Exports
Server side:

WebAPI:Request(method, endpoint, params, jsondata) > exports['sandbox-base']:WebAPIRequest(method, endpoint, params, jsondata)
WebAPI.GetMember:Identifier(identifier) > exports['sandbox-base']:WebAPIGetMemberIdentifier(identifier)
WebAPI.GetMember:AccountID(accountId) > exports['sandbox-base']:WebAPIGetMemberAccountID(accountId)
WebAPI:Validate() > exports['sandbox-base']:WebAPIValidate() (commented out)

Rewrote Regex Component > Exports
Server side:

Regex:Test(regex, testString, regexOptions) > exports['sandbox-base']:RegexTest(regex, testString, regexOptions)

Rewrote Punishment Component > Exports
Server side:

Punishment:CheckBan(key, value) > exports['sandbox-base']:PunishmentCheckBan(key, value)
Punishment:Kick(source, reason, issuer, afk) > exports['sandbox-base']:PunishmentKick(source, reason, issuer, afk)
Punishment.Unban:BanID(id, issuer) > exports['sandbox-base']:PunishmentUnbanBanID(id, issuer)
Punishment.Unban:AccountID(aId, issuer) > exports['sandbox-base']:PunishmentUnbanAccountID(aId, issuer)
Punishment.Unban:Identifier(identifier, issuer) > exports['sandbox-base']:PunishmentUnbanIdentifier(identifier, issuer)
Punishment.Ban:Source(source, expires, reason, issuer) > exports['sandbox-base']:PunishmentBanSource(source, expires, reason, issuer)
Punishment.Ban:AccountID(aId, expires, reason, issuer) > exports['sandbox-base']:PunishmentBanAccountID(aId, expires, reason, issuer)
Punishment.Ban:Identifier(identifier, expires, reason, issuer) > exports['sandbox-base']:PunishmentBanIdentifier(identifier, expires, reason, issuer)
Punishment.Actions:Kick(tSource, reason, issuer) > exports['sandbox-base']:PunishmentActionsKick(tSource, reason, issuer)
Punishment.Actions:Ban(tSource, tAccount, tIdentifier, tName, tTokens, reason, expires, expStr, issuer, issuerId, mask) > exports['sandbox-base']:PunishmentActionsBan(tSource, tAccount, tIdentifier, tName, tTokens, reason, expires, expStr, issuer, issuerId, mask)
Punishment.Actions:Unban(ids, issuer) > exports['sandbox-base']:PunishmentActionsUnban(ids, issuer)


Rewrote Phone Component > Exports
Client side:

Phone:Open() > exports['sandbox-phone']:Open()
Phone:OpenLimited() > exports['sandbox-phone']:OpenLimited()
Phone:OpenPayphone() > exports['sandbox-phone']:OpenPayphone()
Phone:Close(forced, doJankyStuff) > exports['sandbox-phone']:Close(forced, doJankyStuff)
Phone:IsOpen() > exports['sandbox-phone']:IsOpen()
Phone:ResetRoute() > exports['sandbox-phone']:ResetRoute()
Phone:ReceiveShare(data) > exports['sandbox-phone']:ReceiveShare(data)
Phone.Permissions:Load(p) > exports['sandbox-phone']:PermissionsLoad(p)
Phone:IsAppUsable(app) > exports['sandbox-phone']:IsAppUsable(app)
Phone.Data:Set(key, data) > exports['sandbox-phone']:DataSet(key, data)
Phone.Data:Add(type, data, key) > exports['sandbox-phone']:DataAdd(type, data, key)
Phone.Data:Update(type, id, data) > exports['sandbox-phone']:DataUpdate(type, id, data)
Phone.Data:Remove(key, id) > exports['sandbox-phone']:DataRemove(key, id)
Phone.Data:Reset() > exports['sandbox-phone']:DataReset()
Phone.Notification:Add(...) > exports['sandbox-phone']:NotificationAdd(...)
Phone.Notification:AddWithId(...) > exports['sandbox-phone']:NotificationAddWithId(...)
Phone.Notification:Update(...) > exports['sandbox-phone']:NotificationUpdate(...)
Phone.Notification:Remove(id) > exports['sandbox-phone']:NotificationRemove(id)
Phone.Notification:Reset() > exports['sandbox-phone']:NotificationReset()
Phone:SetExpanded(state) > exports['sandbox-phone']:SetExpanded(state)
Phone.Permissions:HasPermission(app, permission) > exports['sandbox-phone']:PermissionsHasPermission(app, permission)
Phone.Call:Create(data) > exports['sandbox-phone']:CallCreate(data)
Phone.Call:Recieve(id, number, limited) > exports['sandbox-phone']:CallReceive(id, number, limited)
Phone.Call:Accept() > exports['sandbox-phone']:CallAccept()
Phone.Call:End() > exports['sandbox-phone']:CallEnd()
Phone.Call:Read() > exports['sandbox-phone']:CallRead()
Phone.Call:Status() > exports['sandbox-phone']:CallStatus()

Server side:

Phone:UpdateJobData(source, returnValues) > exports['sandbox-phone']:UpdateJobData(source, returnValues)
Phone.Notification:Add(...) > exports['sandbox-phone']:NotificationAdd(...)
Phone.Notification:AddWithId(...) > exports['sandbox-phone']:NotificationAddWithId(...)
Phone.Notification:Update(...) > exports['sandbox-phone']:NotificationUpdate(...)
Phone.Notification:RemoveById(source, id) > exports['sandbox-phone']:NotificationRemoveById(source, id)
Phone:GeneratePhoneNumber() > exports['sandbox-phone']:GeneratePhoneNumber()
Phone.Call:End(source, business) > exports['sandbox-phone']:CallEnd(source, business)
Phone.Call:CreateRecord(record) > exports['sandbox-phone']:CallCreateRecord(record)
Phone.Call:Decrypt(owner, number) > exports['sandbox-phone']:CallDecrypt(owner, number)
Phone.Call:Read(owner) > exports['sandbox-phone']:CallRead(owner)
Phone.Contacts:IsContact(myId, targetNumber) > exports['sandbox-phone']:ContactsIsContact(myId, targetNumber)
Phone.Adverts:Create(source, advert) > exports['sandbox-phone']:AdvertsCreate(source, advert)
Phone.Adverts:Update(source, advert) > exports['sandbox-phone']:AdvertsUpdate(source, advert)
Phone.Adverts:Delete(source) > exports['sandbox-phone']:AdvertsDelete(source)
Phone.Documents:Create(source, doc) > exports['sandbox-phone']:DocumentsCreate(source, doc)
Phone.Documents:Edit(source, id, doc) > exports['sandbox-phone']:DocumentsEdit(source, id, doc)
Phone.Documents:Delete(source, id) > exports['sandbox-phone']:DocumentsDelete(source, id)
Phone.Email:Read(charId, id) > exports['sandbox-phone']:EmailRead(charId, id)
Phone.Email:Send(serverId, sender, time, subject, body, flags, expires) > exports['sandbox-phone']:EmailSend(serverId, sender, time, subject, body, flags, expires)
Phone.Email:Delete(charId, id) > exports['sandbox-phone']:EmailDelete(charId, id)
Phone.Messages:Read(owner, number) > exports['sandbox-phone']:MessagesRead(owner, number)
Phone.Messages:Delete(owner, number) > exports['sandbox-phone']:MessagesDelete(owner, number)
Phone.Store.Install:Check(app, method) > exports['sandbox-phone']:StoreInstallCheck(app, method)
Phone.Store.Install:Do(app, apps, method) > exports['sandbox-phone']:StoreInstallDo(app, apps, method)
Phone.Store.Uninstall:Check(app) > exports['sandbox-phone']:StoreUninstallCheck(app)
Phone.Store.Uninstall:Do(app, apps) > exports['sandbox-phone']:StoreUninstallDo(app, apps)
Phone.Twitter:Get() > exports['sandbox-phone']:TwitterGet()
Phone.Twitter:Post(source, SID, author, content, image, isRetweet, verified) > exports['sandbox-phone']:TwitterPost(source, SID, author, content, image, isRetweet, verified)
Phone.CoManager:FetchAllAccessibleRosters(source) > exports['sandbox-phone']:CoManagerFetchAllAccessibleRosters(source)
Phone.CoManager:FetchTimeWorked(source, jobId) > exports['sandbox-phone']:CoManagerFetchTimeWorked(source, jobId)
PHOTOS:Create(source, photo) > exports['sandbox-phone']:PhotosCreate(source, photo)
PHOTOS:Fetch(source) > exports['sandbox-phone']:PhotosFetch(source)
PHOTOS:Delete(source, id) > exports['sandbox-phone']:PhotosDelete(source, id)


Rewrote Menu Component > Exports
Client side:

Menu:Create(...) > exports['sandbox-menu']:Create(...)
Menu:IsOpen() > exports['sandbox-menu']:IsOpen()

Rewrote Buffs Component > Exports
Client side:

Buffs:RegisterBuff(id, icon, color, duration, type) > exports['sandbox-hud']:RegisterBuff(id, icon, color, duration, type)
Buffs:ApplyBuff(buffId, val, override, options) > exports['sandbox-hud']:ApplyBuff(buffId, val, override, options)
Buffs:ApplyUniqueBuff(buffId, val, override, options) > exports['sandbox-hud']:ApplyUniqueBuff(buffId, val, override, options)
Buffs:UpdateBuff(buffId, nVal) > exports['sandbox-hud']:UpdateBuff(buffId, nVal)
Buffs:IconOverride(buffId, override) > exports['sandbox-hud']:BuffsIconOverride(buffId, override)
Buffs:RemoveBuffType(buffId) > exports['sandbox-hud']:RemoveBuffType(buffId)

Rewrote Action Component > Exports
Client side:

Action:Show(id, message, duration) > exports['sandbox-hud']:ActionShow(id, message, duration)
Action:Hide(id) > exports['sandbox-hud']:ActionHide(id)
Action:HideAll() > exports['sandbox-hud']:ActionHideAll()

Rewrote Confirm Component > Exports
Client side:

Confirm:Show(title, events, description, data, denyLabel, acceptLabel) > exports['sandbox-hud']:ConfirmShow(title, events, description, data, denyLabel, acceptLabel)
Confirm:Close() > exports['sandbox-hud']:ConfirmClose()

Rewrote UISounds Component > Exports
Client side:

UISounds.Play:Generic(id, sound, library) > exports['sandbox-sounds']:UISoundsPlayGeneric(id, sound, library)
UISounds.Play:Coords(id, sound, library, coords) > exports['sandbox-sounds']:UISoundsPlayCoords(id, sound, library, coords)
UISounds.Play:Entity(id, sound, library, entity) > exports['sandbox-sounds']:UISoundsPlayEntity(id, sound, library, entity)
UISounds.Play:FrontEnd(id, sound, library) > exports['sandbox-sounds']:UISoundsPlayFrontEnd(id, sound, library)

Server side:

UISounds.Play:Generic(clientId, id, sound, library) > exports['sandbox-sounds']:UISoundsPlayGeneric(clientId, id, sound, library)
UISounds.Play:Coords(clientId, id, sound, library, coords) > exports['sandbox-sounds']:UISoundsPlayCoords(clientId, id, sound, library, coords)
UISounds.Play:Entity(clientId, id, sound, library, entity) > exports['sandbox-sounds']:UISoundsPlayEntity(clientId, id, sound, library, entity)
UISounds.Play:FrontEnd(clientId, id, sound, library) > exports['sandbox-sounds']:UISoundsPlayFrontEnd(clientId, id, sound, library)

Rewrote Input Component > Exports
Client side:

Input:Show(title, label, inputs, event, data) > exports['sandbox-hud']:InputShow(title, label, inputs, event, data)
Input:Close() > exports['sandbox-hud']:InputClose()


Rewrote ListMenu Component > Exports
Client side:

ListMenu:Show(menus) > exports['sandbox-hud']:ListMenuShow(menus)
ListMenu:Close() > exports['sandbox-hud']:ListMenuClose()

Rewrote Hud Component > Exports
Client side:

Hud:IsDisabled() > exports['sandbox-hud']:IsDisabled()
Hud:IsDisabledAllowDead() > exports['sandbox-hud']:IsDisabledAllowDead()
Hud:ForceHP() > exports['sandbox-hud']:ForceHP()
Hud:Show() > exports['sandbox-hud']:Show()
Hud:Hide() > exports['sandbox-hud']:Hide()
Hud:Toggle() > exports['sandbox-hud']:Toggle()
Hud:ShiftLocation(status) > exports['sandbox-hud']:ShiftLocation(status)
Hud.Overlay:Show(data) > exports['sandbox-hud']:OverlayShow(data)
Hud.Overlay:Hide() > exports['sandbox-hud']:OverlayHide()
Hud.Vehicle:Show() > exports['sandbox-hud']:VehicleShow()
Hud.Vehicle:Hide() > exports['sandbox-hud']:VehicleHide()
Hud.Vehicle:Toggle() > exports['sandbox-hud']:VehicleToggle()
Hud:RegisterStatus(...) > exports['sandbox-hud']:RegisterStatus(...)
Hud:ResetStatus() > exports['sandbox-hud']:ResetStatus()
Hud.ID:Toggle() > exports['sandbox-hud']:IDToggle()
Hud:Dead(state) > exports['sandbox-hud']:Dead(state)
Hud.GemTable:Open(quality) > exports['sandbox-hud']:GemTableOpen(quality)
Hud.GemTable:Close() > exports['sandbox-hud']:GemTableClose()
Hud.Meth:Open(config) > exports['sandbox-hud']:MethOpen(config)
Hud.Meth:Close() > exports['sandbox-hud']:MethClose()
Hud.DeathTexts:Show(...) > exports['sandbox-hud']:DeathTextsShow(...)
Hud.DeathTexts:Release() > exports['sandbox-hud']:DeathTextsRelease()
Hud.DeathTexts:Hide() > exports['sandbox-hud']:DeathTextsHide()
Hud.Flashbang:Do(...) > exports['sandbox-hud']:FlashbangDo(...)
Hud.Flashbang:End() > exports['sandbox-hud']:FlashbangEnd()
Hud:UpdateVoip(...) > exports['sandbox-hud']:UpdateVoip(...)
Hud:NOS(level) > exports['sandbox-hud']:NOS(level)

Rewrote InfoOverlay Component > Exports
Client side:

InfoOverlay:Show(title, description) > exports['sandbox-hud']:InfoOverlayShow(title, description)
InfoOverlay:Close() > exports['sandbox-hud']:InfoOverlayClose()
InfoOverlay:IsOpen() > exports['sandbox-hud']:InfoOverlayIsOpen()

Rewrote Interaction Component > Exports
Client side:

Interaction:Show() > exports['sandbox-hud']:InteractionShow()
Interaction:Hide() > exports['sandbox-hud']:InteractionHide()
Interaction:RegisterMenu(id, label, icon, action, shouldShow, labelFunc) > exports['sandbox-hud']:InteractionRegisterMenu(id, label, icon, action, shouldShow, labelFunc)
Interaction:ShowMenu(items) > exports['sandbox-hud']:InteractionShowMenu(items)
Interaction:Back() > exports['sandbox-hud']:InteractionBack()
Interaction:ItemsAsMenu(items) > exports['sandbox-hud']:InteractionItemsAsMenu(items)

Rewrote Progress Component > Exports
Client side:

Progress:CurrentAction() > exports['sandbox-hud']:ProgressCurrentAction()
Progress:Progress(action, finish) > exports['sandbox-hud']:Progress(action, finish)
Progress:ProgressWithStartEvent(action, start, finish) > exports['sandbox-hud']:ProgressWithStartEvent(action, start, finish)
Progress:ProgressWithTickEvent(action, tick, finish) > exports['sandbox-hud']:ProgressWithTickEvent(action, tick, finish)
Progress:ProgressWithStartAndTick(action, start, tick, finish) > exports['sandbox-hud']:ProgressWithStartAndTick(action, start, tick, finish)
Progress:Modifier(p, t) > exports['sandbox-hud']:ProgressModifier(p, t)
Progress:Cancel(force) > exports['sandbox-hud']:ProgressCancel(force)
Progress:Fail() > exports['sandbox-hud']:ProgressFail()
Progress:Finish() > exports['sandbox-hud']:ProgressFinish()

Rewrote Drilling Component > Exports
Client side:

Drilling.Start(callback) > exports['sandbox-games']:DrillingStart(callback)
Drilling.Draw() > exports['sandbox-games']:DrillingDraw()
Drilling.HandleControls() > exports['sandbox-games']:DrillingHandleControls()
Drilling.DisableControls() > exports['sandbox-games']:DrillingDisableControls()
Drilling.EnableControls() > exports['sandbox-games']:DrillingEnableControls()

Rewrote Minigame Component > Exports
Client side:

Minigame.Play:Skillbar(...) > exports['sandbox-games']:MinigamePlaySkillbar(...)
Minigame.Play:RoundSkillbar(...) > exports['sandbox-games']:MinigamePlayRoundSkillbar(...)
Minigame.Play:Scanner(...) > exports['sandbox-games']:MinigamePlayScanner(...)
Minigame.Play:Sequencer(...) > exports['sandbox-games']:MinigamePlaySequencer(...)
Minigame.Play:Keypad(...) > exports['sandbox-games']:MinigamePlayKeypad(...)
Minigame.Play:Scrambler(...) > exports['sandbox-games']:MinigamePlayScrambler(...)
Minigame.Play:Memory(...) > exports['sandbox-games']:MinigamePlayMemory(...)
Minigame.Play:Aim(...) > exports['sandbox-games']:MinigamePlayAim(...)
Minigame.Play:Captcha(...) > exports['sandbox-games']:MinigamePlayCaptcha(...)
Minigame.Play:Keymaster(...) > exports['sandbox-games']:MinigamePlayKeymaster(...)
Minigame.Play:Pattern(...) > exports['sandbox-games']:MinigamePlayPattern(...)
Minigame.Play:Icons(...) > exports['sandbox-games']:MinigamePlayIcons(...)
Minigame.Play:Tracking(...) > exports['sandbox-games']:MinigamePlayTracking(...)
Minigame.Play:Sliders(...) > exports['sandbox-games']:MinigamePlaySliders(...)
Minigame.Play:Drill(...) > exports['sandbox-games']:MinigamePlayDrill(...)
Minigame:Cancel() > exports['sandbox-games']:MinigameCancel()
Minigame:End() > exports['sandbox-games']:MinigameEnd()

Rewrote Scaleform Component > Exports
Client side:

Scaleforms.LoadMovie(name) > exports['sandbox-games']:ScaleformLoadMovie(name)
Scaleforms.LoadInteractive(name) > exports['sandbox-games']:ScaleformLoadInteractive(name)
Scaleforms.UnloadMovie(scaleform) > exports['sandbox-games']:ScaleformUnloadMovie(scaleform)
Scaleforms.LoadAdditionalText(gxt, count) > exports['sandbox-games']:ScaleformLoadAdditionalText(gxt, count)
Scaleforms.SetLabels(scaleform, labels) > exports['sandbox-games']:ScaleformSetLabels(scaleform, labels)
Scaleforms.PopMulti(scaleform, method, ...) > exports['sandbox-games']:ScaleformPopMulti(scaleform, method, ...)
Scaleforms.PopFloat(scaleform, method, val) > exports['sandbox-games']:ScaleformPopFloat(scaleform, method, val)
Scaleforms.PopInt(scaleform, method, val) > exports['sandbox-games']:ScaleformPopInt(scaleform, method, val)
Scaleforms.PopBool(scaleform, method, val) > exports['sandbox-games']:ScaleformPopBool(scaleform, method, val)
Scaleforms.PopRet(scaleform, method) > exports['sandbox-games']:ScaleformPopRet(scaleform, method)
Scaleforms.PopVoid(scaleform, method) > exports['sandbox-games']:ScaleformPopVoid(scaleform, method)
Scaleforms.RetBool(ret) > exports['sandbox-games']:ScaleformRetBool(ret)
Scaleforms.RetInt(ret) > exports['sandbox-games']:ScaleformRetInt(ret)
Scaleforms.TrueType(val) > exports['sandbox-games']:ScaleformTrueType(val)

Rewrote Fuel Component > Exports
Client side:

Vehicles.Fuel:CanBeFueled(vehicle) > exports['sandbox-fuel']:CanBeFueled(vehicle)

Rewrote Trunk Component > Exports
Client side:

Trunk:GetIn(veh) > exports['sandbox-escort']:TrunkGetIn(veh)
Trunk:GetOut() > exports['sandbox-escort']:TrunkGetOut()
Trunk:ToggleTrunk() > exports['sandbox-escort']:TrunkToggleTrunk()

Server side:

Trunk:Enter(source, netId) > exports['sandbox-escort']:TrunkEnter(source, netId)
Trunk:Exit(source, netId) > exports['sandbox-escort']:TrunkExit(source, netId)

Rewrote Escort Component > Exports
Client side:

Escort:DoEscort(target, tPlayer) > exports['sandbox-escort']:DoEscort(target, tPlayer)
Escort:StopEscort() > exports['sandbox-escort']:StopEscort()

Server side:

Escort:Do(source, data) > exports['sandbox-escort']:EscortDo(source, data)
Escort:DoPutIn(source, data) > exports['sandbox-escort']:EscortDoPutIn(source, data)
Escort:Stop(source) > exports['sandbox-escort']:EscortStop(source)

Rewrote Loot Component > Exports
Server side:

Loot:ItemClass(...) > exports['sandbox-inventory']:LootItemClass(...)
Loot:CustomSet(...) > exports['sandbox-inventory']:LootCustomSet(...)
Loot:CustomSetWithCount(...) > exports['sandbox-inventory']:LootCustomSetWithCount(...)
Loot:CustomWeightedSet(...) > exports['sandbox-inventory']:LootCustomWeightedSet(...)
Loot:CustomWeightedSetWithCount(...) > exports['sandbox-inventory']:LootCustomWeightedSetWithCount(...)
Loot:CustomWeightedSetWithCountAndModifier(...) > exports['sandbox-inventory']:LootCustomWeightedSetWithCountAndModifier(...)
Loot.Sets:Gem(...) > exports['sandbox-inventory']:LootSetsGem(...)
Loot.Sets:GemRandom(...) > exports['sandbox-inventory']:LootSetsGemRandom(...)
Loot.Sets:Ore(...) > exports['sandbox-inventory']:LootSetsOre(...)

Rewrote Vendor & PedInteraction Component > Exports
Client side:

PedInteraction:Add(id, model, coords, heading, range, menu, icon, scenario, enabled, anim, component) > exports['sandbox-pedinteraction']:Add(id, model, coords, heading, range, menu, icon, scenario, enabled, anim, component)
PedInteraction:Toggle(id, enabled) > exports['sandbox-pedinteraction']:Toggle(id, enabled)
PedInteraction:Remove(id) > exports['sandbox-pedinteraction']:Remove(id)
PedInteraction:GetPed(id) > exports['sandbox-pedinteraction']:GetPed(id)

Server side:

Vendor:Create(id, type, name, model, position, items, iconOverride, labelOverride, isUnique, isGlobalUnique, isIllegal, stockTimeDelay, restock) > exports['sandbox-pedinteraction']:VendorCreate(id, type, name, model, position, items, iconOverride, labelOverride, isUnique, isGlobalUnique, isIllegal, stockTimeDelay, restock)
Vendor:Remove(id) > exports['sandbox-pedinteraction']:VendorRemove(id)

Rewrote Vehicles Component > Exports
Client side:

Vehicles.Repair:NeedsKit(veh, type) > exports['sandbox-vehicles']:RepairNeedsKit(veh, type)
Vehicles.Repair:Kit(veh, type) > exports['sandbox-vehicles']:RepairKit(veh, type)
Vehicles.Repair:Normal(veh, alreadyDone) > exports['sandbox-vehicles']:RepairNormal(veh, alreadyDone)
Vehicles.Repair:Engine(veh) > exports['sandbox-vehicles']:RepairEngine(veh)
Vehicles.Repair:Part(veh, part, repairAmount) > exports['sandbox-vehicles']:RepairPart(veh, part, repairAmount)
Vehicles.Repair:Full(veh) > exports['sandbox-vehicles']:RepairFull(veh)
Vehicles.Sync.Indicators:Get() > exports['sandbox-vehicles']:SyncIndicatorsGet()
Vehicles.Sync.Indicators:Set(type) > exports['sandbox-vehicles']:SyncIndicatorsSet(type)
Vehicles.Sync.Neons:Has() > exports['sandbox-vehicles']:SyncNeonsHas()
Vehicles.Sync.Neons:IsDisabled() > exports['sandbox-vehicles']:SyncNeonsIsDisabled()
Vehicles.Sync.Neons:Toggle(toggle) > exports['sandbox-vehicles']:SyncNeonsToggle(toggle)
Vehicles.Sync.EmergencyLights:Toggle() > exports['sandbox-vehicles']:SyncEmergencyLightsToggle()
Vehicles.Sync.EmergencyLights:Get() > exports['sandbox-vehicles']:SyncEmergencyLightsGet()
Vehicles.Sync.EmergencySiren:Cycle() > exports['sandbox-vehicles']:SyncEmergencySirenCycle()
Vehicles.Sync.EmergencySiren:Toggle() > exports['sandbox-vehicles']:SyncEmergencySirenToggle()
Vehicles.Sync.EmergencySiren:Get() > exports['sandbox-vehicles']:SyncEmergencySirenGet()
Vehicles.Sync.EmergencyAirhorn:Set(state) > exports['sandbox-vehicles']:SyncEmergencyAirhornSet(state)
Vehicles.Sync.EmergencyAirhorn:Get() > exports['sandbox-vehicles']:SyncEmergencyAirhornGet()
Vehicles.Sync.Doors:Open(vehicle, doorNum, loose, instant) > exports['sandbox-vehicles']:SyncDoorsOpen(vehicle, doorNum, loose, instant)
Vehicles.Sync.Doors:Shut(vehicle, doorNum, instant) > exports['sandbox-vehicles']:SyncDoorsShut(vehicle, doorNum, instant)
Vehicles.Sync.Bike:Pickup(vehicle) > exports['sandbox-vehicles']:SyncBikePickup(vehicle)
Vehicles.Sync.Bike:Drop() > exports['sandbox-vehicles']:SyncBikeDrop()
Vehicles.Keys:Has(VIN, gKeys) > exports['sandbox-vehicles']:KeysHas(VIN, gKeys)
Vehicles:SetLocks(veh, state) > exports['sandbox-vehicles']:SetLocks(veh, state)
Vehicles:HasAccess(vehicle, keysOnly, ownedOnly) > exports['sandbox-vehicles']:HasAccess(vehicle, keysOnly, ownedOnly)
Vehicles.Engine:Force(veh, state) > exports['sandbox-vehicles']:EngineForce(veh, state)
Vehicles.Engine:Off(customMessage) > exports['sandbox-vehicles']:EngineOff(customMessage)
Vehicles.Engine:On() > exports['sandbox-vehicles']:EngineOn()
Vehicles.Engine:CheckKeys() > exports['sandbox-vehicles']:EngineCheckKeys()
Vehicles.Engine:Toggle(vehicle) > exports['sandbox-vehicles']:EngineToggle(vehicle)
Vehicles:SlimJim(vehicle) > exports['sandbox-vehicles']:SlimJim(vehicle)
Vehicles:LockpickExterior(config, canUnlockOwned, vehicle, cb) > exports['sandbox-vehicles']:LockpickExterior(config, canUnlockOwned, vehicle, cb)
Vehicles:Lockpick(config, canUnlockOwned, cb) > exports['sandbox-vehicles']:Lockpick(config, canUnlockOwned, cb)
Vehicles:HackExterior(hackData, canUnlockOwned, vehicle, cb) > exports['sandbox-vehicles']:HackExterior(hackData, canUnlockOwned, vehicle, cb)
Vehicles:Hack(hackData, canUnlockOwned, cb) > exports['sandbox-vehicles']:Hack(hackData, canUnlockOwned, cb)
Vehicles:CanBeStored(vehicle) > exports['sandbox-vehicles']:CanBeStored(vehicle)
Vehicles.Properties:Get(vehicle) > exports['sandbox-vehicles']:PropertiesGet(vehicle)
Vehicles.Properties:Set(vehicle, data) > exports['sandbox-vehicles']:PropertiesSet(vehicle, data)
Vehicles.Utils:IsCloseToRearOfVehicle(vehicle, coords) > exports['sandbox-vehicles']:UtilsIsCloseToRearOfVehicle(vehicle, coords)
Vehicles.Utils:IsCloseToFrontOfVehicle(vehicle, coords) > exports['sandbox-vehicles']:UtilsIsCloseToFrontOfVehicle(vehicle, coords)
Vehicles.Utils:IsCloseToVehicle(vehicle, coords) > exports['sandbox-vehicles']:UtilsIsCloseToVehicle(vehicle, coords)
Vehicles.Class:Get(entity) > exports['sandbox-vehicles']:ClassGet(entity)
Vehicles.Class:IsClass(entity, class) > exports['sandbox-vehicles']:IsClass(entity, class)
Vehicles.Class:IsClassOrHigher(entity, class) > exports['sandbox-vehicles']:IsClassOrHigher(entity, class)

Server side:

Vehicles.Stores:Create(id, data) > exports['sandbox-vehicles']:StoresCreate(id, data)
Vehicles.Stores:Delete(id) > exports['sandbox-vehicles']:StoresDelete(id)
Vehicles.RandomModel:DClass() > exports['sandbox-vehicles']:RandomModelDClass()
Vehicles.RandomModel:CCLass() > exports['sandbox-vehicles']:RandomModelCClass()
Vehicles.RandomModel:BClass() > exports['sandbox-vehicles']:RandomModelBClass()
Vehicles.RandomModel:AClass() > exports['sandbox-vehicles']:RandomModelAClass()
Vehicles.RandomModel:SClass() > exports['sandbox-vehicles']:RandomModelSClass()
Vehicles.RandomModel:XClass() > exports['sandbox-vehicles']:RandomModelXClass()
Vehicles:RandomName() > exports['sandbox-vehicles']:RandomName()
Vehicles:RandomNameByMake(make) > exports['sandbox-vehicles']:RandomNameByMake(make)
Vehicles.Garages:GetAll() > exports['sandbox-vehicles']:GaragesGetAll()
Vehicles.Garages:Get(id) > exports['sandbox-vehicles']:GaragesGet(id)
Vehicles.Garages:Impound() > exports['sandbox-vehicles']:GaragesImpound()
Vehicles.Owned:AddToCharacter(...) > exports['sandbox-vehicles']:OwnedAddToCharacter(...)
Vehicles.Owned:AddToFleet(...) > exports['sandbox-vehicles']:OwnedAddToFleet(...)
Vehicles.Owned:Add(...) > exports['sandbox-vehicles']:OwnedAdd(...)
Vehicles.Owned:GetActive(VIN) > exports['sandbox-vehicles']:OwnedGetActive(VIN)
Vehicles.Owned:GetVIN(VIN, cb) > exports['sandbox-vehicles']:OwnedGetVIN(VIN, cb)
Vehicles.Owned:GetAll(...) > exports['sandbox-vehicles']:OwnedGetAll(...)
Vehicles.Owned:GetAllActive() > exports['sandbox-vehicles']:OwnedGetAllActive()
Vehicles.Owned:Spawn(...) > exports['sandbox-vehicles']:OwnedSpawn(...)
Vehicles.Owned:Store(...) > exports['sandbox-vehicles']:OwnedStore(...)
Vehicles.Owned:Delete(...) > exports['sandbox-vehicles']:OwnedDelete(...)
Vehicles.Owned:ForceSave(VIN) > exports['sandbox-vehicles']:OwnedForceSave(VIN)
Vehicles.Owned:Properties:Store(...) > exports['sandbox-vehicles']:OwnedPropertiesStore(...)
Vehicles.Owned:Properties:Get(...) > exports['sandbox-vehicles']:OwnedPropertiesGet(...)
Vehicles.Owned:Properties:GetCount(...) > exports['sandbox-vehicles']:OwnedPropertiesGetCount(...)
Vehicles.Owned:Seize(VIN, seizeState) > exports['sandbox-vehicles']:OwnedSeize(VIN, seizeState)
Vehicles.Owned:Track(VIN) > exports['sandbox-vehicles']:OwnedTrack(VIN)
Vehicles:SpawnTemp(...) > exports['sandbox-vehicles']:SpawnTemp(...)
Vehicles:Delete(vehicleId, cb) > exports['sandbox-vehicles']:Delete(vehicleId, cb)
Vehicles:StopDespawn(vehicle) > exports['sandbox-vehicles']:StopDespawn(vehicle)
Vehicles.Identification.Plate:Generate(isTemp) > exports['sandbox-vehicles']:PlateGenerate(isTemp)
Vehicles.Identification.VIN:GenerateOwned() > exports['sandbox-vehicles']:VINGenerateOwned()
Vehicles.Identification.VIN:GenerateLocal() > exports['sandbox-vehicles']:VINGenerateLocal()
Vehicles.Stores:Delete(VIN) > exports['sandbox-vehicles']:StoresDelete(VIN)
Vehicles.Stores:Create(vehicle.VIN, vehicle) > exports['sandbox-vehicles']:StoresCreate(vehicle.VIN, vehicle)
Vehicles.Keys:Has(source, VIN, groupKeys) > exports['sandbox-vehicles']:KeysHas(source, VIN, groupKeys)
Vehicles.Keys:Add(source, VIN) > exports['sandbox-vehicles']:KeysAdd(source, VIN)
Vehicles.Keys:Remove(source, VIN) > exports['sandbox-vehicles']:KeysRemove(source, VIN)
Vehicles.Keys:AddBySID(SID, VIN) > exports['sandbox-vehicles']:KeysAddBySID(SID, VIN)
Vehicles.DonatorPlates:Add(playerIdentifier) > exports['sandbox-vehicles']:DonatorPlatesAdd(playerIdentifier)
Vehicles.DonatorPlates:Check(playerIdentifier) > exports['sandbox-vehicles']:DonatorPlatesCheck(playerIdentifier)
Vehicles.DonatorPlates:Remove(playerIdentifier, amount) > exports['sandbox-vehicles']:DonatorPlatesRemove(playerIdentifier, amount)

Rewrote Ped Component > Exports
Client side:

Ped:ApplyToPed(ped, skip, entityOverride) > exports['sandbox-ped']:ApplyToPed(ped, skip, entityOverride)
Ped:Preview(entity, gender, ped, skip, gangChain) > exports['sandbox-ped']:Preview(entity, gender, ped, skip, gangChain)
Ped.Creator:Start(data) > exports['sandbox-ped']:CreatorStart(data)
Ped.Creator:End() > exports['sandbox-ped']:CreatorEnd()
Ped.Customization:Show(type, data) > exports['sandbox-ped']:CustomizationShow(type, data)
Ped.Customization:Hide() > exports['sandbox-ped']:CustomizationHide()
Ped.Customization:Save(cb) > exports['sandbox-ped']:CustomizationSave(cb)
Ped.Customization:Cancel() > exports['sandbox-ped']:CustomizationCancel()

Server side:

Ped:Save(char, ped) > exports['sandbox-ped']:Save(char, ped)
Ped:ApplyOutfit(source, outfit) > exports['sandbox-ped']:ApplyOutfit(source, outfit)
Ped.Mask:Equip(source, data) > exports['sandbox-ped']:MaskEquip(source, data)
Ped.Mask:Unequip(source) > exports['sandbox-ped']:MaskUnequip(source)
Ped.Mask:UnequipNoItem(source) > exports['sandbox-ped']:MaskUnequipNoItem(source)
Ped.Hat:Equip(source, data) > exports['sandbox-ped']:HatEquip(source, data)
Ped.Hat:Unequip(source) > exports['sandbox-ped']:HatUnequip(source)
Ped.Necklace:Equip(source, data) > exports['sandbox-ped']:NecklaceEquip(source, data)
Ped.Necklace:Unequip(source) > exports['sandbox-ped']:NecklaceUnequip(source)
Ped.Necklace:UnequipNoItem(source) > exports['sandbox-ped']:NecklaceUnequipNoItem(source)

Rewrote Wardrobe Component > Exports
Client side:

Wardrobe:Show() > exports['sandbox-ped']:WardrobeShow()
Wardrobe:Close() > exports['sandbox-ped']:WardrobeClose()

Rewrote Billboards Component > Exports
Server side:

Billboards:Set(id, url) > exports['sandbox-billboards']:BillboardsSet(id, url)
Billboards:Get(id) > exports['sandbox-billboards']:BillboardsGet(id)
Billboards:GetCategory(cat) > exports['sandbox-billboards']:BillboardsGetCategory(cat)

Rewrote Animations Component > Exports
Client side:

Animations.Emotes:Play(emote, fromUserInput, time, notCancellable, skipDisarm) > exports['sandbox-animations']:EmotesPlay(emote, fromUserInput, time, notCancellable, skipDisarm)
Animations.Emotes:Cancel() > exports['sandbox-animations']:EmotesCancel()
Animations.Emotes:ForceCancel() > exports['sandbox-animations']:EmotesForceCancel()
Animations.Emotes:Get() > exports['sandbox-animations']:EmotesGet()
Animations.Emotes:WakeUp(pos) > exports['sandbox-animations']:EmotesWakeUp(pos)
Animations.EmoteBinds:Update(newBinds) > exports['sandbox-animations']:EmoteBindsUpdate(newBinds)
Animations.EmoteBinds:Use(bindId) > exports['sandbox-animations']:EmoteBindsUse(bindId)
Animations:OpenMainEmoteMenu() > exports['sandbox-animations']:OpenMainEmoteMenu()
Animations:OpenWalksMenu(fromMainMenu) > exports['sandbox-animations']:OpenWalksMenu(fromMainMenu)
Animations:OpenExpressionsMenu() > exports['sandbox-animations']:OpenExpressionsMenu()
Animations.PedFeatures:ToggleCrouch(toggle) > exports['sandbox-animations']:PedFeaturesToggleCrouch(toggle)
Animations.PedFeatures:SetWalk(walk, label) > exports['sandbox-animations']:PedFeaturesSetWalk(walk, label)
Animations.PedFeatures:SetExpression(expression, label) > exports['sandbox-animations']:PedFeaturesSetExpression(expression, label)
Animations.PedFeatures:RequestFeaturesUpdate(feats) > exports['sandbox-animations']:PedFeaturesRequestFeaturesUpdate(feats)

Server side:

Animations.PedFeatures:UpdateFeatureInfo(char, type, data, cb) > exports['sandbox-animations']:PedFeaturesUpdateFeatureInfo(char, type, data, cb)
Animations.EmoteBinds:Update(char, data, cb) > exports['sandbox-animations']:EmoteBindsUpdate(char, data, cb)

Rewrote Damage & Hospital Component > Exports
Client side:

Hospital:CheckIn() > exports['sandbox-damage']:HospitalCheckIn()
Hospital:SendToBed(bed, isRp, bedId) > exports['sandbox-damage']:HospitalSendToBed(bed, isRp, bedId)
Hospital:FindBed(object) > exports['sandbox-damage']:HospitalFindBed(object)
Hospital:LeaveBed() > exports['sandbox-damage']:HospitalLeaveBed()
Damage.Reductions:Increase(amt) > exports['sandbox-damage']:ReductionsIncrease(amt)
Damage.Reductions:Reset() > exports['sandbox-damage']:ReductionsReset()
Damage:CalculateMaxHp() > exports['sandbox-damage']:CalculateMaxHp()
Damage:WasDead(sid) > exports['sandbox-damage']:WasDead(sid)
Damage:Revive(fieldTreat) > exports['sandbox-damage']:Revive(fieldTreat)
Damage:Died() > exports['sandbox-damage']:Died()
Damage.Apply:StandardDamage(value, armorFirst, forceKill) > exports['sandbox-damage']:ApplyStandardDamage(value, armorFirst, forceKill)

Server side:

Hospital:RequestBed(source) > exports['sandbox-damage']:HospitalRequestBed(source)
Hospital:FindBed(source, location) > exports['sandbox-damage']:HospitalFindBed(source, location)
Hospital:OccupyBed(source, bedId) > exports['sandbox-damage']:HospitalOccupyBed(source, bedId)
Hospital:LeaveBed(source) > exports['sandbox-damage']:HospitalLeaveBed(source)
Hospital.ICU:Send(target) > exports['sandbox-damage']:HospitalICUSend(target)
Hospital.ICU:Release(target) > exports['sandbox-damage']:HospitalICURelease(target)
Hospital.ICU:GetItems(target) > exports['sandbox-damage']:HospitalICUGetItems(target)
Damage:GetLimbDamage(sid) > exports['sandbox-damage']:GetLimbDamage(sid)
Damage:ResetLimbDamage(sid) > exports['sandbox-damage']:ResetLimbDamage(sid)
Damage.Effects:Painkiller(source, tier) > exports['sandbox-damage']:EffectsPainkiller(source, tier)
Damage.Effects:Adrenaline(source, tier) > exports['sandbox-damage']:EffectsAdrenaline(source, tier)

Rewrote Snowballs Component > ExportsS
Client side:

Snowballs:Pickup() > exports['sandbox-xmas']:SnowballsPickup()
Snowballs:CanPickup() > exports['sandbox-xmas']:SnowballsCanPickup()

Rewrote Polyzone Component > Exports
Client side:

Polyzone.Create:Box(id, center, length, width, options, data) > exports['sandbox-polyzone']:CreateBox(id, center, length, width, options, data)
Polyzone.Create:Poly(id, points, options, data) > exports['sandbox-polyzone']:CreatePoly(id, points, options, data)
Polyzone.Create:Circle(id, center, radius, options, data) > exports['sandbox-polyzone']:CreateCircle(id, center, radius, options, data)
Polyzone:Remove(id) > exports['sandbox-polyzone']:Remove(id)
Polyzone:Get(id) > exports['sandbox-polyzone']:Get(id)
Polyzone:GetZoneAtCoords(coords) > exports['sandbox-polyzone']:GetZoneAtCoords(coords)
Polyzone:GetAllZonesAtCoords(coords) > exports['sandbox-polyzone']:GetAllZonesAtCoords(coords)
Polyzone:IsCoordsInZone(coords, id, key, val) > exports['sandbox-polyzone']:IsCoordsInZone(coords, id, key, val)

Rewrote Banking Component > Exports
Server side:

Banking.Accounts:Get(accountNumber) > exports['sandbox-finance']:AccountsGet(accountNumber)
Banking.Accounts:CreatePersonal(ownerSID) > exports['sandbox-finance']:AccountsCreatePersonal(ownerSID)
Banking.Accounts:GetPersonal(ownerSID) > exports['sandbox-finance']:AccountsGetPersonal(ownerSID)
Banking.Accounts:CreatePersonalSavings(ownerSID) > exports['sandbox-finance']:AccountsCreatePersonalSavings(ownerSID)
Banking.Accounts:AddPersonalSavingsJointOwner(accountId, jointOwnerSID) > exports['sandbox-finance']:AccountsAddPersonalSavingsJointOwner(accountId, jointOwnerSID)
Banking.Accounts:RemovePersonalSavingsJointOwner(accountId, jointOwnerSID) > exports['sandbox-finance']:AccountsRemovePersonalSavingsJointOwner(accountId, jointOwnerSID)
Banking.Accounts:GetOrganization(accountId) > exports['sandbox-finance']:AccountsGetOrganization(accountId)
Banking.Balance:Get(accountNumber) > exports['sandbox-finance']:BalanceGet(accountNumber)
Banking.Balance:Has(accountNumber, amount) > exports['sandbox-finance']:BalanceHas(accountNumber, amount)
Banking.Balance:Deposit(accountNumber, amount, transactionLog, skipPhoneNoti) > exports['sandbox-finance']:BalanceDeposit(accountNumber, amount, transactionLog, skipPhoneNoti)
Banking.Balance:Withdraw(accountNumber, amount, transactionLog) > exports['sandbox-finance']:BalanceWithdraw(accountNumber, amount, transactionLog)
Banking.Balance:Charge(accountNumber, amount, transactionLog) > exports['sandbox-finance']:BalanceCharge(accountNumber, amount, transactionLog)
Banking.TransactionLogs:Add(accountNumber, tType, amount, title, description, transactionAccount, data) > exports['sandbox-finance']:TransactionLogsAdd(accountNumber, tType, amount, title, description, transactionAccount, data)

Rewrote Billing Component > Exports
Server side:

Billing:Create(source, name, amount, description, cb) > exports['sandbox-finance']:BillingCreate(source, name, amount, description, cb)
Billing:PlayerCreateOrganizationBill(billingSource, stateId, account, amount, description) > exports['sandbox-finance']:BillingPlayerCreateOrganizationBill(billingSource, stateId, account, amount, description)
Billing:Dismiss(source, billId) > exports['sandbox-finance']:BillingDismiss(source, billId)
Billing:Accept(source, billId, withAccount) > exports['sandbox-finance']:BillingAccept(source, billId, withAccount)
Billing:Fine(finingSource, targetSource, amount) > exports['sandbox-finance']:BillingFine(finingSource, targetSource, amount)
Billing:Charge(source, amount, title, description) > exports['sandbox-finance']:BillingCharge(source, amount, title, description)

Rewrote Crypto Component > Exports
Server side:

Crypto.Coin:Create(name, acronym, price, buyable, sellable) > exports['sandbox-finance']:CryptoCoinCreate(name, acronym, price, buyable, sellable)
Crypto.Coin:Get(acronym) > exports['sandbox-finance']:CryptoCoinGet(acronym)
Crypto.Coin:GetAll() > exports['sandbox-finance']:CryptoCoinGetAll()
Crypto:Has(source, coin, amt) > exports['sandbox-finance']:CryptoHas(source, coin, amt)
Crypto.Exchange:IsListed(coin) > exports['sandbox-finance']:CryptoExchangeIsListed(coin)
Crypto.Exchange:Buy(coin, target, amount) > exports['sandbox-finance']:CryptoExchangeBuy(coin, target, amount)
Crypto.Exchange:Sell(coin, target, amount) > exports['sandbox-finance']:CryptoExchangeSell(coin, target, amount)
Crypto.Exchange:Add(coin, target, amount, skipAlert) > exports['sandbox-finance']:CryptoExchangeAdd(coin, target, amount, skipAlert)
Crypto.Exchange:Remove(coin, target, amount, skipAlert) > exports['sandbox-finance']:CryptoExchangeRemove(coin, target, amount, skipAlert)
Crypto.Exchange:Transfer(coin, sender, target, amount) > exports['sandbox-finance']:CryptoExchangeTransfer(coin, sender, target, amount)

Rewrote Loans Component > Exports
Server side:

Loans:GetAllowedLoanAmount(stateId, type) > exports['sandbox-finance']:LoansGetAllowedLoanAmount(stateId, type)
Loans:GetDefaultInterestRate() > exports['sandbox-finance']:LoansGetDefaultInterestRate()
Loans:GetPlayerLoans(stateId, type) > exports['sandbox-finance']:LoansGetPlayerLoans(stateId, type)
Loans:CreateVehicleLoan(targetSource, VIN, totalCost, downPayment, totalWeeks) > exports['sandbox-finance']:LoansCreateVehicleLoan(targetSource, VIN, totalCost, downPayment, totalWeeks)
Loans:CreatePropertyLoan(targetSource, propertyId, totalCost, downPayment, totalWeeks) > exports['sandbox-finance']:LoansCreatePropertyLoan(targetSource, propertyId, totalCost, downPayment, totalWeeks)
Loans:MakePayment(source, loanId, inAdvanced, advancedPaymentCount) > exports['sandbox-finance']:LoansMakePayment(source, loanId, inAdvanced, advancedPaymentCount)
Loans:HasRemainingPayments(assetType, assetId, checkAge) > exports['sandbox-finance']:LoansHasRemainingPayments(assetType, assetId, checkAge)
Loans.Credit:Get(stateId) > exports['sandbox-finance']:LoansCreditGet(stateId)
Loans.Credit:Set(stateId, newVal) > exports['sandbox-finance']:LoansCreditSet(stateId, newVal)
Loans.Credit:Increase(stateId, increase) > exports['sandbox-finance']:LoansCreditIncrease(stateId, increase)
Loans.Credit:Decrease(stateId, decrease) > exports['sandbox-finance']:LoansCreditDecrease(stateId, decrease)
Loans:HasBeenDefaulted(assetType, assetId) > exports['sandbox-finance']:LoansHasBeenDefaulted(assetType, assetId)

Rewrote Wallet Component > Exports
Server side:

Wallet:Get(source) > exports['sandbox-finance']:WalletGet(source)
Wallet:Has(source, amount) > exports['sandbox-finance']:WalletHas(source, amount)
Wallet:Modify(source, amount, skipNotify) > exports['sandbox-finance']:WalletModify(source, amount, skipNotify)

Rewrote Generator Component > Exports
Server side:

Generator:Color(t) > exports['sandbox-base']:GeneratorColor(t)
Generator.Name:First(t) > exports['sandbox-base']:GeneratorNameFirst(t)
Generator.Name:Last(t) > exports['sandbox-base']:GeneratorNameLast(t)
Generator.Name:Middle(t) > exports['sandbox-base']:GeneratorNameMiddle(t)
Generator:Job(t) > exports['sandbox-base']:GeneratorJob(t)
Generator:Company(t) > exports['sandbox-base']:GeneratorCompany(t)
Generator.Address:City(t) > exports['sandbox-base']:GeneratorAddressCity(t)
Generator.Address:State(t) > exports['sandbox-base']:GeneratorAddressState(t)
Generator.Address:Street(t) > exports['sandbox-base']:GeneratorAddressStreet(t)
Generator.Address:StreetSecondary(t) > exports['sandbox-base']:GeneratorAddressStreetSecondary(t)
Generator.Finance:Account(t) > exports['sandbox-base']:GeneratorFinanceAccount(t)
Generator.Finance:CreditCard(t) > exports['sandbox-base']:GeneratorFinanceCreditCard(t)
Generator.Finance:CryptoAddress(t) > exports['sandbox-base']:GeneratorFinanceCryptoAddress(t)
Generator.Internet:Email(t) > exports['sandbox-base']:GeneratorInternetEmail(t)
Generator.Internet:Avatar(t) > exports['sandbox-base']:GeneratorInternetAvatar(t)
Generator.Internet:Domain(t) > exports['sandbox-base']:GeneratorInternetDomain(t)
Generator.Internet:IP(t) > exports['sandbox-base']:GeneratorInternetIP(t)
Generator.Internet:IPv6(t) > exports['sandbox-base']:GeneratorInternetIPv6(t)
Generator.Internet:MacAddress(t) > exports['sandbox-base']:GeneratorInternetMacAddress(t)
Generator.Date:Past(t) > exports['sandbox-base']:GeneratorDatePast(t)
Generator.Date:Future(t) > exports['sandbox-base']:GeneratorDateFuture(t)
Generator.Date:Recent(t) > exports['sandbox-base']:GeneratorDateRecent(t)
Generator.Date:Soon(t) > exports['sandbox-base']:GeneratorDateSoon(t)
Generator:Phone(t) > exports['sandbox-base']:GeneratorPhone(t)
Generator.Vehicle:MakeModel(t) > exports['sandbox-base']:GeneratorVehicleMakeModel(t)
Generator.Vehicle:Make(t) > exports['sandbox-base']:GeneratorVehicleMake(t)
Generator.Vehicle:Model(t) > exports['sandbox-base']:GeneratorVehicleModel(t)
Generator.Vehicle:Color(t) > exports['sandbox-base']:GeneratorVehicleColor(t)
Generator.Vehicle:VIN(t) > exports['sandbox-base']:GeneratorVehicleVIN(t)
Generator.Vehicle:Plate(t) > exports['sandbox-base']:GeneratorVehiclePlate(t)
Generator.Data:Number(t) > exports['sandbox-base']:GeneratorDataNumber(t)
Generator.Data:Float(t) > exports['sandbox-base']:GeneratorDataFloat(t)
Generator.Data:String(t) > exports['sandbox-base']:GeneratorDataString(t)
Generator.Data:UUID(t) > exports['sandbox-base']:GeneratorDataUUID(t)
Generator.Image:Image(t) > exports['sandbox-base']:GeneratorImageImage(t)
Generator.Image:Avatar(t) > exports['sandbox-base']:GeneratorImageAvatar(t)
Generator.Hacker:Abbreviation(t) > exports['sandbox-base']:GeneratorHackerAbbreviation(t)
Generator.Hacker:Adjective(t) > exports['sandbox-base']:GeneratorHackerAdjective(t)
Generator.Hacker:Noun(t) > exports['sandbox-base']:GeneratorHackerNoun(t)
Generator.Hacker:Verb(t) > exports['sandbox-base']:GeneratorHackerVerb(t)
Generator.Hacker:ingVerb(t) > exports['sandbox-base']:GeneratorHackerIngVerb(t)
Generator.Word:adjective(t) > exports['sandbox-base']:GeneratorWordAdjective(t)
Generator.Word:adverb(t) > exports['sandbox-base']:GeneratorWordAdverb(t)
Generator.Word:noun(t) > exports['sandbox-base']:GeneratorWordNoun(t)
Generator.Word:verb(t) > exports['sandbox-base']:GeneratorWordVerb(t)

Rewrote Jobs Component > Exports
Client side:

Jobs.Permissions:GetJobs() > exports['sandbox-jobs']:GetJobs()
Jobs.Permissions:HasJob(jobId, workplaceId, gradeId, gradeLevel, checkDuty, permissionKey) > exports['sandbox-jobs']:HasJob(jobId, workplaceId, gradeId, gradeLevel, checkDuty, permissionKey)
Jobs.Permissions:GetPermissionsFromJob(jobId, workplaceId) > exports['sandbox-jobs']:GetPermissionsFromJob(jobId, workplaceId)
Jobs.Permissions:HasPermissionInJob(jobId, permissionKey) > exports['sandbox-jobs']:HasPermissionInJob(jobId, permissionKey)
Jobs.Permissions:HasPermission(permissionKey) > exports['sandbox-jobs']:HasPermission(permissionKey)
Jobs.Duty:On(jobId, cb) > exports['sandbox-jobs']:DutyOn(jobId, cb)
Jobs.Duty:Off(jobId, cb) > exports['sandbox-jobs']:DutyOff(jobId, cb)
Jobs.Duty:Get(jobId) > exports['sandbox-jobs']:DutyGet(jobId)

Server side:

Jobs:GetAll() > exports['sandbox-jobs']:GetAll()
Jobs:Get(jobId) > exports['sandbox-jobs']:Get(jobId)
Jobs:DoesExist(jobId, workplaceId, gradeId) > exports['sandbox-jobs']:DoesExist(jobId, workplaceId, gradeId)
Jobs:GiveJob(stateId, jobId, workplaceId, gradeId, noOverride) > exports['sandbox-jobs']:GiveJob(stateId, jobId, workplaceId, gradeId, noOverride)
Jobs:RemoveJob(stateId, jobId) > exports['sandbox-jobs']:RemoveJob(stateId, jobId)
Jobs.Duty:On(source, jobId, hideNotify) > exports['sandbox-jobs']:DutyOn(source, jobId, hideNotify)
Jobs.Duty:Off(source, jobId, hideNotify) > exports['sandbox-jobs']:DutyOff(source, jobId, hideNotify)
Jobs.Duty:Get(source, jobId) > exports['sandbox-jobs']:DutyGet(source, jobId)
Jobs.Duty:GetDutyData(jobId) > exports['sandbox-jobs']:DutyGetDutyData(jobId)
Jobs.Duty:RefreshDutyData(jobId) > exports['sandbox-jobs']:DutyRefreshDutyData(jobId)
Jobs.Permissions:IsOwner(source, jobId) > exports['sandbox-jobs']:IsOwner(source, jobId)
Jobs.Permissions:IsOwnerOfCompany(source) > exports['sandbox-jobs']:IsOwnerOfCompany(source)
Jobs.Permissions:GetJobs(source) > exports['sandbox-jobs']:GetJobs(source)
Jobs.Permissions:HasJob(source, jobId, workplaceId, gradeId, gradeLevel, checkDuty, permissionKey) > exports['sandbox-jobs']:HasJob(source, jobId, workplaceId, gradeId, gradeLevel, checkDuty, permissionKey)
Jobs.Permissions:GetPermissionsFromJob(source, jobId, workplaceId) > exports['sandbox-jobs']:GetPermissionsFromJob(source, jobId, workplaceId)
Jobs.Permissions:HasPermissionInJob(source, jobId, permissionKey) > exports['sandbox-jobs']:HasPermissionInJob(source, jobId, permissionKey)
Jobs.Permissions:GetAllPermissions(source) > exports['sandbox-jobs']:GetAllPermissions(source)
Jobs.Permissions:HasPermission(source, permissionKey) > exports['sandbox-jobs']:HasPermission(source, permissionKey)
Jobs.Management:Create(name, ownerSID) > exports['sandbox-jobs']:ManagementCreate(name, ownerSID)
Jobs.Management:Transfer(jobId, newOwner) > exports['sandbox-jobs']:ManagementTransfer(jobId, newOwner)
Jobs.Management.Upgrades:Has(jobId, upgradeKey) > exports['sandbox-jobs']:ManagementUpgradesHas(jobId, upgradeKey)
Jobs.Management.Upgrades:Unlock(jobId, upgradeKey) > exports['sandbox-jobs']:ManagementUpgradesUnlock(jobId, upgradeKey)
Jobs.Management.Upgrades:Lock(jobId, upgradeKey) > exports['sandbox-jobs']:ManagementUpgradesLock(jobId, upgradeKey)
Jobs.Management.Upgrades:Reset(jobId) > exports['sandbox-jobs']:ManagementUpgradesReset(jobId)
Jobs.Management:Delete(jobId) > exports['sandbox-jobs']:ManagementDelete(jobId)
Jobs.Management:Edit(jobId, settingData) > exports['sandbox-jobs']:ManagementEdit(jobId, settingData)
Jobs.Management.Workplace:Edit(jobId, workplaceId, newWorkplaceName) > exports['sandbox-jobs']:ManagementWorkplaceEdit(jobId, workplaceId, newWorkplaceName)
Jobs.Management.Grades:Create(jobId, workplaceId, gradeName, gradeLevel, gradePermissions) > exports['sandbox-jobs']:ManagementGradesCreate(jobId, workplaceId, gradeName, gradeLevel, gradePermissions)
Jobs.Management.Grades:Edit(jobId, workplaceId, gradeId, settingData) > exports['sandbox-jobs']:ManagementGradesEdit(jobId, workplaceId, gradeId, settingData)
Jobs.Management.Grades:Delete(jobId, workplaceId, gradeId) > exports['sandbox-jobs']:ManagementGradesDelete(jobId, workplaceId, gradeId)
Jobs.Management.Employees:GetAll(jobId, workplaceId, gradeId) > exports['sandbox-jobs']:ManagementEmployeesGetAll(jobId, workplaceId, gradeId)
Jobs.Management.Employees:UpdateAllJob(jobId, newJobName) > exports['sandbox-jobs']:ManagementEmployeesUpdateAllJob(jobId, newJobName)
Jobs.Management.Employees:UpdateAllWorkplace(jobId, workplaceId, newWorkplaceName) > exports['sandbox-jobs']:ManagementEmployeesUpdateAllWorkplace(jobId, workplaceId, newWorkplaceName)
Jobs.Management.Employees:UpdateAllGrade(jobId, workplaceId, gradeId, settingData) > exports['sandbox-jobs']:ManagementEmployeesUpdateAllGrade(jobId, workplaceId, gradeId, settingData)
Jobs.Data:Set(jobId, key, val) > exports['sandbox-jobs']:DataSet(jobId, key, val)
Jobs.Data:Get(jobId, key) > exports['sandbox-jobs']:DataGet(jobId, key)

Rewrote Apartment Component > Exports
Client side:

Apartment:Enter(tier, id) > exports['sandbox-apartments']:Enter(tier, id)
Apartment:Exit() > exports['sandbox-apartments']:Exit()
Apartment:GetNearApartment() > exports['sandbox-apartments']:GetNearApartment()
Apartment.Extras:Stash() > exports['sandbox-apartments']:ExtrasStash()
Apartment.Extras:Wardrobe() > exports['sandbox-apartments']:ExtrasWardrobe()
Apartment.Extras:Logout() > exports['sandbox-apartments']:ExtrasLogout()

Server side:

Apartment:Enter(source, targetType, target, wakeUp) > exports['sandbox-apartments']:Enter(source, targetType, target, wakeUp)
Apartment:Exit(source) > exports['sandbox-apartments']:Exit(source)
Apartment:GetInteriorLocation(apartment) > exports['sandbox-apartments']:GetInteriorLocation(apartment)
Apartment.Requests:Get(source) > exports['sandbox-apartments']:RequestsGet(source)
Apartment.Requests:Create(source, target, inZone) > exports['sandbox-apartments']:RequestsCreate(source, target, inZone)

Rewrote Characters Component > Exports
Client side:

Characters.Logout() > exports['sandbox-characters']:Logout()

Rewrote Locations Component > Exports
Client side:

Locations:GetAll(type, cb) > exports['sandbox-locations']:GetAll(type, cb)

Server side:

Locations:Add(coords, heading, type, name, cb) > exports['sandbox-locations']:Add(coords, heading, type, name, cb)
Locations:GetAll(type, cb) > exports['sandbox-locations']:GetAll(type, cb)

Rewrote Mechanic Component > Exports
Client side:

Mechanic:CanAccessVehicleAsMechanic(vehicle) > exports['sandbox-mechanic']:CanAccessVehicleAsMechanic(vehicle)

Rewrote Admin Component > Exports
Client side:

Admin:OpenMenu() > exports['sandbox-admin']:OpenMenu()
Admin:CopyClipboard(txt) > exports['sandbox-admin']:CopyClipboard(txt)
Admin.NoClip:Toggle(mode) > exports['sandbox-admin']:NoClipToggle(mode)
Admin.NoClip:Start() > exports['sandbox-admin']:NoClipStart()
Admin.NoClip:Stop() > exports['sandbox-admin']:NoClipStop()
Admin.NoClip:IsActive() > exports['sandbox-admin']:NoClipIsActive()
Admin.NoClip:GetPos() > exports['sandbox-admin']:NoClipGetPos()

Rewrote Config Component > Exports
Server side:

COMPONENTS.Config.Discord > exports['sandbox-base']:ConfigGetDiscord()
COMPONENTS.Config.Groups > exports['sandbox-base']:ConfigGetGroups()
COMPONENTS.Config.Server > exports['sandbox-base']:ConfigGetServer()
COMPONENTS.Config.Groups[groupId] > exports['sandbox-base']:ConfigGetGroupById(groupId)
COMPONENTS.Config.Groups[groupId].Permission > exports['sandbox-base']:ConfigGetGroupPermission(groupId)
COMPONENTS.Config.Groups[groupId].Queue.Priority > exports['sandbox-base']:ConfigGetGroupQueuePriority(groupId)

Rewrote Casino Component > Exports
Server side:

Casino.Chips:Get(source) > exports['sandbox-casino']:ChipsGet(source)
Casino.Chips:Has(source, amount) > exports['sandbox-casino']:ChipsHas(source, amount)
Casino.Chips:Modify(source, amount) > exports['sandbox-casino']:ChipsModify(source, amount)
Casino.Config:Set(key, data) > exports['sandbox-casino']:ConfigSet(key, data)
Casino.Config:Get(key) > exports['sandbox-casino']:ConfigGet(key)

Rewrote Radar Component > Exports
Server side:

Radar:AddFlaggedPlate(plate, reason) > exports['sandbox-radar']:AddFlaggedPlate(plate, reason)
Radar:RemoveFlaggedPlate(plate) > exports['sandbox-radar']:RemoveFlaggedPlate(plate)
Radar:ClearFlaggedPlates() > exports['sandbox-radar']:ClearFlaggedPlates()
Radar:GetFlaggedPlates() > exports['sandbox-radar']:GetFlaggedPlates()
Radar:CheckPlate(plate) > exports['sandbox-radar']:CheckPlate(plate)

Rewrote EmergencyAlerts Component > Exports
Client side:

EmergencyAlerts:Open() > exports['sandbox-mdt']:EmergencyAlertsOpen()
EmergencyAlerts:Close() > exports['sandbox-mdt']:EmergencyAlertsClose()
EmergencyAlerts:CreateIfReported(...) > exports['sandbox-mdt']:EmergencyAlertsCreateIfReported(...)
EmergencyAlerts:CreateClientAlert(...) > exports['sandbox-mdt']:EmergencyAlertsCreateClientAlert(...)

Server side:

EmergencyAlerts:Create(...) > exports['sandbox-mdt']:EmergencyAlertsCreate(...)
EmergencyAlerts:OnDuty(...) > exports['sandbox-mdt']:EmergencyAlertsOnDuty(...)
EmergencyAlerts:GetUnitData(...) > exports['sandbox-mdt']:EmergencyAlertsGetUnitData(...)
EmergencyAlerts:OffDuty(...) > exports['sandbox-mdt']:EmergencyAlertsOffDuty(...)
EmergencyAlerts:DisableTracker(...) > exports['sandbox-mdt']:EmergencyAlertsDisableTracker(...)
EmergencyAlerts:RefreshCallsign(...) > exports['sandbox-mdt']:EmergencyAlertsRefreshCallsign(...)
EmergencyAlerts:SendMemberUpdates() > exports['sandbox-mdt']:EmergencyAlertsSendMemberUpdates()
EmergencyAlerts:SendOnDutyEvent(...) > exports['sandbox-mdt']:EmergencyAlertsSendOnDutyEvent(...)

Rewrote MDT Component > Exports
Client side:

MDT:Open() > exports['sandbox-mdt']:Open()
MDT:Close() > exports['sandbox-mdt']:Close()
MDT.Data:Set(key, data) > exports['sandbox-mdt']:DataSet(key, data)
MDT.Data:Add(type, data, key) > exports['sandbox-mdt']:DataAdd(type, data, key)
MDT.Data:Update(type, id, data) > exports['sandbox-mdt']:DataUpdate(type, id, data)
MDT.Data:Remove(key, id) > exports['sandbox-mdt']:DataRemove(key, id)
MDT.Data:Reset() > exports['sandbox-mdt']:DataReset()
MDT.Badges:Open(data) > exports['sandbox-mdt']:BadgesOpen(data)
MDT.Badges:Close() > exports['sandbox-mdt']:BadgesClose()
MDT.Licenses:Open(data) > exports['sandbox-mdt']:LicensesOpen(data)
MDT.Licenses:Close() > exports['sandbox-mdt']:LicensesClose()

Server side:

MDT.Firearm:Search(term) > exports['sandbox-mdt']:FirearmSearch(term)
MDT.Firearm:View(id) > exports['sandbox-mdt']:FirearmView(id)
MDT.Firearm.Flags:Add(firearmSerial, data, author) > exports['sandbox-mdt']:FirearmFlagsAdd(firearmSerial, data, author)
MDT.Firearm.Flags:Remove(firearmSerial, flagId) > exports['sandbox-mdt']:FirearmFlagsRemove(firearmSerial, flagId)
MDT.Library:Create(label, link, job, workplace) > exports['sandbox-mdt']:LibraryCreate(label, link, job, workplace)
MDT.Library:Delete(id) > exports['sandbox-mdt']:LibraryDelete(id)
MDT.Misc.Create:BOLO(data) > exports['sandbox-mdt']:MiscCreateBOLO(data)
MDT.Misc.Create:Charge(data) > exports['sandbox-mdt']:MiscCreateCharge(data)
MDT.Misc.Create:Notice(data) > exports['sandbox-mdt']:MiscCreateNotice(data)
MDT.Misc.View:Notice(id) > exports['sandbox-mdt']:MiscViewNotice(id)
MDT.Misc.Update:Charge(id, data) > exports['sandbox-mdt']:MiscUpdateCharge(id, data)
MDT.Misc.Delete:BOLO(id) > exports['sandbox-mdt']:MiscDeleteBOLO(id)
MDT.Misc.Delete:Notice(id) > exports['sandbox-mdt']:MiscDeleteNotice(id)
MDT.Misc.Delete:Charge(id) > exports['sandbox-mdt']:MiscDeleteCharge(id)
MDT.People.Search:People(term) > exports['sandbox-mdt']:PeopleSearchPeople(term)
MDT.People:View(id, requireAllData) > exports['sandbox-mdt']:PeopleView(id, requireAllData)
MDT.People:Update(requester, id, key, value) > exports['sandbox-mdt']:PeopleUpdate(requester, id, key, value)
MDT.Reports:Search(term, rType, page, perPage, isAttorney, evidence) > exports['sandbox-mdt']:ReportsSearch(term, rType, page, perPage, isAttorney, evidence)
MDT.Reports:SearchEvidence(term) > exports['sandbox-mdt']:ReportsSearchEvidence(term)
MDT.Reports:View(id) > exports['sandbox-mdt']:ReportsView(id)
MDT.Reports:Create(data) > exports['sandbox-mdt']:ReportsCreate(data)
MDT.Reports:Update(id, char, report) > exports['sandbox-mdt']:ReportsUpdate(id, char, report)
MDT.Reports:Delete(id) > exports['sandbox-mdt']:ReportsDelete(id)
MDT.Vehicles:Search(term, page, perPage) > exports['sandbox-mdt']:VehiclesSearch(term, page, perPage)
MDT.Vehicles:View(VIN) > exports['sandbox-mdt']:VehiclesView(VIN)
MDT.Vehicles.Flags:Add(VIN, data, plate) > exports['sandbox-mdt']:VehiclesFlagsAdd(VIN, data, plate)
MDT.Vehicles.Flags:Remove(VIN, flag, plate, removeRadarFlag) > exports['sandbox-mdt']:VehiclesFlagsRemove(VIN, flag, plate, removeRadarFlag)
MDT.Vehicles:UpdateStrikes(VIN, strikes) > exports['sandbox-mdt']:VehiclesUpdateStrikes(VIN, strikes)
MDT.Vehicles:GetStrikes(VIN) > exports['sandbox-mdt']:VehiclesGetStrikes(VIN)
MDT.Warrants:Search(term, page, perPage) > exports['sandbox-mdt']:WarrantsSearch(term, page, perPage)
MDT.Warrants:View(id) > exports['sandbox-mdt']:WarrantsView(id)
MDT.Warrants:Create(report, suspect, notes, author) > exports['sandbox-mdt']:WarrantsCreate(report, suspect, notes, author)
MDT.Warrants:Update(id, state) > exports['sandbox-mdt']:WarrantsUpdate(id, state)

Rewrote CCTV Component > Exports
Client side:

CCTV:View(camId) > exports['sandbox-cctv']:View(camId)
CCTV:Close() > exports['sandbox-cctv']:Close()

Server side:

CCTV:View(source, camId) > exports['sandbox-cctv']:View(source, camId)
CCTV:ViewGroup(source, camGroup) > exports['sandbox-cctv']:ViewGroup(source, camGroup)
CCTV.State:Online(camId) > exports['sandbox-cctv']:StateOnline(camId)
CCTV.State:Offline(camId) > exports['sandbox-cctv']:StateOffline(camId)
CCTV.State.Group:Online(groupId) > exports['sandbox-cctv']:StateGroupOnline(groupId)
CCTV.State.Group:Offline(groupId) > exports['sandbox-cctv']:StateGroupOffline(groupId)

Rewrote EMS, Police & Handcuffs Components > Exports
Client side:

EMS:HaveEvaluated(id) > exports['sandbox-police']:HaveEvaluated(id)
Police:IsPdCar(entity) > exports['sandbox-police']:IsPdCar(entity)
Police:IsEMSCar(entity) > exports['sandbox-police']:IsEMSCar(entity)

Server side:

Handcuffs:SelfToggle(source) > exports['sandbox-police']:SelfToggle(source)
Handcuffs:ToggleCuffs(source) > exports['sandbox-police']:ToggleCuffs(source)
Handcuffs:SoftCuff(source) > exports['sandbox-police']:SoftCuff(source)
Handcuffs:SoftCuffTarget(source, target, forced) > exports['sandbox-police']:SoftCuffTarget(source, target, forced)
Handcuffs:HardCuff(source) > exports['sandbox-police']:HardCuff(source)
Handcuffs:HardCuffTarget(source, target, forced) > exports['sandbox-police']:HardCuffTarget(source, target, forced)
Handcuffs:Uncuff(source) > exports['sandbox-police']:Uncuff(source)
Handcuffs:UncuffTarget(source, target) > exports['sandbox-police']:UncuffTarget(source, target)
Police:IsInBreach(source, type, id, extraCheck) > exports['sandbox-police']:IsInBreach(source, type, id, extraCheck)
Police:RunPlate(source, plate, wasEntity) > exports['sandbox-police']:RunPlate(source, plate, wasEntity)
Police:IsPdCar(model) > exports['sandbox-police']:IsPdCar(model)
Police:IsEMSCar(model) > exports['sandbox-police']:IsEMSCar(model)

Rewrote Labor Component > Exports
Client side:

Labor.Get:Jobs() > exports['sandbox-labor']:GetJobs()
Labor.Get:Groups() > exports['sandbox-labor']:GetGroups()
Labor.Get:Reputations() > exports['sandbox-labor']:GetReputations()

Server side:

Labor.Get:Jobs() > exports['sandbox-labor']:GetJobs()
Labor.Get:Groups() > exports['sandbox-labor']:GetGroups()
Labor.Jobs:Register(id, name, limit, salary, repAward, restrictions, customRep, hiddenRep, timeout) > exports['sandbox-labor']:RegisterJob(id, name, limit, salary, repAward, restrictions, customRep, hiddenRep, timeout)
Labor.Offers:Task(joiner, job, text, appOverride) > exports['sandbox-labor']:TaskOffer(joiner, job, text, appOverride)
Labor.Offers:Start(joiner, job, text, max, appOverride) > exports['sandbox-labor']:StartOffer(joiner, job, text, max, appOverride)
Labor.Offers:Update(joiner, job, change, skipFinish, appOverride) > exports['sandbox-labor']:UpdateOffer(joiner, job, change, skipFinish, appOverride)
Labor.Offers:Complete(source, job) > exports['sandbox-labor']:CompleteOffer(source, job)
Labor.Offers:ManualFinish(joiner, job, appOverride) > exports['sandbox-labor']:ManualFinishOffer(joiner, job, appOverride)
Labor.Offers:Fail(joiner, job, timeout) > exports['sandbox-labor']:FailOffer(joiner, job, timeout)
Labor.Offers:Cancel(joiner, job) > exports['sandbox-labor']:CancelOffer(joiner, job)
Labor.Workgroups:Create(source) > exports['sandbox-labor']:CreateWorkgroup(source)
Labor.Workgroups:Disband(source, force) > exports['sandbox-labor']:DisbandWorkgroup(source, force)
Labor.Workgroups:Join(creator, source) > exports['sandbox-labor']:JoinWorkgroup(creator, source)
Labor.Workgroups:Request(group, source) > exports['sandbox-labor']:RequestWorkgroup(group, source)
Labor.Workgroups:Leave(group, source) > exports['sandbox-labor']:LeaveWorkgroup(group, source)
Labor.Workgroups:SendEvent(joiner, event, ...) > exports['sandbox-labor']:SendWorkgroupEvent(joiner, event, ...)
Labor.Duty:On(job, joiner, isWorkgroup, data) > exports['sandbox-labor']:OnDuty(job, joiner, isWorkgroup, data)
Labor.Duty:Off(job, joiner, wasFinished, noAlert) > exports['sandbox-labor']:OffDuty(job, joiner, wasFinished, noAlert)
Labor.Jail:Sentenced(source) > exports['sandbox-labor']:JailSentenced(source)
Labor.Jail:Released(source) > exports['sandbox-labor']:JailReleased(source)

Rewrote Tow Component > Exports
Client side:

Tow:IsTowTruck(entity) > exports['sandbox-tow']:IsTowTruck(entity)

Server side:

Tow:PayoutPickup(source) > exports['sandbox-tow']:PayoutPickup(source)
Tow:CleanupPickup(source) > exports['sandbox-tow']:CleanupPickup(source)

Rewrote Jail Component > Exports
Client side:

Jail:IsJailed() > exports['sandbox-jail']:IsJailed()
Jail:IsReleaseEligible() > exports['sandbox-jail']:IsReleaseEligible()

Server side:

Jail:IsJailed(source) > exports['sandbox-jail']:IsJailed(source)
Jail:IsReleaseEligible(source) > exports['sandbox-jail']:IsReleaseEligible(source)
Jail:Sentence(source, target, duration) > exports['sandbox-jail']:Sentence(source, target, duration)
Jail:Reduce(source, reduction) > exports['sandbox-jail']:Reduce(source, reduction)
Jail:Release(source) > exports['sandbox-jail']:Release(source)
Jail:GetPrisoners() > exports['sandbox-jail']:GetPrisoners()

Rewrote Dealerships Component > Exports
(I was wrong, server side did get used...)

Server side:

Dealerships.Donator:AddPending(playerIdentifier, class, data) > exports['sandbox-dealerships']:DonatorAddPending(playerIdentifier, class, data)
Dealerships.Donator:GetPending(playerIdentifier, includeRedeemed) > exports['sandbox-dealerships']:DonatorGetPending(playerIdentifier, includeRedeemed)
Dealerships.Donator:RemovePending(playerIdentifier, id) > exports['sandbox-dealerships']:DonatorRemovePending(playerIdentifier, id)
Dealerships.Donator:DeletePending(playerIdentifier, id) > exports['sandbox-dealerships']:DonatorDeletePending(playerIdentifier, id)
Dealerships.Management:LoadData() > exports['sandbox-dealerships']:ManagementLoadData()
Dealerships.Management:SetData(dealerId, key, val) > exports['sandbox-dealerships']:ManagementSetData(dealerId, key, val)
Dealerships.Management:SetMultipleData(dealerId, updatingData) > exports['sandbox-dealerships']:ManagementSetMultipleData(dealerId, updatingData)
Dealerships.Management:GetAllData(dealerId) > exports['sandbox-dealerships']:ManagementGetAllData(dealerId)
Dealerships.Management:GetData(dealerId, key) > exports['sandbox-dealerships']:ManagementGetData(dealerId, key)
Dealerships.Records:Get(dealership) > exports['sandbox-dealerships']:RecordsGet(dealership)
Dealerships.Records:GetPage(category, term, dealership, page, perPage) > exports['sandbox-dealerships']:RecordsGetPage(category, term, dealership, page, perPage)
Dealerships.Records:Create(dealership, document) > exports['sandbox-dealerships']:RecordsCreate(dealership, document)
Dealerships.Records:CreateBuyBack(dealership, document) > exports['sandbox-dealerships']:RecordsCreateBuyBack(dealership, document)
Dealerships.Showroom:Load() > exports['sandbox-dealerships']:ShowroomLoad()
Dealerships.Showroom:Update(dealershipId, showroom) > exports['sandbox-dealerships']:ShowroomUpdate(dealershipId, showroom)
Dealerships.Showroom:UpdatePos(dealershipId, position, vehicleData) > exports['sandbox-dealerships']:ShowroomUpdatePos(dealershipId, position, vehicleData)
Dealerships.Stock:FetchAll() > exports['sandbox-dealerships']:StockFetchAll()
Dealerships.Stock:FetchDealer(dealerId) > exports['sandbox-dealerships']:StockFetchDealer(dealerId)
Dealerships.Stock:FetchDealerVehicle(dealerId, vehModel) > exports['sandbox-dealerships']:StockFetchDealerVehicle(dealerId, vehModel)
Dealerships.Stock:HasVehicle(dealerId, vehModel) > exports['sandbox-dealerships']:StockHasVehicle(dealerId, vehModel)
Dealerships.Stock:Add(dealerId, vehModel, modelType, quantity, vehData) > exports['sandbox-dealerships']:StockAdd(dealerId, vehModel, modelType, quantity, vehData)
Dealerships.Stock:Increase(dealerId, vehModel, amount) > exports['sandbox-dealerships']:StockIncrease(dealerId, vehModel, amount)
Dealerships.Stock:Update(dealerId, vehModel, setting) > exports['sandbox-dealerships']:StockUpdate(dealerId, vehModel, setting)
Dealerships.Stock:Ensure(dealerId, vehModel, quantity, vehData) > exports['sandbox-dealerships']:StockEnsure(dealerId, vehModel, quantity, vehData)
Dealerships.Stock:Remove(dealerId, vehModel, quantity) > exports['sandbox-dealerships']:StockRemove(dealerId, vehModel, quantity)

Rewrote Robbery Component > Exports
Server side:

Robbery:TriggerPDAlert(source, coords, code, title, blip, description, cameraGroup, isArea) > exports['sandbox-robbery']:TriggerPDAlert(source, coords, code, title, blip, description, cameraGroup, isArea)
Robbery:GetAccessCodes(bankId) > exports['sandbox-robbery']:RobberyGetAccessCodes(bankId)
Robbery.State:Set(bank, state) > exports['sandbox-robbery']:StateSet(bank, state)
Robbery.State:Update(bank, key, value, tableId) > exports['sandbox-robbery']:StateUpdate(bank, key, value, tableId)

Rewrote Taxi Component > Exports
Client side:

Taxi.Hud:Show() > exports['sandbox-taxi']:HudShow()
Taxi.Hud:Hide() > exports['sandbox-taxi']:HudHide()
Taxi.Hud:Reset() > exports['sandbox-taxi']:HudReset()
Taxi.Hud:Toggle() > exports['sandbox-taxi']:HudToggle()
Taxi.Rate:Increase() > exports['sandbox-taxi']:RateIncrease()
Taxi.Rate:Decrease() > exports['sandbox-taxi']:RateDecrease()
Taxi.Trip:Reset() > exports['sandbox-taxi']:TripReset()

Rewrote Drugs Component > Exports
Server side:

Drugs.Meth:GenerateTable(tier) > exports['sandbox-drugs']:MethGenerateTable(tier)
Drugs.Meth:GetTable(tableId) > exports['sandbox-drugs']:MethGetTable(tableId)
Drugs.Meth:IsTablePlaced(tableId) > exports['sandbox-drugs']:MethIsTablePlaced(tableId)
Drugs.Meth:CreatePlacedTable(tableId, owner, tier, coords, heading, created) > exports['sandbox-drugs']:MethCreatePlacedTable(tableId, owner, tier, coords, heading, created)
Drugs.Meth:RemovePlacedTable(tableId) > exports['sandbox-drugs']:MethRemovePlacedTable(tableId)
Drugs.Meth:StartTableCook(tableId, cooldown, recipe) > exports['sandbox-drugs']:MethStartTableCook(tableId, cooldown, recipe)
Drugs.Meth:FinishTableCook(tableId) > exports['sandbox-drugs']:MethFinishTableCook(tableId)
Drugs.Moonshine.Still:Generate(tier) > exports['sandbox-drugs']:MoonshineStillGenerate(tier)
Drugs.Moonshine.Still:Get(stillId) > exports['sandbox-drugs']:MoonshineStillGet(stillId)
Drugs.Moonshine.Still:IsPlaced(stillId) > exports['sandbox-drugs']:MoonshineStillIsPlaced(stillId)
Drugs.Moonshine.Still:CreatePlaced(stillId, owner, tier, coords, heading, created) > exports['sandbox-drugs']:MoonshineStillCreatePlaced(stillId, owner, tier, coords, heading, created)
Drugs.Moonshine.Still:RemovePlaced(stillId) > exports['sandbox-drugs']:MoonshineStillRemovePlaced(stillId)
Drugs.Moonshine.Still:StartCook(stillId, cooldown, results) > exports['sandbox-drugs']:MoonshineStillStartCook(stillId, cooldown, results)
Drugs.Moonshine.Still:FinishCook(stillId) > exports['sandbox-drugs']:MoonshineStillFinishCook(stillId)
Drugs.Moonshine.Barrel:Generate() > exports['sandbox-drugs']:MoonshineBarrelGenerate()
Drugs.Moonshine.Barrel:IsPlaced(barrelId) > exports['sandbox-drugs']:MoonshineBarrelIsPlaced(barrelId)
Drugs.Moonshine.Barrel:CreatePlaced(owner, coords, heading, created, brewData) > exports['sandbox-drugs']:MoonshineBarrelCreatePlaced(owner, coords, heading, created, brewData)
Drugs.Moonshine.Barrel:RemovePlaced(barrelId) > exports['sandbox-drugs']:MoonshineBarrelRemovePlaced(barrelId)
Drugs.Addiction:Add(source, drug, factor) > exports['sandbox-drugs']:AddictionAdd(source, drug, factor)
Drugs.Addiction:Remove(source, drug, factor) > exports['sandbox-drugs']:AddictionRemove(source, drug, factor)DRUGS.Addiction:Reset(source, drug) > exports['sandbox-drugs']:AddictionReset(source, drug)

Rewrote Weed Component > Exports
Server side:

Weed.Planting:Set(id, isUpdate, skipEvent) > exports['sandbox-weed']:PlantingSet(id, isUpdate, skipEvent)
Weed.Planting:Delete(id, skipRemove) > exports['sandbox-weed']:PlantingDelete(id, skipRemove)
Weed.Planting:Create(isMale, location, material) > exports['sandbox-weed']:PlantingCreate(isMale, location, material)

Rewrote Properties Component > Exports
Client side:

Properties:Enter(id) > exports['sandbox-properties']:Enter(id)
Properties:GetProperties() > exports['sandbox-properties']:GetProperties()
Properties:GetPropertiesWithAccess() > exports['sandbox-properties']:GetPropertiesWithAccess()
Properties:Get(pId) > exports['sandbox-properties']:Get(pId)
Properties:GetUpgradesConfig() > exports['sandbox-properties']:GetUpgradesConfig()
Properties:GetNearHouse() > exports['sandbox-properties']:GetNearHouse()
Properties:GetNearHouseBackdoor() > exports['sandbox-properties']:GetNearHouseBackdoor()
Properties:GetNearHouseGarage(coordOverride) > exports['sandbox-properties']:GetNearHouseGarage(coordOverride)
Properties:GetInside() > exports['sandbox-properties']:GetInside()
Properties.Extras:Stash() > exports['sandbox-properties']:Stash()
Properties.Extras:Closet() > exports['sandbox-properties']:Closet()
Properties.Extras:Logout() > exports['sandbox-properties']:Logout()
Properties.Keys:HasAccessWithData(key, value) > exports['sandbox-properties']:HasAccessWithData(key, value)
Properties.Furniture:GetCurrent(property) > exports['sandbox-properties']:GetCurrent(property)
Properties.Furniture:EditMode(state) > exports['sandbox-properties']:EditMode(state)
Properties.Furniture:Place(model, category, metadata, blockBrowse, skipPhone, startCoords, startRot) > exports['sandbox-properties']:Place(model, category, metadata, blockBrowse, skipPhone, startCoords, startRot)
Properties.Furniture:Move(id, skipPhone) > exports['sandbox-properties']:Move(id, skipPhone)
Properties.Furniture:Delete(id) > exports['sandbox-properties']:Delete(id)
Properties.Interiors:Preview(int) > exports['sandbox-properties']:Preview(int)

Server side:

Properties.Manage:Add(source, type, interior, price, label, pos) > exports['sandbox-properties']:Add(source, type, interior, price, label, pos)
Properties.Manage:AddFrontdoor(id, pos) > exports['sandbox-properties']:AddFrontdoor(id, pos)
Properties.Manage:AddBackdoor(id, pos) > exports['sandbox-properties']:AddBackdoor(id, pos)
Properties.Manage:AddGarage(id, pos) > exports['sandbox-properties']:AddGarage(id, pos)
Properties.Manage:SetLabel(id, label) > exports['sandbox-properties']:SetLabel(id, label)
Properties.Manage:SetPrice(id, price) > exports['sandbox-properties']:SetPrice(id, price)
Properties.Manage:SetData(id, key, value) > exports['sandbox-properties']:SetData(id, key, value)
Properties.Manage:Delete(id) > exports['sandbox-properties']:Delete(id)
Properties.Upgrades:Set(id, upgrade, level) > exports['sandbox-properties']:UpgradeSet(id, upgrade, level)
Properties.Upgrades:Get(id, upgrade) > exports['sandbox-properties']:UpgradeGet(id, upgrade)
Properties.Upgrades:Increase(id, upgrade) > exports['sandbox-properties']:UpgradeIncrease(id, upgrade)
Properties.Upgrades:Decrease(id, upgrade) > exports['sandbox-properties']:UpgradeDecrease(id, upgrade)
Properties.Upgrades:SetInterior(id, interior) > exports['sandbox-properties']:UpgradeSetInterior(id, interior)
Properties.Commerce:Sell(id) > exports['sandbox-properties']:Sell(id)
Properties.Commerce:Buy(id, owner, payment) > exports['sandbox-properties']:Buy(id, owner, payment)
Properties.Commerce:Foreclose(id, state) > exports['sandbox-properties']:Foreclose(id, state)
Properties.Utils:IsNearProperty(source) > exports['sandbox-properties']:IsNearProperty(source)
Properties.Utils:SetLock(id, locked) > exports['sandbox-properties']:SetLock(id, locked)
Properties.Utils:ToggleLock(id) > exports['sandbox-properties']:ToggleLock(id)
Properties.Keys:Give(charData, id, isOwner, permissions, updating) > exports['sandbox-properties']:GiveKey(charData, id, isOwner, permissions, updating)
Properties.Keys:Take(target, id) > exports['sandbox-properties']:TakeKey(target, id)
Properties.Keys:Has(id, charId) > exports['sandbox-properties']:HasKey(id, charId)
Properties.Keys:HasBySID(id, stateId) > exports['sandbox-properties']:HasKeyBySID(id, stateId)
Properties.Keys:HasAccessWithData(source, key, value) > exports['sandbox-properties']:HasAccessWithData(source, key, value)
Properties:Get(propertyId) > exports['sandbox-properties']:Get(propertyId)
Properties:ForceEveryoneLeave(propertyId) > exports['sandbox-properties']:ForceEveryoneLeave(propertyId)
Properties:GetMaxParkingSpaces(propertyId) > exports['sandbox-properties']:GetMaxParkingSpaces(propertyId)

Rewrote Laptop Component > Exports
Client side:

Laptop:Open() > exports['sandbox-laptop']:Open()
Laptop:Close(forced) > exports['sandbox-laptop']:Close(forced)
Laptop:IsOpen() > exports['sandbox-laptop']:IsOpen()
Laptop:ResetRoute() > exports['sandbox-laptop']:ResetRoute()
Laptop.Permissions:Load(p) > exports['sandbox-laptop']:LoadPermissions(p)
Laptop:IsAppUsable(app) > exports['sandbox-laptop']:IsAppUsable(app)
Laptop.Data:Set(key, data) > exports['sandbox-laptop']:SetData(key, data)
Laptop.Data:Add(type, data, key) > exports['sandbox-laptop']:AddData(type, data, key)
Laptop.Data:Update(type, id, data) > exports['sandbox-laptop']:UpdateData(type, id, data)
Laptop.Data:Remove(key, id) > exports['sandbox-laptop']:RemoveData(key, id)
Laptop.Data:Reset() > exports['sandbox-laptop']:ResetData()
Laptop.Notification:Add(title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:AddNotification(title, description, time, duration, app, actions, notifData)
Laptop.Notification:AddWithId(id, title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:AddNotificationWithId(id, title, description, time, duration, app, actions, notifData)
Laptop.Notification:Update(id, title, description, skipSound) > exports['sandbox-laptop']:UpdateNotification(id, title, description, skipSound)
Laptop.Notification:Remove(id) > exports['sandbox-laptop']:RemoveNotification(id)
Laptop.Notification:Reset() > exports['sandbox-laptop']:ResetNotifications()
Laptop.Permissions:HasPermission(app, permission) > exports['sandbox-laptop']:HasPermission(app, permission)
Laptop.LSUnderground.Chopping:CreateBlips() > exports['sandbox-laptop']:ChoppingCreateBlips()
Laptop.LSUnderground.Chopping:AttemptChop() > exports['sandbox-laptop']:AttemptChop()

Server side:

Laptop:UpdateJobData(source, returnValues) > exports['sandbox-laptop']:UpdateJobData(source, returnValues)
Laptop.Notification:Add(source, title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:AddNotification(source, title, description, time, duration, app, actions, notifData)
Laptop.Notification:AddWithId(source, id, title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:AddNotificationWithId(source, id, title, description, time, duration, app, actions, notifData)
Laptop.Notification:Update(source, id, title, description, skipSound) > exports['sandbox-laptop']:UpdateNotification(source, id, title, description, skipSound)
Laptop.Notification:RemoveById(source, id) > exports['sandbox-laptop']:RemoveNotificationById(source, id)
Laptop.BizWiz.Documents:Search(jobId, term) > exports['sandbox-laptop']:BizWizDocumentsSearch(jobId, term)
Laptop.BizWiz.Documents:View(jobId, id) > exports['sandbox-laptop']:BizWizDocumentsView(jobId, id)
Laptop.BizWiz.Documents:Create(jobId, data) > exports['sandbox-laptop']:BizWizDocumentsCreate(jobId, data)
Laptop.BizWiz.Documents:Update(jobId, id, char, report) > exports['sandbox-laptop']:BizWizDocumentsUpdate(jobId, id, char, report)
Laptop.BizWiz.Documents:Delete(jobId, id) > exports['sandbox-laptop']:BizWizDocumentsDelete(jobId, id)
Laptop.BizWiz.Notices:Create(source, job, data) > exports['sandbox-laptop']:BizWizNoticesCreate(source, job, data)
Laptop.BizWiz.Notices:Delete(job, id) > exports['sandbox-laptop']:BizWizNoticesDelete(job, id)
Laptop.BizWiz.Receipts:Search(jobId, term) > exports['sandbox-laptop']:BizWizReceiptsSearch(jobId, term)
Laptop.BizWiz.Receipts:View(jobId, id) > exports['sandbox-laptop']:BizWizReceiptsView(jobId, id)
Laptop.BizWiz.Receipts:Create(jobId, data) > exports['sandbox-laptop']:BizWizReceiptsCreate(jobId, data)
Laptop.BizWiz.Receipts:Update(jobId, id, char, report) > exports['sandbox-laptop']:BizWizReceiptsUpdate(jobId, id, char, report)
Laptop.BizWiz.Receipts:Delete(jobId, id) > exports['sandbox-laptop']:BizWizReceiptsDelete(jobId, id)
Laptop.BizWiz.Receipts:DeleteAll(jobId) > exports['sandbox-laptop']:BizWizReceiptsDeleteAll(jobId)
Laptop.LSUnderground.Boosting:RewardContract(source) > exports['sandbox-laptop']:LSUndergroundBoostingRewardContract(source)
Laptop.LSUnderground.Boosting:GiveContract(source, vehicle, prices, timeLength, settings) > exports['sandbox-laptop']:LSUndergroundBoostingGiveContract(source, vehicle, prices, timeLength, settings)
Laptop.LSUnderground.Boosting:Start(teamId, contract) > exports['sandbox-laptop']:LSUndergroundBoostingStart(teamId, contract)
Laptop.LSUnderground.Boosting:Cancel(teamId, teamDeleted) > exports['sandbox-laptop']:LSUndergroundBoostingCancel(teamId, teamDeleted)
Laptop.LSUnderground.Boosting:Complete(teamId) > exports['sandbox-laptop']:LSUndergroundBoostingComplete(teamId)
Laptop.LSUnderground.Chopping:GenerateList(length, hvCount) > exports['sandbox-laptop']:LSUndergroundChoppingGenerateList(length, hvCount)
Laptop.LSUnderground.Chopping:InProgress(source, type, model, listId) > exports['sandbox-laptop']:LSUndergroundChoppingInProgress(source, type, model, listId)
Laptop.LSUnderground.Chopping:FindList(source, vehNet) > exports['sandbox-laptop']:LSUndergroundChoppingFindList(source, vehNet)
Laptop.LSUnderground.Chopping:IsOnList(list, model) > exports['sandbox-laptop']:LSUndergroundChoppingIsOnList(list, model)
Laptop.LSUnderground.Chopping:RemoveFromList(source, type, model, listId) > exports['sandbox-laptop']:LSUndergroundChoppingRemoveFromList(source, type, model, listId)
Laptop.LSUnderground.Chopping:CreatePickupBox(source, wasHv, type) > exports['sandbox-laptop']:LSUndergroundChoppingCreatePickupBox(source, wasHv, type)
Laptop.Teams:GetAll() > exports['sandbox-laptop']:TeamsGetAll()
Laptop.Teams:Get(id) > exports['sandbox-laptop']:TeamsGet(id)
Laptop.Teams:GetByMember(SID) > exports['sandbox-laptop']:TeamsGetByMember(SID)
Laptop.Teams:GetByMemberSource(source) > exports['sandbox-laptop']:TeamsGetByMemberSource(source)
Laptop.Teams:Create(source, name) > exports['sandbox-laptop']:TeamsCreate(source, name)
Laptop.Teams:Delete(id, leaderDropped) > exports['sandbox-laptop']:TeamsDelete(id, leaderDropped)
Laptop.Teams:SetState(team, state, stateName) > exports['sandbox-laptop']:TeamsSetState(team, state, stateName)
Laptop.Teams:ResetState(team) > exports['sandbox-laptop']:TeamsResetState(team)
Laptop.Teams.Members:Add(source, team) > exports['sandbox-laptop']:TeamsMembersAdd(source, team)
Laptop.Teams.Members:Remove(source, teamId, wasRemoved) > exports['sandbox-laptop']:TeamsMembersRemove(source, teamId, wasRemoved)
Laptop.Teams.Members:SendEvent(team, event, ...) > exports['sandbox-laptop']:TeamsMembersSendEvent(team, event, ...)
Laptop.Teams.Members:Notification(team, title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:TeamsMembersNotification(team, title, description, time, duration, app, actions, notifData)
Laptop.Teams.Members:NotificationAddWithId(team, id, title, description, time, duration, app, actions, notifData) > exports['sandbox-laptop']:TeamsMembersNotificationAddWithId(team, id, title, description, time, duration, app, actions, notifData)
Laptop.Teams.Members:NotificationUpdate(team, id, title, description, skipSound) > exports['sandbox-laptop']:TeamsMembersNotificationUpdate(team, id, title, description, skipSound)
Laptop.Teams.Members:NotificationRemoveById(team, id) > exports['sandbox-laptop']:TeamsMembersNotificationRemoveById(team, id)
Laptop.Teams.Requests:Add(target, isTeam, event, label, description, data, time) > exports['sandbox-laptop']:TeamsRequestsAdd(target, isTeam, event, label, description, data, time)
Laptop.Teams.Requests:Clear(id) > exports['sandbox-laptop']:TeamsRequestsClear(id)
Laptop.Teams.Requests:Get(source) > exports['sandbox-laptop']:TeamsRequestsGet(source)

Rewrote Doors Component > Exports
Client side:

Doors:IsLocked(doorId) > exports['sandbox-doors']:IsLocked(doorId)
Doors:CheckRestriction(doorId) > exports['sandbox-doors']:CheckRestriction(doorId)
Doors:GetCurrentDoor() > exports['sandbox-doors']:GetCurrentDoor()

Server side:

Doors:SetLock(doorId, newState, doneDouble) > exports['sandbox-doors']:SetLock(doorId, newState, doneDouble)
Doors:IsLocked(doorId) > exports['sandbox-doors']:IsLocked(doorId)
Doors:SetForcedOpen(doorId) > exports['sandbox-doors']:SetForcedOpen(doorId)
Doors:SetElevatorLock(elevatorId, floorId, newState) > exports['sandbox-doors']:SetElevatorLock(elevatorId, floorId, newState)
Doors:DisableDoor(doorId, seconds, doneDouble) > exports['sandbox-doors']:DisableDoor(doorId, seconds, doneDouble)

Rewrote StorageUnits Component > Exports
Client side:

StorageUnits:Access() > exports['sandbox-businesses']:StorageUnitsAccess()
StorageUnits:Manage(specificUnit) > exports['sandbox-businesses']:StorageUnitsManage(specificUnit)
StorageUnits:ManageAll(managedBy) > exports['sandbox-businesses']:StorageUnitsManageAll(managedBy)
StorageUnits:GetNearUnit() > exports['sandbox-businesses']:StorageUnitsGetNearUnit()

Server side:

StorageUnits:Create(location, label, level, managedBy) > exports['sandbox-businesses']:StorageUnitsCreate(location, label, level, managedBy)
StorageUnits:Update(id, key, value, skipRefresh) > exports['sandbox-businesses']:StorageUnitsUpdate(id, key, value, skipRefresh)
StorageUnits:Delete(id) > exports['sandbox-businesses']:StorageUnitsDelete(id)
StorageUnits:Sell(id, owner, seller) > exports['sandbox-businesses']:StorageUnitsSell(id, owner, seller)
StorageUnits:Get(id) > exports['sandbox-businesses']:StorageUnitsGet(id)
StorageUnits:GetAll() > exports['sandbox-businesses']:StorageUnitsGetAll()
StorageUnits:GetAllManagedBy(managedBy) > exports['sandbox-businesses']:StorageUnitsGetAllManagedBy(managedBy)
StorageUnits:GetNearUnit(source) > exports['sandbox-businesses']:StorageUnitsGetNearUnit(source)

Rewrote Status Component > Exports
Client side:

Status:Register(name, max, icon, color, flash, modify, options) > exports['sandbox-status']:Register(name, max, icon, color, flash, modify, options)
Status:GetRegistered() > exports['sandbox-status']:GetRegistered()
Status.Get:All() > exports['sandbox-status']:GetAll()
Status.Get:Single(name) > exports['sandbox-status']:GetSingle(name)
Status.Set:All(entity, value) > exports['sandbox-status']:SetAll(entity, value)
Status.Set:Single(name, value) > exports['sandbox-status']:SetSingle(name, value)
Status:Reset(entity, value) > exports['sandbox-status']:Reset(entity, value)
Status.Modify:Add(status, value, addCd, force) > exports['sandbox-status']:Add(status, value, addCd, force)
Status.Modify:Remove(status, value, force) > exports['sandbox-status']:Remove(status, value, force)
Status:Toggle() > exports['sandbox-status']:Toggle()
Status:Check() > exports['sandbox-status']:Check()

Server side:

Status:Register(name, max, icon, tick, modify) > exports['sandbox-status']:Register(name, max, icon, tick, modify)
Status.Get:All() > exports['sandbox-status']:GetAll()
Status.Get:Single(name) > exports['sandbox-status']:GetSingle(name)
Status.Modify:Add(source, name, value, addCd, isForced) > exports['sandbox-status']:Add(source, name, value, addCd, isForced)
Status.Modify:Remove(source, name, value, addCd, isForced) > exports['sandbox-status']:Remove(source, name, value, addCd, isForced)
Status:Set(source, name, value) > exports['sandbox-status']:Set(source, name, value)

Rewrote Scenes Component > Exports
Client side:

Scenes:BeginCreation(text, staff) > exports['sandbox-scenes']:BeginCreation(text, staff)
Scenes:Deletion() > exports['sandbox-scenes']:Deletion()
Scenes:Edit() > exports['sandbox-scenes']:Edit()

Server side:

Scenes:Create(scene, isStaff) > exports['sandbox-scenes']:Create(scene, isStaff)
Scenes:Edit(id, newData, isStaff) > exports['sandbox-scenes']:Edit(id, newData, isStaff)
Scenes:Delete(id) > exports['sandbox-scenes']:Delete(id)

Rewrote Reputation Component > Exports
Client side:

Reputation:GetLevel(id) > exports['sandbox-characters']:RepGetLevel(id)
Reputation:HasLevel(id, level) > exports['sandbox-characters']:RepHasLevel(id, level)
Reputation:GetLevelData(id) > exports['sandbox-characters']:RepGetLevelData(id)

Server side:

Reputation:Create(id, label, levels, hidden) > exports['sandbox-characters']:RepCreate(id, label, levels, hidden)
Reputation:GetLevel(source, id) > exports['sandbox-characters']:RepGetLevel(source, id)
Reputation:HasLevel(source, id, level) > exports['sandbox-characters']:RepHasLevel(source, id, level)
Reputation:View(source) > exports['sandbox-characters']:RepView(source)
Reputation:ViewList(source, list) > exports['sandbox-characters']:RepViewList(source, list)
Reputation.Modify:Add(source, id, amount) > exports['sandbox-characters']:RepAdd(source, id, amount)
Reputation.Modify:Remove(source, id, amount) > exports['sandbox-characters']:RepRemove(source, id, amount)

Rewrote Objects & ObjectsPlacer Components > Exports
Client side:

Objects:Create(id, type, creator, model, coords, heading, rotation, isFrozen, nameOverride) > exports['sandbox-objects']:Create(id, type, creator, model, coords, heading, rotation, isFrozen, nameOverride)
Objects:Delete(id) > exports['sandbox-objects']:Delete(id)
ObjectPlacer:Start(model, finishEvent, data, allowedInterior, cancelEvent, useGizmo, isFurniture, startCoords, startHeading, startRotation, maxDistOverride) > exports['sandbox-objects']:PlacerStart(model, finishEvent, data, allowedInterior, cancelEvent, useGizmo, isFurniture, startCoords, startHeading, startRotation, maxDistOverride)
ObjectPlacer:End() > exports['sandbox-objects']:PlacerEnd()
ObjectPlacer:Cancel(skipNotification, skipEvent) > exports['sandbox-objects']:PlacerCancel(skipNotification, skipEvent)

Server side:

Objects:Info(source, id) > exports['sandbox-objects']:Info(source, id)
Objects:Create(source, type, isTemp, model, coords, rotation, isFrozen, nameOverride) > exports['sandbox-objects']:Create(source, type, isTemp, model, coords, rotation, isFrozen, nameOverride)
Objects:Delete(source, id) > exports['sandbox-objects']:Delete(source, id)

Rewrote Pwnzor Component > Exports
Server side:

Pwnzor.Players:Disconnected(source) > exports['sandbox-pwnzor']:Disconnected(source)
Pwnzor.Players:Get(source, key) > exports['sandbox-pwnzor']:Get(source, key)
Pwnzor.Players:Set(source, key) > exports['sandbox-pwnzor']:Set(source, key)
Pwnzor.Players:Unset(source, key) > exports['sandbox-pwnzor']:Unset(source, key)
Pwnzor.Players:TempPosIgnore(source) > exports['sandbox-pwnzor']:TempPosIgnore(source)
Pwnzor:Screenshot(stateId, desc) > exports['sandbox-pwnzor']:Screenshot(stateId, desc)

Rewrote Queue Component > Exports
Server side:

Queue:HandleConnection(source, identifier, deferrals) > exports['sandbox-queue']:HandleConnection(source, identifier, deferrals)
Queue.Queue:Sort() > exports['sandbox-queue']:Sort()
Queue.Queue:Pop(identifier, disconnect) > exports['sandbox-queue']:Pop(identifier, disconnect)
Queue.Queue:Check(identifier) > exports['sandbox-queue']:Check(identifier)
Queue.Queue:GetCount() > exports['sandbox-queue']:GetCount()
Queue.Queue:GetPosition(identifier) > exports['sandbox-queue']:GetPosition(identifier)
Queue.Queue:CheckGhosts() > exports['sandbox-queue']:CheckGhosts()
Queue:AddCrashPriority(identifier, message) > exports['sandbox-queue']:AddCrashPriority(identifier, message)
Queue:HasCrashPriority(identifier) > exports['sandbox-queue']:HasCrashPriority(identifier)
Queue:AddTempPriority(identifier, prio) > exports['sandbox-queue']:AddTempPriority(identifier, prio)
Queue:RemoveTempPriority(identifier) > exports['sandbox-queue']:RemoveTempPriority(identifier)
Queue:HasTempPriority(identifier) > exports['sandbox-queue']:HasTempPriority(identifier)
Queue.Utils:CloseAndDrop() > exports['sandbox-queue']:CloseAndDrop()

Rewrote Lasers Component > Exports
Client side:

Lasers:Create(id, originPoint, targetPoints, options, startEnabled, onHit) > exports['sandbox-lasers']:Create(id, originPoint, targetPoints, options, startEnabled, onHit)
Lasers:GetLaser(id) > exports['sandbox-lasers']:GetLaser(id)
Lasers:GetActive(id) > exports['sandbox-lasers']:GetActive(id)
Lasers:GetVisible(id) > exports['sandbox-lasers']:GetVisible(id)
Lasers:GetMoving(id) > exports['sandbox-lasers']:GetMoving(id)
Lasers:GetColor(id) > exports['sandbox-lasers']:GetColor(id)
Lasers.Utils:SetActive(id, state) > exports['sandbox-lasers']:SetActive(id, state)
Lasers.Utils:SetVisible(id, state) > exports['sandbox-lasers']:SetVisible(id, state)
Lasers.Utils:SetMoving(id, state) > exports['sandbox-lasers']:SetMoving(id, state)
Lasers.Utils:SetColor(id, r, g, b, a) > exports['sandbox-lasers']:SetColor(id, r, g, b, a)

Rewrote Notification Component > Exports
Notification:Clear() > exports["sandbox-hud"]:Notification(clear)
Notification:Success(message, duration, icon) > exports["sandbox-hud"]:Notification(message, duration, icon)
Notification:Warn(message, duration, icon) > exports["sandbox-hud"]:Notification(warn, message, duration, icon)
Notification:Error(message, duration, icon) > exports["sandbox-hud"]:NotiNotificationfError(error, message, duration, icon)
Notification:Info(message, duration, icon) > exports["sandbox-hud"]:Notification(info, message, duration, icon)
Notification:Standard(message, duration, icon) > exports["sandbox-hud"]:Notification(standard, message, duration, icon)
Notification:Custom(message, duration, icon, style) > exports["sandbox-hud"]:Notification(custom, message, duration, icon, style)
-- havent done the ones below yet
Notification.Persistent:Success(id, message, icon) > exports["sandbox-hud"]:NotifPersistentSuccess(id, message, icon)
Notification.Persistent:Warn(id, message, icon) > exports["sandbox-hud"]:NotifPersistentWarn(id, message, icon)
Notification.Persistent:Error(id, message, icon) > exports["sandbox-hud"]:NotifPersistentError(id, message, icon)
Notification.Persistent:Info(id, message, icon) > exports["sandbox-hud"]:NotifPersistentInfo(id, message, icon)
Notification.Persistent:Standard(id, message, icon) > exports["sandbox-hud"]:NotifPersistentStandard(id, message, icon)
Notification.Persistent:Custom(id, message, icon, style) > exports["sandbox-hud"]:NotifPersistentCustom(id, message, icon, style)
Notification.Persistent:Remove(id) > exports["sandbox-hud"]:NotifPersistentRemove(id)