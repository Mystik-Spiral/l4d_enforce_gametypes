### `Enforce Gametypes`
(l4d_enforce_gametypes) by *_Mystik Spiral_*


**Objective:**

* Prevent client using mm_dedicated_force_servers to override sv_gametypes on server.
* Reject client connection if mp_gamemode set by lobby reservation is not included in sv_gametypes.


**Description and options:**

My server has sv_gametypes set to "coop,realism,nightmaredifficulty", but I was seeing other active game modes, like "versus", "survival", and "scavenge". I discovered that clients were setting mm_dedicated_force_servers to my server IP address and port, then connecting from lobby. When a client sets mm_dedicated_force_servers (in the client console), it overrides the value for sv_gametypes in the server and allows connections for any mp_gamemode. This simple plugin checks the value of mp_gamemode (set during lobby reservation) and compares it to the values in sv_gametypes... if there is no match the client connection is rejected.

Please be aware this will block all mutations that are not listed in sv_gametypes, even if the base gamemode for the mutation is listed.

This plugin does not have any configurable console variables, though it does read the values for the Valve console variables sv_gametypes and mp_gamemode.

Please ensure these two Valve console variables are explicitly set in the server.cfg file the way you want them:

sv_hibernate_when_empty  
sb_all_bot_game


**Notes:**

This plugin does not kick clients, it starts before that and rejects connection to the server for non-matching gamemodes. 
 
If sv_gametypes is not set in your server.cfg file, it should default to: 
coop,realism,survival,versus,scavenge,dash,holdout,shootzones
 
I do not plan to add any new features, but if you find any bugs, please let me know and I will do my best to correct them.  I have only tested this with L4D2, but I expect it should also work with L4D1.  It will probably work with any game that uses sv_gametypes and mp_gamemode.


**Credits:**

Game modes on/off/tog code: Silvers  
Reminder that mp_gamemode may be set in server.cfg: Mika Misori  
Reminder that L4D1/2 map names are different: Ja-Forces
 
Want to contribute code enhancements?
Create a pull request using this GitHub repository: https://github.com/Mystik-Spiral/l4d_enforce_gametypes

Plugin discussion: https://forums.alliedmods.net/showthread.php?t=342570


**Changelog:** 

26-Jun-2023 v1.4
- Fixed compatibility issue with L4D1

19-Jun-2023 v1.3
- Fixed issue if mp_gamemode was defined in server.cfg

08-May-2023 v1.2
- Reject connections if changelevel is already in progress to reset the mp_gamemode

02-May-2023 v1.1
- On reject, changelevel to set an allowed mp_gamemode (uses first entry in sv_gametypes).

25-Apr-2023 v1.0
- Initial release


**Installation:**

Place the l4d_enforce_gametypes.smx file in the SourceMod "plugins" directory.

