# Roblox External Naming Convention
aka RENC, is an organization between executor developers to provide a unified scripting API for our scripters.
---   
**Please go to our official website for better styled information: https://roblox.scriptenc.org/**

## Why?
Over the years scripting has gotten more and more complex to support multiple executors. This is because of the many unique naming conventions various executors use.

Consider the following scenario. You want to know if a function belongs to the executor or not. In order for this code to be cross compatiable with all executors code like this is needed:
```lua
local is_executor_closure = is_syn_closure or is_fluxus_closure or is_sentinel_closure or is_krnl_closure or is_proto_closure or is_calamari_closure or is_electron_closure or is_elysian_closure
```
This is reality for scripters who want cross compatibilty in their scripts. Scripters shouldn't have to do such laborous work just to attain cross compatability. The RENC seeks to solve this problem using naming conventions everyone agrees upon and follows.

One variant of a script should naturally work on all script executors which have their environment properly fitted to the RENC. 

## How?
The RENC provides standards for naming conventions as well as API functionality. The standard is written in markdown on this GitHub. Edits or additions are done through pull requests. Edits and additions are manually approved by the RENC council and discussed by everyone.

## Supporting RENC
As a product owner, your support of RENC by following the API will result in a far smoother experience for scripters, as they are able to work on scripts that they can confidently say will work on **most** products. Once you have implemented RENC's API, you can display so by adding the badge to your website, thread or application.

Here are a few examples for badges. You can use the HTML one for websites, and the markdown one for repositories.
```html

<i>RENC Badge</i>

<a href="https://roblox.scriptenc.org" style="height:max-content;" target="_blank">
    <img style="width: 120px;height:auto;" alt="RENC Supported Badge" src="https://roblox.scriptenc.org/badge.png"/>
</a>
<i>RENC Supported Badge</i>

<a href="https://roblox.scriptenc.org" style="height:max-content;" target="_blank">
    <img style="width: 120px;height:auto;" alt="RENC Supported Badge" src="https://roblox.scriptenc.org/badge-supported.png"/>
</a>
```   
```md
_RENC Badge_

[![RENC Supported Badge](https://roblox.scriptenc.org/badge.png)](https://roblox.scriptenc.org)

_RENC Supported Badge_

[![RENC Supported Badge(https://roblox.scriptenc.org/badge-supported.png)](https://roblox.scriptenc.org)
```

This will notify people of your alliance in providing scripters with an easier method of engineering scripts that your consumers can enjoy.

NOTICE: If you, as a product owner, do not have all of these functions but yet support the ones you do - you then support RENC! You are more than able to display the badge on your website.

## Checking your environment

You can run the RENC environment checking script to see how well your executor environment supports the RENC standard. Find the script [here.](RENCCheckEnv.lua) The script determines what is missing, and writes the results to file under workspace.

## Contributing
Go [here](CONTRIBUTING.md) for a guide on contributing.