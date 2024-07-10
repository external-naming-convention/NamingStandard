## getdevice

`⏰ Yields` `🌎 Global` `🪲 Inconsistent` `🔎 Needs Investigation` `📌 Custom Tag`

```lua
function getdevice()
    local inputsrv = game:GetService("UserInputService")
        if inputsrv:GetPlatform() == Enum.Platform.Windows then
            return 'Windows'
        elseif inputsrv:GetPlatform() == Enum.Platform.OSX then
            return 'macOS'
        elseif inputsrv:GetPlatform() == Enum.Platform.IOS then
            return 'iOS'
        elseif inputsrv:GetPlatform() == Enum.Platform.UWP then
            return 'Windows (Microsoft Store)'
        elseif inputsrv:GetPlatform() == Enum.Platform.Android then
            return 'Android'
	    else return 'Unknown'
    end
end
```

This function will make script development easier because it directly returns the user's platform, allowing for easier optimisation of scripts for certain platforms

> ### 🔎 Notes, tips, info
> I don't really know what to put in here, its pretty simple

> ### ⚠️ Warnings, risks
> This can be spoofed with Hookmetamethod

> ### ⛔ Danger!
> Nothing really

> ### 🪲 Bugs, issues
> Some platforms not commonly used for exploiting will return Unknown

### Parameters

None

### Aliases

 * `getplatform`
 * `getos`

### Example

A description of the example that follows.

```lua
if getdevice() == "Windows" or getdevice() == "Windows (Microsoft Store)" or getdevice() == "macOS" then
  print("Player is using a computer")
elseif getdevice() == "iOS" or getdevice() == "Android" then
  print("Player is on mobile")
else
  print("Unknown device. Player is most likely spoofing their device")
end
```
