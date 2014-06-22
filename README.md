LibApolloFixes
==============

Library that exposes obscured Addons and adds a GetAddons() method to Apollo.

##Apollo.GetAddons

This returns list of all addons that Wildstar is aware of.  It does not know their state (loaded or not)

###Usage
```lua
local tAddonNames = Apollo.GetAddons()
for k,v in ipairs(tAddonNames) do
    Print(v)
end
```

##Apollo.GetAddon extension

This library makes Apollo.GetAddon work for the following addons:

* ImprovedSalvage
* ItemPreview
* TradeskillContainer
* TradeskillSchematics
* TradeskillTalents
* WarpartyRegister
* WarpartyBattle
* TutorialPrompts
* PathSoldierMissions
* PathSettlerMissions
* PathScientistExperimentation
* PathScientistCustomize
* PathExplorerMissions
* HUDInteract
* HousingRemodel
* HousingLandscape
* HousingListWindow
* DecorPreview
* PlugPreview
* Mannequin
* HousingDatachron
* CircleRegistration
* GroupDisplayOptions
* FloatTextPanel
* ChallengeLog
* ChallengeRewardPanel
* ArenaTeamRegister

###Caveat

GetAddon may not return anything for one of the above addons if it has not initialized yet.

Example: TradeskillTalents will be accessible until the GenericEvent_InitializeTradeskillTalents event has fired.

Once accessible though you can get a reference to it anytime.