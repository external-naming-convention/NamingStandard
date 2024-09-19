# Scripts

The **script** functions provide access to script environments and internal state.

---

## getgenv

```lua
function getgenv(): { [string]: any }
```

Returns the custom global environment of the executor. It can be used to add global functions or share variables between scripts.

### Example

Prevent a script from being run twice:

```lua
if getgenv().__IS_LOADED then
	error("This script is already loaded!")
end

getgenv().__IS_LOADED = true
```