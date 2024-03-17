# Sense ESP
This documentation is for Sense ESP Credit To The Owner

## Booting the Sense ESP Library
```lua
-- 1. Load the library
local Sense = loadstring(game:HttpGet('https://sirius.menu/sense'))()

-- 2. Change the configuration.
Sense.teamSettings.enemy.enabled = true
Sense.teamSettings.enemy.box = true
Sense.teamSettings.enemy.boxColor[1] = Color3.new(0, 0.25, 0.75)

-- 3. Load the esp. It doesn't really matter where you put this, but it's recommended you put it at the end of your script.
Sense.Load()

-- 4. Unload the esp. When you unload Sense, it will clean up every drawing object and instance it has made.
--Sense.Unload()
```




## Configuring
```lua
Sense = {
  whitelist = {}, -- When this table contains at least 1 user id, it will only show esp for those players.
  sharedSettings = {
      textSize = 13,
      textFont = 2,
      limitDistance = false, -- Set a maximum render distance
      maxDistance = 150,
      useTeamColor = false -- Change all colors to the players team color
  },
  teamSettings = {
      enemy = {
          enabled = false,
          box = false,
          boxColor = { Color3.new(1,0,0), 1 },
          --boxColor = { "Team Color", 1 }, -- Do this to change a single color to the team color
          boxOutline = true,
          boxOutlineColor = { Color3.new(), 1 },
          boxFill = false,
          boxFillColor = { Color3.new(1,0,0), 0.5 },
          healthBar = false,
          healthyColor = Color3.new(0,1,0),
          dyingColor = Color3.new(1,0,0),
          healthBarOutline = true,
          healthBarOutlineColor = { Color3.new(), 0.5 },
          healthText = false,
          healthTextColor = { Color3.new(1,1,1), 1 },
          healthTextOutline = true,
          healthTextOutlineColor = Color3.new(),
          box3d = false,
          box3dColor = { Color3.new(1,0,0), 1 },
          name = false,
          nameColor = { Color3.new(1,1,1), 1 },
          nameOutline = true,
          nameOutlineColor = Color3.new(),
          weapon = false,
          weaponColor = { Color3.new(1,1,1), 1 },
          weaponOutline = true,
          weaponOutlineColor = Color3.new(),
          distance = false,
          distanceColor = { Color3.new(1,1,1), 1 },
          distanceOutline = true,
          distanceOutlineColor = Color3.new(),
          tracer = false,
          tracerOrigin = "Bottom",
          tracerColor = { Color3.new(1,0,0), 1 },
          tracerOutline = true,
          tracerOutlineColor = { Color3.new(), 1 },
          offScreenArrow = false,
          offScreenArrowColor = { Color3.new(1,1,1), 1 },
          offScreenArrowSize = 15,
          offScreenArrowRadius = 150,
          offScreenArrowOutline = true,
          offScreenArrowOutlineColor = { Color3.new(), 1 },
          chams = false,
          chamsVisibleOnly = false,
          chamsFillColor = { Color3.new(0.2, 0.2, 0.2), 0.5 },
          chamsOutlineColor = { Color3.new(1,0,0), 0 },
      },
      friendly = {
          enabled = false,
          box = false,
          boxColor = { Color3.new(0,1,0), 1 },
          boxOutline = true,
          boxOutlineColor = { Color3.new(), 1 },
          boxFill = false,
          boxFillColor = { Color3.new(0,1,0), 0.5 },
          healthBar = false,
          healthyColor = Color3.new(0,1,0),
          dyingColor = Color3.new(1,0,0),
          healthBarOutline = true,
          healthBarOutlineColor = { Color3.new(), 0.5 },
          healthText = false,
          healthTextColor = { Color3.new(1,1,1), 1 },
          healthTextOutline = true,
          healthTextOutlineColor = Color3.new(),
          box3d = false,
          box3dColor = { Color3.new(0,1,0), 1 },
          name = false,
          nameColor = { Color3.new(1,1,1), 1 },
          nameOutline = true,
          nameOutlineColor = Color3.new(),
          weapon = false,
          weaponColor = { Color3.new(1,1,1), 1 },
          weaponOutline = true,
          weaponOutlineColor = Color3.new(),
          distance = false,
          distanceColor = { Color3.new(1,1,1), 1 },
          distanceOutline = true,
          distanceOutlineColor = Color3.new(),
          tracer = false,
          tracerOrigin = "Bottom",
          tracerColor = { Color3.new(0,1,0), 1 },
          tracerOutline = true,
          tracerOutlineColor = { Color3.new(), 1 },
          offScreenArrow = false,
          offScreenArrowColor = { Color3.new(1,1,1), 1 },
          offScreenArrowSize = 15,
          offScreenArrowRadius = 150,
          offScreenArrowOutline = true,
          offScreenArrowOutlineColor = { Color3.new(), 1 },
          chams = false,
          chamsVisibleOnly = false,
          chamsFillColor = { Color3.new(0.2, 0.2, 0.2), 0.5 },
          chamsOutlineColor = { Color3.new(0,1,0), 0 }
      }
  }
}
```

## Game Functions
```lua
function EspInterface.getWeapon(player)
    return "Unknown";
end

function EspInterface.isFriendly(player)
    return player.Team and player.Team == localPlayer.Team;
end

function EspInterface.getTeamColor(player)
    return player.Team and player.Team.TeamColor and player.Team.TeamColor.Color;
end

function EspInterface.getCharacter(player)
    return player.Character;
end

function EspInterface.getHealth(player)
    local character = player and EspInterface.getCharacter(player);
    local humanoid = character and findFirstChildOfClass(character, "Humanoid");
    if humanoid then
        return humanoid.Health, humanoid.MaxHealth;
    end
    return 100, 100;
end
```

## Instance ESP
```lua
local object = Sense.AddInstance(workspace.Part, {
    --enabled = false,
    text = "{name}", -- Placeholders: {name}, {distance}, {position}
    textColor = { Color3.new(1,1,1), 1 },
    textOutline = true,
    textOutlineColor = Color3.new(),
    textSize = 13,
    textFont = 2,
    limitDistance = false,
    maxDistance = 150
})

object.options.enabled = false
```
