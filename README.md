# DUFuelMon
Dual Universe Fuel Monitor with HUD

Why are you here?

1)You were given the link and asked to try it out: Welcome, see instructions below, please provide comments on Discord(KVeen#3678)

2)You searched for Dual Universe on GitHub: Welcome as well, but this code is not ready for general distribution. You can try it out by following the instructions below but it is currently in limited distribution for testing. A public release should be available soon. 

Installation Instructions:
1) Place a Programming Board on your ship, and optionally, screens
2) Select "DU Programming Board Paste" above and select the 'Raw' view
3) Copy the entire block of code
4) In-game, right click on your Programming Board, select 'advanced' and then "Paste LUA Configuration from Clipboard"
5) Enter construct build-mode and connect any of the following using the link tool:
    **-Atmo Fuel Tanks
    -Space Fuel Tanks
    -Screens**
   **NOTE:** tanks connected first will be to the left of tanks connected after them on the final display, if you want to change the order, disconnect the tanks and reconnect them in the order you want from left to right. All Nitron are always the the left of Kergon however.
6) Exit build mode and activate the programming board

**Optional:** You can connect a switch or zone detector to the Programming board, ensuring you link FROM the switch/zone detector TO the Programming board. This will auto-start the Fuel Monitor, However, the HUD feature will ONLY activate if you manually activate the board. This is a built in game limitation not a feature.

**System behavior**

  1) You can connect any combination up to 10 of the items above (10 is the Programming Board limit)
  2) All screens connected will show the fuel levels of all connected tanks dynamically
  3) If the board was manually activated, a fuel HUD will appear in the upper left of your screen HOWEVER this version does NOT dynamically resize. Right click on the board, select advanced->Edit LUA Parameters. Using the fuel_xpos, fuel_ypos, and fuel_size variables you can adjust the size and position of the HUD element for your monitor/screen resolution
  4) The Screen will show 'ON at the top when actively updating, and 'OFF' when, you know, it is off.
  5) The HUD will show a clock when running, since that is handy, and the HUD would not be there if it was not on.....(the timeoffset variable in LUA parameters will adjust for your timezone/DST, you have to figure that part out, I don't know where you live)

Variables under Lua Parameters (right-click board, advanced->Edit LUA Parameters)

**displayTime:** checkbox, turns clock on/off in HUD display

**timeOffset:** used to adjust timezone/DST settings, you figure out the right number for you....

**timemode12:** If you are weak and need a 12-hour clock, check this box, otherwise use 24 hour time like normal people

**useHUD:** enables/disables the HUD view when the board is manually activated

**fuel_xpos:** left/right HUD position, 0 all the way left, 100 all the way right

**fuel_ypos:** up/down HUD position, 0 at the top, 100 at the bottom

**fuel_size:** scaling factor for the HUD size, bigger number bigger HUD

**WarnPoint:** percentage of fuel where the tank bar will change to orange

**CriticalPoint:** percentage of fuel where the tank bar will turn red

**opacity:** transparency factor-number between 0 and 1 (e.g.  0.5 is 50% transparent) great for those transparent screens or if you use the HUD while flying


**Common questions pre-answered:**

1) Can I use this while flying? Sure, but you have to manually activate the board, this is a game limitation that HUDs can only be displayed when the player directly inrteracts with the controller. If you place a screen (transparent are good for this) in your vision path while flying and connect the board via a switch that is activated by your controller, then it will update as you fly that way as well.

2) Does this work with ArchHud? Sure, but see above, you would have to manually activate it for the HUD to appear and you will have to play around with sizing and transparency. ArchHud can be configured to activate a switch attached the ArchHud controller, which you can then link into (FROM switch TO board) the programming board and it will run and update any screens you have attached while you are flying but the HUD will not show up unless you manually activate the board. You can do this from the seat once you sit in it if the board is visible.

3) Does this work with any other HUD? Sure, it works great with my custom HUD since that is what it was designed for, but beyond that and ArchHUD, no idea, good luck!

4) Why is the HUD so small when I first start it? You should buy a bigger monitor....The HUD code was ported over from another project and currenlty does not dynamically resize in the stand-alone fuel monitor. In short, HUD sizes are driven by your actual computers monitor resolution and the game resolution. In-game screens are fixed size and the actual resolution does not change so they should always be fine. The scaling factor for the HUD has been tested on 3840x2160 resolution and 1920x1080 resolution, but does not change itself, you have to manually figure out the right number in the fuel_size variable right now and the tank configuration on your ship.

    4a) Follow on question: will the HUD resize be fixed in the future? Yes, this is a simple fix, but tied to a more complex problem with the current code, it will be fixed and the HUD will dynamically adjust to your particular screen resolution, just not in this version
  
