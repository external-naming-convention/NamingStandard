## getdevice

Eeturns the user's platform, allowing for easier optimisation of scripts for certain platforms.

> ### 🔎 Notes
> This can be spoofed with Hookmetamethod.
> Some platforms not commonly used for exploiting will return Unknown.

### Aliases

 * `getplatform`
 * `getos`

### Example

```lua
if getdevice() == "Windows" or getdevice() == "Windows (Microsoft Store)" or getdevice() == "macOS" then
  print("Player is using a computer")
elseif getdevice() == "iOS" or getdevice() == "Android" then
  print("Player is on mobile")
else
  print("Unknown device. Player is most likely spoofing their device")
end
```
