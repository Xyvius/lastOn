lastOn
======

lastOn is an event script for the SimpleServer (a Minecraft Server tunnel) Events System.


#### LastOn, by Xyvius

This event provides a quick output of the last few (# is configurable, default is 4) players on. As of V2.0 it also tracks the Most players that have been on at once, broadcasting whenever a new record is set.

The event should be called from the onPlayerConnect event. See the example below. (I preceed it with a sleep in order to delay the initial output till after the other "On Connect" items (i.e. MOTD, etc.)

```xml
<event name="onPlayerConnect">
    sleep 1000
    run lastOn true
</event>
```
Note:  The event is called from the onPlayerConnect event using the argument "true".  This is to be set anytime that you want the event to actually update the player name list.  The reason for this, if it is not obvious, is so that if you desire you can also set up a custom command which allows your players to view this data at will without "reordering" the list every time they do so. (See example below)

```xml
<command name="laston" allow="1+" event="lastOn"/>
```

To customize the number of Player names displayed (I use 7 on my server) simply change #numDisp from 4 to whatever you would like and adjust the number of global variables at the bottom to match (The naming scheme should be obvious).
