# lastOn
### Version: 1.1.0
### By: Xyvius
### Updated: 2.21.14
### lastOn is a simple event script which displays the last players (the number to display is configurable) to logon.
#### See REM statements which start with *** for customization...

```xml
<event name="lastOn">
	rem Init Vars
		set '#update '#rest to #POP Aexplode
	rem *** Change number below to number of players you would like to display! 
	rem ***(Don't forget to add variables at bottom to match!)
		set '#numDisp 4
		set '#count #numDisp
		set '#msg " "
		set '#vers "1.1.0"
		set '#players getplayers
		set '#numOn #players Asize
	rem *** Change the numbers below to change the "Color Scheme" of the displayed text. Use standard MC defined colors. 0-9,A-F
		set '#colorMain 6
		set '#colorName f
		set '#colorHigh e
		set '#colorCred 9
		set '#colorVers b

	rem Disp Header
		say #PLAYER "§" #colorMain . "-=== Last" . #numDisp .. "Players to LogOn / ReSpawn ===- §" .. #colorCred . "(lastOn§" . #colorVers . "v" .. #vers . "§" . #colorCred . "By:Xyvius)§r" .
		
	rem Disp last players on
		while #count 0 gt
			set '#msgA "§" #colorMain . #count . ":§" . #colorName .
			set '#msgB "'$lastOn_" #count . evalvar
			if #msgB "Xyvius" eq
				set '#msgA "§b" #count . ":§9" .
			endif
			set '#msg #msg #msgA .. #msgB .
			dec '#count
		endwhile
		say #PLAYER #msg

	rem Set $lastOn_X (Max On Simu.)
		if #numOn $lastOn_X gt
			set '$lastOn_X #numOn
			broadcast "§" #colorHigh . "New Record!§" . #colorMain . "- Most Players Online: §" .. #colorHigh . $lastOn_X .. " §" .. #colorMain . "Players§r" .
		else
			say #PLAYER "§" #colorMain . "-=== Most players Online: §" . #colorHigh . $lastOn_X .. " §" .. #colorMain . "Players§r" .
		endif
		
	rem Update List?
		if #update true eq
		rem Check player in list?
			set '#limit #numDisp
			while #count #numDisp lt
				inc '#count
				set '#player "'$lastOn_" #count . evalvar
				if #PLAYER #player eq
					set '#limit #count
				endif
			endwhile
		rem Set Shift Limit
			if #limit #count lt
				set '#count #limit
			endif
		rem Shift names
			while #count 1 gt
				set '$lastOn_ #count . '$lastOn_ #count 1 - . evalvar
				dec '#count
			endwhile
		rem Set player to last on
			set '$lastOn_1 #PLAYER
		endif
	</event>
<event name="lastOn_1" value="Notch"/>
<event name="lastOn_2" value="Dinnerbone"/>
<event name="lastOn_3" value="Jeb"/>
<event name="lastOn_4" value="Zelda"/>

rem *** copy the above line changing number to next in sequence to add more positions.
	
<event name="lastOn_X" value="0"/>
```
