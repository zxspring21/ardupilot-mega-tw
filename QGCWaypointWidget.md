#summary 使用 QGroundControl 航點部件說明

# 介紹 #

使用 QGroundControl 航點列表部件說明。

本文內容更新到 2/5/2011．

ArduPilotMega 和　QGroundControl 都在開發中，因此更新會很頻繁


# 細節 #

The QGroundControl Waypoint List widget can be used to view the current mission loaded to ArduPilotMega, change waypoints/commands in the mission, and upload mission changes to APM

The widget looks like this (may vary with QGroundControl revision and setup)

![http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Waypoints.png](http://wiki.ardupilot-mega.googlecode.com/git/images/ArduPilotMegaImages/QGC_Waypoints.png)

Clicking the "Read" button (lower right) will cause the current mission command list to be downloaded from ArduPilotmega

The Waypoint labelled 0 is the home location

The first field in each Waypoint(Command)is the Command Type.  This field is a dropdown box which will let you pick from available commands.
Additional fields will vary with the command type.  Please note that all fields are not relevant to, or used by, ArduPilotMega.  In particular fields which specify if a waypoint location is Global (absolute) or Local (relative) are not used at this time.  The checkbox on the right indicating the UAV should automatically continue after the waypoint is also not.

The three buttons on the right side of the waypoint line allow the waypoint to be moved up, moved down, or deleted from the mission.

Changes made to the mission in the Waypoint List widget have no effect on ArduPilotMega till they are uploaded.  Use the "Write" button (lower right) to send the changed mission to ArduPilotMega.

The remaining five buttons on the bottom of the widget allow for mission files to be saved to or retrieved from the ground stations local hard drive, setting the UAV's current location as a waypoint, adding a waypoint, or deleting all of the commands in the mission.

**IMORTANT THINGS TO UNDERSTAND**
When you upload waypoints/command changes to the current command while ArduPilotMega is in AUTO mode, those changes will not take effect.  APM loads the command parameters from EEPROM when the command becomes active and does not use the values stored in EEPROM for ongoing calculations.  If you want APM to react to a changed current waypoint you have uploaded you need to switch out of, and then back in to AUTO mode.