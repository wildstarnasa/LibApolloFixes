LibApolloFixes
==============

Library that exposes obscured Addons and adds two methods to Apollo:
* GetAddons()
* GetReplacement(strAddonName)

##Apollo.GetAddons

This returns a list of all addons that Wildstar is aware of.  It does not know their state (loaded or not)

###Usage
```lua
local tAddonNames = Apollo.GetAddons()
for k,v in ipairs(tAddonNames) do
    Print(v)
end
```

##Apollo.GetReplacement(strAddonName)

This returns a table containing all addons that have indicated they replace the addon named strAddonName or an empty table if not replaced

###Usage
```lua
local tReplacements = Apollo.GetReplacement("Vendor")
if #tReplacements > 0 then
  for _,v in ipairs(tReplacements) do
    Print("Replaced by: " .. v)
  end
else
  Print("Not Replaced!")
end
```

##Apollo.GetAddon extension

This library makes `Apollo.GetAddon` work for the following addons:

| Addon Name | Purpose |
|------------|---------|
|ArenaTeamRegister|Registration of an Arena Team|
|ChallengeLog|Challenge section of Codex|
|ChallengeRewardPanel|Reward Panel seen when a Challenge reward is chosen|
|CircleRegistration|Registration of a Circle|
|DecorPreview|Preview of Decor|
|FloatTextPanel|Various Float Texts|
|GroupDisplayOptions|Group Options (Invite/Loot)|
|HousingDatachron|Housing Menu|
|HousingLandscape|Housing Landscape|
|HousingList|Placed Decor List|
|HousingRemodel|Housing Remodel|
|HUDInteract|HUD Interact (F)|
|ImprovedSalvage|Item Salvage All Addon|
|ItemPreview|Item Preview Window (Ctrl + right click)|
|Mannequin|Housing Mannequins|
|PathExplorerMissions|Explorer Path Missions|
|PathScientistCustomize|Scientest Scanbot Customization|
|PathScientistExperimentation|Scientiest Experimentation|
|PathSettlerMissions|Settler Path Missions|
|PathSoldierMissions|Soldier Path Missions|
|PlugPreview|Preview of Housing Plugs|
|TradeskillContainer|Holds the 3 Tradeskill Forms|
|TradeskillSchematics|Tradeskill Schematics|
|TradeskillTalents|Tradeskill Talents|
|TutorialPrompts|Tutorials|
|WarpartyBattle|Warparty Layout and Boss Tokens|
|WarpartyRegister|Registration of a Warparty|

###Caveat

GetAddon may not return anything for one of the above addons if it has not initialized yet.

Example: TradeskillTalents will not be accessible until the `GenericEvent_InitializeTradeskillTalents` event has fired.


However you *can* register for the "ObscuredAddonVisible" event which will be fired when addons can be retrieved with GetAddon.

The event will contain the name of the addon as the only argument.
