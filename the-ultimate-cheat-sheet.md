---
description: >-
  This page will try as hard as it can to show you all the hidden gems of
  Chataigne, hopefully making you a superpowered Chataigne user !
---

# The Ultimate Cheat Sheet

## Editing Parameters

Generally in the software, trying to right click and see if there are more options is a good idea.\
For example, right clicking on a parameter in the inspector allows you to have extended options about it. You can change its range (if allowed), send it to the Dashboard, copy its script or OSC control address...

![Right click on any parameter in the inspector to reveal a new world of possibilities !](.gitbook/assets/rightclick.gif)

## Common shortcuts

| Shortcut                     | Description                                                                                                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| (Ctrl or ⌘) + N              | Creates a new file                                                                                                                                                            |
| (Ctrl or ⌘) + O              | Opens a file                                                                                                                                                                  |
| (Ctrl or ⌘) + Shift + O      | Opens the last opened file                                                                                                                                                    |
| (Ctrl or ⌘) + S              | Saves the current file                                                                                                                                                        |
| (Ctrl or ⌘) + Shift + S      | Saves the current file as a new file (Save as...)                                                                                                                             |
| (Ctrl or ⌘) + ;              | Edit Preferences (in the Inspector)                                                                                                                                           |
| (Ctrl or ⌘) + ,              | Edit Project Settings (saved in the file)                                                                                                                                     |
| (Ctrl or ⌘) + C              | Copies the current selection                                                                                                                                                  |
| (Ctrl or ⌘) + V              | <p>Paste the current selection<br>This will only work when pasting items of the same type.</p>                                                                                |
| (Ctrl or ⌘) + X              | Cuts the current selection                                                                                                                                                    |
| (Ctrl or ⌘) + D              | Duplicates the current selection                                                                                                                                              |
| Alt + O                      | <p>Import a LiLNut file and add all the content of this file to the existing one.</p><p>Content can be Modules, States, Custom Variables, <br>Module Router and Sequences</p> |
| Alt + S                      | <p>Exports the current selection to a LilNut file.</p><p>Content can be Modules, States, Custom Variables,<br>Module Router and Sequences</p>                                 |
| (Ctrl or ⌘) + Select an Item | Toggles an item's selection state                                                                                                                                             |
| Shift + Select an Item       | Select all elements up to this one                                                                                                                                            |

## Inspector shortcuts

| Shortcut                            | Description               |
| ----------------------------------- | ------------------------- |
| Shift + Click on a Container header | Toggle children collapsed |

![](.gitbook/assets/toggle.gif)

| Shortcut                    | Description                           |
| --------------------------- | ------------------------------------- |
| On a Slider or number label |                                       |
| Alt + Drag                  | Decreases the sensitivity of the drag |
| Shift + Drag                | Increases the sensitivity of the drag |

## State Machine shortcuts

| Shortcut                                               | Description                                                    |
| ------------------------------------------------------ | -------------------------------------------------------------- |
| <p>Mouse middle<br>button drag</p><p>or Alt + drag</p> | Navigate in the State Machine View                             |
| F                                                      | Frame the view to the center of all States                     |
| H                                                      | Home to the absolute center of the view.                       |
| Mouse wheel                                            | <p>Scrolls up and down (might change </p><p>in the future)</p> |
| Shift + Mouse wheel                                    | Zoom in / out                                                  |
| Shift + Enter in a comment                             | Add a new line                                                 |

## Time Machine shortcuts

### Timeline Manipulation

| Shortcut                                           | Description                                               |
| -------------------------------------------------- | --------------------------------------------------------- |
| <p>Drag the blue bar <br>horizontal / vertical</p> | <p></p><p>Zoom in/out and change the time focus frame</p> |
| Right click on the blue bar                        | Reset the view to a full view of the whole sequence       |

![](.gitbook/assets/timemachine.gif)

| Shortcut                                    | Description                                                                |
| ------------------------------------------- | -------------------------------------------------------------------------- |
| Right-click drag on the blue bar            | <p></p><p>Selective zoom on a part of the timeline (absolute)</p>          |
| Right click drag on the numbers             | Selective zoom on a part of the timeline (relative)                        |
| (Ctrl or ⌘) + Left click drag on the number | Show menu for adding/removing timespan                                     |
| Shift + drag the time needle                | Snap the time to timeline elements (cues, triggers, other mapping keys...) |

![](.gitbook/assets/timespan.gif)

| Shortcut                             | Description                                                                |
| ------------------------------------ | -------------------------------------------------------------------------- |
| Double-click on the timeline numbers | Create a Time Cue                                                          |
| Shift + drag a cue                   | Move the trigger with snapping (time bar, triggers, other mapping keys...) |



![](.gitbook/assets/cues.gif)

### Mapping Layer (and Mapping 2D)

| Shortcut                     | Description                                                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Double click  on empty space | Create a new key at that position                                                                                             |
| Double click on curve        | <p>Adds a point, <br>keeping the overall shape intact</p>                                                                     |
| Shift + drag a key           | Keep key's value, only move position                                                                                          |
| Alt + drag a key             | Keep key's position, only move value                                                                                          |
| Shift + Alt + drag a key     | Keep key's value, only move position with snapping on other layers elements (time bar, cues, triggers, other mapping keys...) |
| (Ctrl or ⌘) + click on curve | Change the curve easing type                                                                                                  |
| (Ctrl or ⌘) + shift + drag   | Manually draw the curve                                                                                                       |

![](<.gitbook/assets/draw .gif>)

### Module shortcuts

| Shortcut                     | Description                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------- |
| Drag the module into a State | Show menu to automatically use it as an input or output for Action or Mapping |

![](.gitbook/assets/module.gif)

| Shortcut                     | Description                                                 |
| ---------------------------- | ----------------------------------------------------------- |
| Click on the activity arrows | Toggles Log Incoming / Log Outgoing options for this module |

![](.gitbook/assets/logInOut.gif)
