# DUFuelMon
Dual Universe Fuel Monitor
Why are you here?
1)You were given the link and asked to try it out: Welcome, see instructions below, please provide comments on Discord
2)You searched for Dual Universe on GitHub: Welcome as well, but this code is not ready for general distribution. You can try it out by following the instructions below but it is currently in limited distribution for testing. A public release should be available soon. 

Installation Instructions:
1) Place a Programming Board on your ship, and optionally, screens
2) Select "DU Programming Board Paste" above and select the 'Raw' view
3) Copy the entire block of code
4) In-game, right click on your Programming Board, select 'advanced' and then "Paste LUA Configuration from Clipboard"
5) Enter construct build-mode and connect any of the following using the link tool:
    -Atmo Fuel Tanks
    -Space Fuel Tanks
    -Screens
6) Exit build mode and activate the programming board

Optional: You can connect a switch or zone detector to the Programming board, ensuring you link FROM the switch/zone detector TO the Programming board. This will auto-start the Fuel Monitor, However, the HUD feature will ONLY activate if you manually activate the board. This is a built in game limitation not a feature.

System behavior 
  -You can connect any combination up to 10 of the items above (10 is the Programming Board limit)
  -All screens connected will show the fuel levels of all connected tanks dynamically
  -If the board was manually activated, a fuel HUD will appear in the upper left of your screen HOWEVER this version does NOT dynamically resize
      -Right click on the board, select advanced->Edit LUA Parameters
      -Using the fuel_xpos, fuel_ypos, and fuel_size variables you can adjust the size and position of the HUD element for your monitor/screen resolution
  -The Screen will show 'ON at the top when actively updating, and 'OFF' when, you know, it is off.
  -The HUD will show a clock when running, since that is handy, and the HUD would not be there if it was not on.....(the timeoffset variable in LUA parameters will adjust for your timezone/DST, you have to figure that part out, I don't know where you live)

Variables under Lua Parameters (right-click board, advanced->Edit LUA Parameters)
displayTime: checkbox, turns clock on/off in HUD display
timeOffset: used to adjust timezone/DST settings, you figure out the right number for you....
timemode12: If you are weak and need a 12-hour clock, check this box, otherwise use 24 hour time like normal people
useHUD: enables/disables the HUD view when the board is manually activated
fuel_xpos: left/right HUD position, 0 all the way left, 100 all the way right
fuel_ypos: up/down HUD position, 0 at the top, 100 at the bottom
fuel_size: scaling factor for the HUD size, bigger number bigger HUD
WarnPoint: percentage of fuel where the tank bar will change to orange
CriticalPoint: percentage of fuel where the tank bar will turn red
opacity: transparency factor-number between 0 and 1 (e.g.  0.5 is 50% transparent) great for those transparent screens or if you use the HUD while flying


Common questions pre-answered:

-Can I use this while flying? Sure, but you have to manually activate the board, this is a game limitation that HUDs can only be displayed when the player directly inrteracts with the controller. If you place a screen (transparent are good for this) in your vision path while flying and connect the board via a switch that is activated by your controller, then it will update as you fly that way as well.

-Does this work with ArchHud? Sure, but see above, you would have to manually activate it for the HUD to appear and you will have to play around with sizing and transparency. ArchHud can be configured to activate a switch attached the ArchHud controller, which you can then link into (FROM switch TO board) the programming board and it will run and update any screens you have attached while you are flying.

-Does this work with any other HUD? Sure, it works great with my custom HUD since that is what it was designed for, but beyond that and ArchHUD, no idea, good luck!

-Why is the HUD so small when I first start it? You should buy a bigger monitor....The HUD code was ported over from another project and currenlty does not dynamically resize in the stand-alone fuel monitor. In short, HUD sizes are driven by your actual computers monitor resolution and the game resolution. In-game screens are fixed size and the actual resolution does not change so they should always be fine. The scaling factor for the HUD has been tested on 3840x2160 resolution and 1920x1080 resolution, but does not change itself, you have to manually figure out the right number in the fuel_size variable right now.
  -Follow on question: will the HUD resize be fixed in the future? Yes, this is a simple fix, but tied to a more complex problem with the current code, it will be fixed and the HUD will dynamically adjust to your particular screen resolution, just not in this version
  
Can I connect anything else to the board? Sure, let me know if it breaks....it should ignore anything other than the three item types listed above AND Databanks. It actually does something if you connect a databank, or multiple databanks, but you can't see it and it is not related to stand-alone functionality, so there is no reason to attach one now. That will be part of a future project release.
