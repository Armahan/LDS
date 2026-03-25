# Lego Destruction System (LDS) for Roblox

**Created by Samtyy** *(Aka Armahan, Prymitif, Durkheim)*

The **Lego Destruction System (LDS)** is a highly optimized, voxel-based destruction engine designed for Roblox. It dynamically processes CSG (Constructive Solid Geometry) subtractions to create satisfying, blocky craters on any BasePart, while instantly generating physics-simulated debris that inherits the exact textures and materials of the destroyed object.

![LDS Preview](https://image.noelshack.com/fichiers/2026/12/1/1773686853-capture-d-cran-2026-03-16-194653.png)

## Key Features

* **Voxel Grid Snapping:** Impacts don't just make messy holes; they carve out perfect 2x2x2 blocky craters for that classic "brick" aesthetic.
* **Zero Server Lag:** A strict Server-Client architecture. The server calculates the math and CSG, while the client handles *all* physics, particles, and sounds.
* **Smart Debris:** Debris isn't just generic plastic. It perfectly inherits the Color, Material, Textures, and Decals of the original wall.
* **Suction System:** Built-in client optimization where players naturally "vacuum" up nearby debris to keep the workspace clean.
* **Anti-Freeze Protection:** The server automatically caps recursive cuts to prevent engine crashes during massive explosions.

## Full Documentation

For the complete API reference, Client Configuration settings, and Part Attributes (like `Unbreakable` and `Undividable`), please visit the official documentation website:

👉 **[Read the LDS Documentation Here](https://armahan.github.io/LDS/#overview)**

## Quick Setup

1. Create a `Folder` named **`Breakable`** inside your `Workspace`. Put any destructible parts inside it.
2. Place the **LDS Server Module** inside `ReplicatedStorage.Assets.Modules.Server.LDS`.
3. Place the **LDS Client LocalScript** inside `StarterPlayer.StarterPlayerScripts`.
4. Initialize the system from a Server Script:

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local DestructionModule = require(ReplicatedStorage.Assets.Modules.Server.LDS)

DestructionModule.Start()

-- Trigger an explosion at Vector3(0, 10, 0)
DestructionModule.ProcessImpact(Vector3.new(0, 10, 0), {
    ImpactRadius = 10,
    HoleVoidRadius = 4,
    ImpactForce = 100
})
