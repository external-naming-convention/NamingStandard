# Cache

The **cache** library provides methods for modifying the internal Instance cache.

Note that some of the methods are only available as global functions. They will be tagged with `🌎 Global`.

---

## cache.invalidate

```lua
function invalidate(object: Instance): ()
```

Deletes `object` from the Instance cache. Effectively invalidates `object` as a reference to the underlying Instance.

### Parameters

 * `object` - The object to invalidate.

### Example

```lua
local HttpService = game:GetService("HttpService")
cache.invalidate(game:GetService("HttpService"))
print(HttpService, HttpService == game:GetService("HttpService")) --> HttpService, false
```

---

## cache.iscached

```lua
function iscached(object: Instance): boolean
```

Checks whether `object` exists in the Instance cache.

### Parameters

 * `object` - The object to find.

### Example

```lua
local HttpService = game:GetService("HttpService")
cache.invalidate(HttpService)
print(cache.iscached(HttpService)) --> false
```

---

## cache.replace

```lua
function replace(object: Instance, newObject: Instance): ()
```

Replaces `object` in the Instance cache with `newObject`.

### Parameters

 * `object` - The object to replace.
 * `newObject` - The new object to replace `object` with.

### Example

```lua
local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")

cache.replace(HttpService, Players)

print(HttpService) --> Players
```

---

## cloneref

`🌎 Global`

```lua
function cloneref(object: Instance): Instance
```

Returns a copy of the Instance reference to `object`. This is useful for managing an Instance without directly referencing it.

### Parameters

 * `object` - The Instance to clone.

### Example

```lua
local HttpService = game:GetService("HttpService")
local HttpServiceClone = cloneref(HttpService)

print(HttpService == HttpServiceClone) --> false
```

---

## compareinstances

`🌎 Global`

```lua
function compareinstances(a: Instance, b: Instance): boolean
```

Returns whether objects `a` and `b` both reference the same Instance.

### Parameters

 * `a` - The first Instance to compare.
 * `b` - The second Instance to compare.

### Example

```lua
local HttpService = game:GetService("HttpService")
local HttpServiceClone = cloneref(HttpService)

print(HttpService == HttpServiceClone) --> false
print(compareinstances(HttpService, HttpServiceClone)) --> true
```