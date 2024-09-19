# Instances

The **Instance** functions are used to interact with game objects and their properties.

---

## getinstances

```lua
function getinstances(): {Instance}
```

Returns a list of every Instance referenced on the client.

### Example

```lua
local objects = getinstances()

local gameCount = 0
local miscCount = 0

for _, object in ipairs(objects) do
	if object:IsDescendantOf(game) then
		gameCount += 1
	else
		miscCount += 1
	end
end

print(gameCount) --> The number of objects in the `game` hierarchy.
print(miscCount) --> The number of objects outside of the `game` hierarchy.
```

---

## getnilinstances

```lua
function getnilinstances(): {Instance}
```

Like `getinstances`, but only includes Instances that are not descendants of a service provider.

### Example

```lua
local objects = getnilinstances()

for _, object in ipairs(objects) do
	if object:IsA("LocalScript") then
		print(object, "is a LocalScript")
	end
end
```

---

## getplayer

```lua
function getplayer(name: string?): Instance
```

Gets player from name, or LocalPlayer if no name is provided.

### Aliases   

 * `getlocalplayer` (sorta)   

### Example

```lua
getplayer():Kick("Coolio was too cool")
```

---

## getplayers

```lua
function getplayers(): { [string]: Instance }
```

Returns all players in current game.

### Example

```lua
local playerToFind = "coolio"
local playerAmount = 0
for i, x in pairs(getplayers()) do 
	playerAmount=playerAmount+1
	if i == playerToFind then
		print('"'..playerToFind.."\" was found with the DisplayName \""..x.DisplayName..'"')
		getplayer():Kick("Admin \""..playerToFind.."\" was found in your server")
	end
end
print("There are currently "..tostring(playerAmount).." players in your lobby.")
```

---

## runanimation

```lua
function runanimation(animationId, player: Instance?): ()
```

Plays an animation on the chosen player.

### Aliases   

 * `playanimation`   

### Example

```lua
local function youShouldDanceYourselfNow()
    runanimation(507772104)
end
local function danceTillYoureDead()
    for _, x in pairs(getplayers()) do
        runanimation(507772104, x)
    end
end
danceTillYoureDead() -- Wowie, everyone be /e dance3ing
```
