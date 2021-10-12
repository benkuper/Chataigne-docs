# Making your own module

You can build your own custom modules to add some functionality to Chataigne or support a specific system or device.

Custom modules are localized in the `<Documents>/Chataigne/modules` folder.

To create a custom module, you first need to create a new folder inside the `modules` folder. Inside this folder, you need a `module.json` file that contains all of the module's metadata, as well as the module structure definition (values, parameters, commands, etc). You can find the description for the `module.json` file below.

Most of the time, you'll also want to add a module script file. This file will handle all of the logic behind the module. You can read about how to write a module script here : [Module Scripts](../scripting/scripting-reference/module-scripts.md)

{% hint style="info" %}
When you make changes to the `module.json` file, don't forget to hit `File > Reload custom modules` if Chataigne is running. You will also have to delete the module and create it back.
{% endhint %}

You can also add a 32x32 pixels `icon.png` file in the module folder if you want to use a custom icon for your module.

You can find a custom module example here : [https://github.com/tommag/Sample-Chataigne-module](https://github.com/tommag/Sample-Chataigne-module) . Feel free to fork this repository to create your own module, and don't forget to share it with the community if you feel that it could be useful to someone else !

{% hint style="info" %}
You can also create a "local" module by putting your module's folder inside a folder called "modules" aside the noisette file.\
In this case, this module will only be visible when the noisette file is loaded
{% endhint %}

## `module.json` file definition

If you've never heard about json, you can check out a short explanation here : [https://learnxinyminutes.com/docs/json/](https://learnxinyminutes.com/docs/json/)

### Module metadata

| Key           | Description                                                                                                                  | Example                                                                                |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `name`        | The custom module name                                                                                                       | `"name":"My custom module"`                                                            |
| `type`        | The custom module type. It indicates which base module you want to extend. You can choose here any of the base module names. | `"type":"WebSocket Client"`                                                            |
| `path`        | (Optional) The modules menu path. Choose one of the base submenus or create your own.                                        | `"path":"Hardware"`                                                                    |
| `version`     | (Optional) The module version.                                                                                               | `"version":"1.0.0"`                                                                    |
| `description` | (Optional) Module description                                                                                                | `"description":"My module description"`                                                |
| `url`         | (Optional) Where to find info about this module                                                                              | `"url":"https://github.com/tommag/Sample-Chataigne-module"`                            |
| `downloadURL` | (Optional) Where to download this module                                                                                     | `"downloadURL":"https://github.com/tommag/Sample-Chataigne-module/archive/master.zip"` |

### Base module overriding

The following JSON keys let you decide what you want to keep from the base module. You can get the "short name" of the parameters that you want to control by hovering your mouse over the parameter and checking the control address.

| Key                     | Description                                                                                                                                                                                                  | Example                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------- |
| `hasInput`              | (Optional) Set to false if your module doesn't receive data. This will disable input streams (if applicable), hide the input activity monitor and hide the module values (unless `alwaysShowValues` is set). | `"hasInput":true`                                             |
| `hasOutput`             | (Optional) Set to false if your module doesn't send data. This will disable output streams (if applicable) and hide the output activity monitor.                                                             | `"hasOutput":true`                                            |
| `defaults`              | (Optional) A collection of values to use for the base module parameters                                                                                                                                      | `"defaults": { "autoAdd":false }` (for an OSC module)         |
| `hideDefaultParameters` | (Optional) An array of the parameters you want to hide in the Inspector                                                                                                                                      | `"hideDefaultParameters": [ "autoAdd", "oscInput/localPort"]` |
| `hideDefaultCommands`   | (Optional) Set to true if you want to hide the base module commands (for example in an OSC module, hide the "Custom Message" command)                                                                        | `"hideDefaultCommands":false`                                 |
| `alwaysShowValues`      | (Optional) Set to true if `hasInput` is set to false and you have no values in this module but you still want to be able to add them manually later                                                          | `"alwaysShowValues":true`                                     |

### Custom parameters and values

Check out the [Data types](making-your-own-module.md#data-types) section to learn more about the different data types and the options you can use for them.

| Key          | Description                                                       | Example                                                   |
| ------------ | ----------------------------------------------------------------- | --------------------------------------------------------- |
| `parameters` | A collection of the parameters that you want to add to the module | `"parameters": { "My parameter": { "type":"Integer" } }"` |
| `values`     | A collection of the values that you want to add to the module     | `"values": { "My value": { "type":"Float" } }`            |

### Custom commands

You can also set custom commands. Every command is linked to a "callback function" in the module script.

| Key        | Description                                                     | Example                                                                                        |
| ---------- | --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `commands` | A collection of the commands that you want to add to the module | `"commands": { "My special command": {COMMAND PARAMS}, "Another command": {COMMAND PARAMS} }"` |

Here are the command parameters :

| Key             | Description                                                                                                                                                                                                                         | Example                                           |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| `menu`          | The name of the menu this command should be in                                                                                                                                                                                      | `"menu":"Special commands"`                       |
| `callback`      | The name of the script function to call when this command is triggered                                                                                                                                                              | `"callback":"setParam"`                           |
| `setupCallback` | The name of the script function to call when creating the command. This allows for dynamic creation of commands.                                                                                                                    | `"setupCallback":"commandSetup"`                  |
| `parameters`    | A collection of the command parameters. The script callback function should have as many parameters as this array. Check the [Data types](making-your-own-module.md#data-types) section for more info about the possible data types | `"parameters": { "Value": { "type":"Integer" } }` |

Example:

> "commands": { "Custom command": { "menu":"",\
> "callback":"customCmd", "parameters": { "Value": { "type":"Integer", } } }

### Scripts

| Key       | Description                                                            | Example                            |
| --------- | ---------------------------------------------------------------------- | ---------------------------------- |
| `scripts` | An array that contains the name of the script(s) to add to the modules | `"scripts": [ "moduleScript.js" ]` |

You can find the documentation for module scripts here : [Module Scripts](../scripting/scripting-reference/module-scripts.md)

### Data types

Whenever you need to specify how to handle some data (i.e. for parameters, values or command parameters), you have the following options.

| Key           | Description                                                                                                                                                                                 | Example                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| `type`        | The type of the data. Possible options are: `Container`, `Boolean`, `Float`, `Integer`, `Enum`, `String`, `File`, `Point2D`, `Point3D`, `Target`, `Color`.                                  | `"type":"Integer"`                        |
| `readOnly`    | (Optional) Whether the variable can be changed by the user                                                                                                                                  | `"readOnly":true`                         |
| `shortName`   | (Optional) Set a custom short name                                                                                                                                                          | `"shortName":"easyParamName"`             |
| `description` | (Optional) Description to show in the tooltips                                                                                                                                              | `"description":"This is a cool variable"` |
| `min`         | (Optional) If applicable, set the min value for this variable. For `Point2D`, `Point3D` types, you can specify an array.                                                                    | `"min":0` for an `Integer`                |
| `max`         | (Optional) If applicable, set the max value for this variable. For `Point2D`, `Point3D` types, you can specify an array.                                                                    | `"max":0.8` for a `Float`                 |
| `default`     | (Optional) If applicable, set the default value for this variable. For `Point2D`, `Point3D` types, you can specify an array.                                                                | `"default":[0.5, 8]` for a `Point2D`      |
| `dependency`  | (Optional) (Except for `Container`) Specify an action to do based on another variable value. Check [Advanced data handling](making-your-own-module.md#advanced-data-handling) for more info |                                           |

#### Containers

Data declared with `Container` has no value but is used to group other variables. It also has a `collapsed` property:

| Key         | Description                                                                | Example            |
| ----------- | -------------------------------------------------------------------------- | ------------------ |
| `collapsed` | If set to true, the GUI panel defaults to collapsed (children not visible) | `"collapsed":true` |

Example:

> "System parameters": { "type":"Container", "collapsed":true, "First variable": { "type":"Float", "default":20, "description":"This is the first variable"}, "Second variable": { "type":"Float", "default":0} }

#### Enums

The `Enum` type is used to let the user choose between a set of values. It has an extra `options` property:

| Key       | Description                                                                              | Example                                             |
| --------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------- |
| `options` | A collection of possible values. Each value has a display string and an associated data. | `"options": { "Option 1":optl", "Option 2":"opt2"}` |

Example:

> "Test Enum": { "type":"Enum", "options": { "All":"all", "Single":"single" } }

#### Float UI types

When setting a variable to `Float` type, there is an extra `ui` property, used to customize the GUI.

| Key  | Description                                            | Example         |
| ---- | ------------------------------------------------------ | --------------- |
| `ui` | Possible options: `stepper`, `slider`, `label`, `time` | `"ui":"slider"` |

### Advanced data handling

You can also change the UI based on the values of other variables. For example, you may want to display different options based on the value of an `Enum`.

For this purpose, you have to add the `dependency` property to the variable, then add the following properties (all required):

| Key      | Description                                                                         | Example               |
| -------- | ----------------------------------------------------------------------------------- | --------------------- |
| `source` | The name of the variable you want to refer to                                       | `"source":"testEnum"` |
| `value`  | What value to compare `source` to                                                   | `"value":"all"`       |
| `check`  | Which check to perform. Possible values: `equals`, `notEquals`                      | `"check":"equals"`    |
| `action` | Which action to perform when check is successful. Possible values: `show`, `enable` | `"action":"show"`     |

Example: This example alternates between two different options based on the enum choice.

> "parameters": { "My variable type": { "type":"Enum", "options": { "Float":"float", "Integer":"int" } }, "Variable (float)": { "type":"Float", "dependency": { "source":"myVariableType", "value":"float", "check":"equals", "action":"show" } }, "Variable (int)": { "type":"Integer", "dependency": { "source":"myVariableType", "value":"int", "check":"equals", "action":"show" } } }
