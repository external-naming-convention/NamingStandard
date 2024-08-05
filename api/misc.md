# Miscellaneous

The **miscellaneous** functions are a temporary collection of functions that are not yet categorized.

---

## identifyexecutor

```lua
function identifyexecutor(): (string, string)
```

Returns the name and version of the current executor.

### Aliases

 * `getexecutorname`

---

## lz4compress

```lua
function lz4compress(data: string): string
```

Compresses `data` using LZ4 compression.

### Parameters

 * `data` - The uncompressed data.

### Example

```lua
local text = "Hello, world! Hello, world! Goodbye, world!"
print(#text) --> 43
print(#lz4compress(text)) --> 34
```

---

## lz4decompress

```lua
function lz4decompress(data: string, size: number): string
```

Decompresses `data` using LZ4 compression, with the decompressed size specified by `size`.

### Parameters

 * `data` - The compressed data.
 * `size` - The size of the decompressed data.

### Example

```lua
local text = "Hello, world! Hello, world!"
local compressed = lz4compress(text)
print(lz4decompress(compressed, #text)) --> "Hello, world! Hello, world!"
```

---

## messagebox

`⏰ Yields`

```lua
function messagebox(text: string, caption: string, flags: number): number
```

Creates a message box with the specified text, caption, and flags. Yields until the message box is closed, and returns the user input code.

Documentation regarding the flags and return codes can be found [here](https://docs.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-messagebox).

### Parameters

 * `text` - The text to display in the message box.
 * `caption` - The caption of the message box.
 * `flags` - The flags to use.

### Example

Prompts the user with a message box with three options and a warning icon:

```lua
local MB_ICONWARNING = 0x00000030
local MB_CANCELTRYCONTINUE = 0x00000006
local MB_DEFBUTTON2 = 0x00000100

local IDCANCEL = 0x00000002
local IDTRYAGAIN = 0x00000004
local IDCONTINUE = 0x00000005

local input = messagebox(
	"Resource not available\nDo you want to try again?",
	"Resource not found",
	bit32.bor(MB_ICONWARNING, MB_CANCELTRYCONTINUE, MB_DEFBUTTON2)
)

if input == IDCANCEL then
	print("Canceled")
elseif input == IDTRYAGAIN then
	print("Try again")
elseif input == IDCONTINUE then
	print("Continue")
end
```

---

## queue_on_teleport

```lua
function queue_on_teleport(code: string): ()
```

Queues the specified script to be executed after the player teleports to a different place.

### Parameters

 * `code` - The script to execute.

### Aliases

 * `queueonteleport` - Will supercede this function in the future.

### Example

```lua
local source = game:GetObjects("rbxassetid://1234")[1].Source
queue_on_teleport(source)
loadstring(source)()
```

---

## request

`⏰ Yields`

```lua
function request(options: HttpRequest): HttpResponse
```

Sends an HTTP request using the specified options. Yields until the request is complete, and returns the response.

### Request

| Field | Type | Description |
| ----- | ---- | ----------- |
| `Url` | string | The URL for the request. |
| `Method` | string | The HTTP method to use. Can be `GET`, `POST`, `PATCH`, or `PUT`. |
| `Body` | string? | The body of the request. |
| `Headers` | table? | A table of headers. |
| `Cookies` | table? | A table of cookies. |

### Response

| Field | Type | Description |
| ----- | ---- | ----------- |
| `Body` | string | The body of the response. |
| `StatusCode` | number | The number status code of the response. |
| `StatusMessage` | string | The status message of the response. |
| `Success` | boolean | Whether or not the request was successful. |
| `Headers` | table | A dictionary of headers. |

### Headers

The executor provides the following headers for identification on a web server:

| Header | Description |
| ------ | ----------- |
| `PREFIX-User-Identifier` | A string unique to each user, and does not change if the script executor is used across computers. |
| `PREFIX-Fingerprint` | The hardware identifier of the user. |
| `User-Agent` | The name and version of the executor. |

### Parameters

 * `options` - The options to use.

### Aliases

 * `http.request`
 * `http_request`

### Example

```lua
local response = request({
	Url = "http://example.com/",
	Method = "GET",
})

print(response.StatusCode .. " - " .. response.StatusMessage) --> 200 - HTTP/1.1 200 OK
```

---

## setclipboard

```lua
function setclipboard(text: string): ()
```

Copies `text` to the clipboard.

### Parameters

 * `text` - The text to copy.

### Aliases

 * `toclipboard`

### Example

```lua
local character = game:GetService("Players").LocalPlayer.Character
local components = table.pack(character.PrimaryPart.CFrame:GetComponents())
setclipboard("CFrame.new(" .. table.concat(components, ", ") .. ")")
```

---

## setfpscap

```lua
function setfpscap(fps: number): ()
```

Sets the in-game FPS cap to `fps`. If `fps` is 0, the FPS cap is disabled.

### Parameters

 * `fps` - The FPS cap.

### Example

```lua
setfpscap(0) -- Unlocks the FPS cap
```

---

## customprint

`🪲 Compatibility`

```lua
function customprint(text: string, properties: table, imageId: rbxasset): ()
```

Prints to the console with special options like setting the image, color & font.

> ### 🪲 Known Issues
> The console is in CoreGui only when open, this can cause problems if you dont fuck around in CoreScripts or whatever.

### Parameters

 * `text` - Text to print.
 * `properties` - Properties for the TextLabel of the print.
 * `imageId` - The Image property for the ImageLabel of the print.

### Example

```lua
customprint("Successful", {TextColor3 = Color3.fromRGB(0, 255, 0)}, "rbxasset://textures/AudioDiscovery/done.png")
```

---

## getfps

```lua
function getfps(): number
```

Gets the current player's fps as a number.

> ### 🔎 Note
> The fps is sometimes rounded(math.round in Lua), so you won't always get the exact fps.

### Example

```lua
print(tostring(getfps()*60).." fpm")
print(tostring(getfps()).." fps")
```

---

## getping

```lua
function getping(): number
```

Gets the current player's ping as a number.

> ### 🔎 Note
> The ping is sometimes rounded(math.round in Lua), so you sometimes won't get the exact ping.

### Example

```lua
print(tostring(getping()/1000).."s ping")
print(tostring(getping()).."ms ping")
```

---

## getdevice

```lua
function getdevice(): string
```

Returns the user's platform, allowing for easier optimisation of scripts for certain platforms.

> ### 🔎 Notes   
> This can be spoofed with Hookmetamethod.   

### Aliases

 * `getplatform`
 * `getos`

### Example

```lua
if getdevice() == "Windows" or getdevice() == "UWP" or getdevice() == "OSX" then
  print("Player is likely using a computer")
elseif getdevice() == "IOS" or getdevice() == "Android" then
  print("Player is likely on mobile")
else
  print("Unknown device. Player is likely spoofing their device")
end
```

---

## join

```lua
function join(PlaceId: number, JobId: string?): ()
```

Joins specified game or server.

### Aliases

 * `joingame`
 * `joinserver`

### Example

```lua
local function rejoin()
	join(game.PlaceId, game.JobId)
end
rejoin()
```