5) Can I connect anything else to the board? Sure, let me know if it breaks....it should ignore anything other than the three item types listed above AND Databanks. It actually does something if you connect a databank, or multiple databanks, but you can't see it and it is not related to stand-alone functionality, so there is no reason to attach one now. That will be part of a future project release.
6) Why is the source code not available in easy to read format? Does this mean you are evil?  It will be later,and Yes. The code was ported from other projects and is frankly, a mess. I am cleaning it up but wanted to get it out to some folks to test the functionality before advertising it for release. The HUD portion has a band-aid on a patch, covered in duct tape at the moment to make the sizing issue resolvable and should NOT be generally installed. The code, in documented and readable form will be available when it is actually released and actually advertised, probably in the next couple weeks
7) Can I use this with a seat/cockpit that is already attached to the fuel tanks? Sure, with limits. Fuel tanks should allow up to 3 controllers to be attached simultaneously, so you can have a seat/cockpit and ECU or two seats and still connect the FuelMon. However, if you have 2 seats and and ECU, then it will not work without removing a link. Pro-tip: The ECU default configuration will sometimes link fuel tanks, however it does not use them. You can disconnect ECU links to fuel tanks and the ECU will still work, but it may be connected sucking up one of your available connections
8) What of the magic of the new LUA screens, why have you neglected these wonderous additions to the game? Yeah, about that...the screen code has been ported to LUA screen format, but there are some issues. There is no efficiency gained using LUA screens in this use-case AND the code is different from what is required to be used for HUD's. So until NQ allows LUA screen code to work with HUDs (no idea why they would) or something else changes, no LUA screen in this project. A future project is planned to integrate the FuelMon with a LUA screen that would allow multiple players to interact with it, but that is a different use case and the actual display code will be entirely different in all liklihood. (if you were wondering about the Databank comment above, that is why, it actually does currently load fuel percentages to the Databank for anything else to read that is attached to the DataBank)
9) What about rockets? Planned but low priority, I don't use rockets in any of my ship builds and do not even own a rocket fuel tank in-game and did not write the original code to support rockets since it was for my own use originally. If there is interest, adding rocket fuel is possible but frankly not high on my priority list.
10) I want to connect more than 10 tanks and screens, how do I do that? You don't with this version. See Databank comment above. It will eventually be possible to merge the output of multiple FuelMon boards into a single display. Technically, it only requires a very small change to support up to 9 fuel tanks of each type already, however, the display scale would be non-optimal (understatement). Supporting more than 9 of each type is possible but will require more work, and if you have that many fuel tanks, wow, just wow.
11) But my other HUD already has Fuel monitoring, is this more accurate or something? Maybe. Non-vanilla Flight HUDs often pull mass figures from the core and try to figure out how much fuel you have based on weight. But this is dependant on talents applied which cannot currenlty be determined using LUA so they require you to know and enter the fuel tank optimizations applied to your particular ship by the builder based on their talents. Sometimes you know this, sometimes it is a spirited search for truth and lots of trial and error. FuelMon pulls the actual tank percentage straight from the tanks getData() function and will always be accurate (within a 1% rounding error, because math) even if talents are re-applied to a ship and change. ArchHud and DU Damage Report can both be perfectly accurage IF you set the parameters correctly, but FuelMon does not require any configuration, just linking to tanks.
12) In one of your pictures, there is a screen that shows element status maps in top, side and front views at the same time, can I get a copy of that? Sure, it comes with the ship, happy to sell you a token in-game....that is a LUA screen running something functionaly equivalent to DU Damage Report but using the LUA screen renderer. However, there are some performance issues with the LUA screen, as soon as I fix them and make it portable to other ships, I will release it for free. Right now, it works fine in ships it has been designed to work in, but I would not trust it to work elsewhere at the moment and it is not a high priority for me, since it works great in all my ships. 
13) What about tank names? How do I know which is which? Great design question...my design goal was a clean minimalist fuel display without extraneous information. Tank names can be added, however, it would require the player to manually rename their tanks or have the default name garbage showing up and tends to clutter the display excessively. I do plan to add the ability to display tank names/identifiers on request for individual tanks but not display them constantly. For putting them in a particular order, the order you connect them matters. They show up from left to right in order of connection if you just connect, but if you right click the board, you will see the slots are named s1-s10. Connect the tanks you want to appear to the left with lower numbers. However, all Nitron will always be on the left and all Kergon will be on the right, ordered by which slot you connected them to.
14) What about pretty colors, can I change the colors? No. Planned. Ability to add logos backgrounds and banners is also planned, no timeline for that yet. This is a pre-beta script version for running on a beta game. Once functionality is confirmed, bells and whistles can be added.
