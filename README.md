# KillNet
<p align="center"><img src="docs/killnet-logo.png" width="200" alt="KillNet logo: a red globe" /></p>

**Multiplayer for ULTRAKILL, over Steam.** Make a party, bring your friends, and play ULTRAKILL's levels together: the same enemies, the same bosses, the same arenas, with voice chat.

KillNet is the multiplayer part of [Killcraft](https://github.com/goonsn/Killcraft) on its own, without Minecraft. KillNet and Killcraft players can be in the same party. Its source is here (`src/`, the launcher in `launcher/app`): it's the same plugin as Killcraft's, run without Minecraft.

## What it does

- **Parties over Steam.** PARTY in ULTRAKILL's main menu: HOST PARTY (name it, pick how many can join, public / friends / private, cheats on or off), JOIN BY CODE, PUBLIC LOBBIES, or a Steam invite. The party host picks the level and everyone goes there.
- **One level for everyone:** shared enemies and bosses (one health bar for all), doors, arenas, breakables, the Cybergrind's waves, and the sandbox's spawner arm.
- **Voice chat** (push to talk, V; or an open mic) heard from where each V1 is, **text chat** (Enter in a level), player colours, a squad list with pings.
- **Spectating** when you die, players bumping into each other (the host's choice), PvP (the host's choice), and being put back on solid ground if you fall out of the map.
- **Replays:** every run is kept. REPLAYS in the main menu lists them with a CASE FILE (rank, damage, secrets, ...); watch them back alone or together with the party.
- **MINOS PRIME mode:** one player becomes Minos Prime, the rest of the party fights him.
- **Your look:** V1's colour, lights and wings' glow on a colour wheel, seen by everyone (and on your own arms).
- More of the level shared: trams, hidden switches, fire, boss intros, and cutscene skips by vote.

Since 2.0.2 KillNet's own download is **Steam only**: none of Killcraft's Minecraft side is in it (no other programs, no local ports, no Discord status). It's the same build as the one made for Thunderstore and Nexus.

## Install

**Easiest:** download `KillNet-Launcher-<version>.exe` from **Releases** and run it. It finds ULTRAKILL, installs BepInEx and KillNet, keeps them (and itself) updated, and starts the game. Leave MINECRAFT on OFF.

> **"Windows protected your PC"?** The launcher isn't code-signed (a signing certificate costs money), so Windows SmartScreen warns about any new exe like it. Click **More info**, then **Run anyway**. Its source is in this repo (`launcher/app`) if you want to check it or build it yourself.
>
> **Installed with r2modman, Gale or the Thunderstore app?** Start ULTRAKILL from there instead: the launcher is for installs in the game's own folder (it tells you if it finds one in a mod manager).

**By hand:**

1. Install **BepInEx 5** into ULTRAKILL: [BepInEx releases](https://github.com/BepInEx/BepInEx/releases) (`BepInEx_win_x64_5.4.x.zip`), unzipped into the ULTRAKILL folder. Start the game once.
2. Download `KillNet-<version>.zip` from **Releases** and unzip it into `ULTRAKILL\BepInEx\plugins\`, so you have `ULTRAKILL\BepInEx\plugins\KillNet\KillNet.dll`. (The settings file is still named after Killcraft.) Updating from 2.0.1 or older: delete `BepInEx\plugins\Killcraft\Killcraft.dll`, but keep the `replays` folder next to it.
3. Start ULTRAKILL and press **PARTY** in the main menu.

Everyone in a party needs the same KillNet / Killcraft version.

## Settings

Esc > KILLNET in a level (party, voice, replays, settings), the KILLNET page in ULTRAKILL's OPTIONS, or `ULTRAKILL\BepInEx\config\dev.killcraft.cfg`.

## Building from source

Needs the .NET SDK (6 or newer) and ULTRAKILL with BepInEx installed.

```
dotnet build -c Release
```

If ULTRAKILL isn't in `C:\Program Files (x86)\Steam\steamapps\common\ULTRAKILL`, add `-p:GameDir="X:\path\to\ULTRAKILL"`. The build copies `Killcraft.dll` into `BepInEx\plugins\Killcraft\` (the plugin keeps Killcraft's name; without Minecraft it runs as KillNet).

KillNet's own Steam-only build (what the releases ship), without any of Killcraft's Minecraft side compiled in:

```
dotnet build -c Release -p:KillNetOnly=true
```

It makes `KillNet.dll`; add `-p:PluginDir="X:\path\to\ULTRAKILL\BepInEx\plugins\KillNet"` to put it where the releases do (with `killcraft-shaders.bundle`, from a release).

The launcher (`launcher/app`, .NET Framework 4.8 WinForms): `cd launcher/app` then `dotnet build -c Release`. Its pictures come from `launcher/design` (`python art.py`, `python icon.py`; Pillow).

## Credits

- Made by goonsn. Part of [Killcraft](https://github.com/goonsn/Killcraft).
- Inspired by UltraLink
- ULTRAKILL by Arsi "Hakita" Patala / New Blood Interactive. KillNet isn't affiliated with them and contains none of their files.

## License

[MIT](LICENSE)
