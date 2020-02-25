# Scripting Reference

Here you can find an almost exhaustive reference on Chataigne specific functions.

{% hint style="info" %}
Scripts in Chataigne are based on a simplified version of Javascript. Most functions are available, but some might be missing. If you're missing some functions, please contact me and consider [donating](https://github.com/sponsors/benkuper) so I can spend more time improving Chataigne !
{% endhint %}

## Common Functions

There are few common functions that you can use, no matter the type of script.

{% hint style="info" %}
None of the functions below are needed when making a script, they are just helper functions.  
If you don't need them, don't add them in your script as Chataigne will optimize your script depending on the available functions in it.
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>init()</b>
      </td>
      <td style="text-align:left">If present, this function will be called right after the script is loaded.</td>
      <td
      style="text-align:left">
        <p><code>function init() {</code>
        </p>
        <p> <code>//init your values, log things and assign variables</code>
        </p>
        <p><code>}</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>update(</b><em>deltaTime</em><b>)</b>
      </td>
      <td style="text-align:left">If present, this function will be called regularly at rate specified by
        the &quot;Update rate&quot; script parameter. This parameter is only visible
        when the function is present in the script. You can also change the rate
        from the script by calling <b>script.updateRate</b><em>(rate).</em> see below
        for more informations.</td>
      <td style="text-align:left">
        <p><code>function update(deltaTime)</code>
        </p>
        <p><code>{</code>
        </p>
        <p> <code>script.log(&quot;Delta time : &quot; + deltaTime);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Parameters and triggers

All parameters and triggers have common methods and specific methods

#### Common methods and properties

|  |  |  |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>getParent()</b>
      </td>
      <td style="text-align:left">Returns the value of this parameter</td>
      <td style="text-align:left"><code>myParam.getParent();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the parameters name</td>
      <td style="text-align:left"><code>myParam.setName(&quot;new name&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets a parameter&apos;s attribute.
        <br />More information below</td>
      <td style="text-align:left">
        <p><code>myParam.setAttribute(&quot;readonly&quot;,true);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;description&quot;,&quot; new description&quot;);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;enabled&quot;,false);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>isParameter()</b>
      </td>
      <td style="text-align:left">returns whether the target is a parameter or a trigger</td>
      <td style="text-align:left"><code>var isParam = myTarget.isParameter();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">This is the name identifier of the object, as you would target it in a
        script.</td>
      <td style="text-align:left"><code>script.log(myParam.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">This is the &quot;nice name&quot; of the object, as you see it in the
        Inspector.</td>
      <td style="text-align:left"><code>script.log(myParam.niceName);</code>
      </td>
    </tr>
  </tbody>
</table>#### Trigger

| Method | Description | Example |
| :--- | :--- | :--- |
| **trigger\(\)** | Returns the value of this parameter | `myTrigger.trigger();` |

#### Float Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myFloatParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myFloatParam.set(.5);` |

#### Integer Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myIntParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myIntParam.set(2);` |

#### Boolean Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myBoolParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myBoolParam.set(true);` |

#### String Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myStringParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myStringParam.set("super");` |

#### Color Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myStringParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myStringParam.set("super");` |

#### Target Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the string value of the target address | `var address = myTargetParam.get();` |
| **getTarget\(\)** | Returns the actual selected target | `var target = myTargetParam.getTarget();` |
| **set\(**_value_**\)** | Sets the string value of the target's address. | `myTargetParam.set("/root/modules/osc");` |

#### Enum Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **addOption\(**_label, value_**\)** | Add an option to the list | `myEnumParam.addOption("new option",3);` |
| **get\(\)** | Get the selected label | `var label = myEnumParam.get();` |
| **getData\(\)** | Get the selected data | `var data = myEnumParam.getData();` |
| **set\(**_label_**\)** | Sets the value with the provided label | `myEnumParam.set("new option");` |

#### File Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">Set specific FileParameter attribute (see examples)</td>
      <td style="text-align:left"><code>myFileParam.setAttribute(&quot;directoryMode&quot;,true);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Get the content of the file. If <em><b>asJSON </b></em>is <em>true, </em>then
        the content will be parsed and returned as an Object.</td>
      <td style="text-align:left">
        <p><code>var myTextContent = myFileParam.readFile();</code>
        </p>
        <p><code>var myJSONContent = myFileParam.readFile(true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(data, </b><em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Write the content or a string of an Object to the selected file. If the
        file exists, <em><b>overwriteIfExists </b></em>will let you decide whether
        to overwrite it or not (false by default).</td>
      <td style="text-align:left">
        <p><code>var data = &quot;super&quot;;</code>
        </p>
        <p><code>myFileParam.writeFile(data, true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getAbsolutePath()</b>
      </td>
      <td style="text-align:left">Returns the absolute path for this file.</td>
      <td style="text-align:left"><code>var path = myFileParam.getAbsolutePath();</code>
      </td>
    </tr>
  </tbody>
</table>#### Point2D Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myP2DParam.get();` |
| **set\(**_x, y_**\)** | Sets the value of this parameter | `myP2DParam.set(.5, 2);` |

#### Point3D Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myP3DParam.get();` |
| **set\(**_x, y, z_**\)** | Sets the value of this parameter | `myP3DParam.set(.5, 2, -1);` |

### Container

| Method | Description | Example |
| :--- | :--- | :--- |
| **getChild\(**_childName_**\)** | Returns the parameter or container with the provided name. | `var child = myContainer.getChild("activity");` |
| **getParent\(\)** | Returns the parent container | `var parent = myContainer.getParent();` |
| **setName\(**_name_**\)** | Changes the name of the container | `myContainer.setName("new name");` |
| **setCollapsed\(**_value_**\)** | Change the collapsed state of the container, if it can be collapsed. | `myContainer.setCollapsed(false);` |
| **name** | This is the name identifier of the object, as you would target it in a script. | `script.log(myContainer.name);` |
| **niceName** | This is the "nice name" of the object, as you see it in the Inspector. | `script.log(myContainer.niceName);` |

### Manager

Managers are special types of container. In the software, you can see that a container is a manager when there is a "**+**" icon on the right of its block. Well, almost all the times, some of them are just enhanced containers. Most of the times, the managers you will be interested in are the **Module manager, the Sequence manager, Layer managers and Automation keys managers.**

When a manipulating a manager, you have access to specific functions and properties like adding items, removing items or getting an array of it's items.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>addItem(</b><em>[type]</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Adds an item to the manager and returns it.</p>
        <p>Some managers like the Module manager or the layer manager can create
          multiple types of items. Thus they need a type of item to create, which
          you must set in the <em><b>type</b></em> argument.</p>
        <p>Other managers like the Sequence manager don&apos;t need this argument
          because there is only one type of sequence. In these cases you don&apos;t
          need to provide an argument when calling the function.</p>
      </td>
      <td style="text-align:left">
        <p><code>var newOSCModule = root.modules.addItem(&quot;OSC&quot;);</code>
        </p>
        <p>&lt;code&gt;&lt;/code&gt;</p>
        <p><code>var newSequence = root.sequences.addItem();</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeItem(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Removes an item. <em><b>item</b></em> must be a item managed by this manager.</td>
      <td
      style="text-align:left"><code>root.modules.removeItem(myModule);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItems()</b>
      </td>
      <td style="text-align:left">Returns an array containing all the items of this manager.</td>
      <td style="text-align:left">
        <p><code>var items = root.sequences.getItems();</code>
        </p>
        <p><code>script.log(&quot;Num sequences : &quot;+items.length);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Script object

The script object refers to the script container. You can add your own custom parameters here, as well as logging informations, warnings and errors.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">This will add a trigger (button)</td>
      <td style="text-align:left"><code>var myTrigger = script.addTrigger(&quot;My Trigger&quot;, &quot;Trigger description&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">This will add a float number parameter (slider).</td>
      <td style="text-align:left"><code>var myFloatParam = script.addFloatParameter(&quot;My Float Param&quot;,&quot;Description of my float param&quot;,.1,0,1);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">add an integer number parameter (stepper), default value of 2, with a
        range between 0 and 10</td>
      <td style="text-align:left"><code>var myIntParam = script.addIntParameter(&quot;My Int Param&quot;,&quot;Description of my int param&quot;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a boolean parameter (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = script.addBoolParameter(&quot;My Bool Param&quot;,&quot;Description of my bool param&quot;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a string parameter (text field)</td>
      <td style="text-align:left"> <code>var myStringParam = script.addStringParameter(&quot;My String Param&quot;,&quot;Description of my string param&quot;, &quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a color parameter (color picker)</td>
      <td style="text-align:left"><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a point 2d parameter</td>
      <td style="text-align:left"><code>var myP2DParam = script.addPoint2DParameter(&quot;My P2D Param&quot;,&quot;Description of my p2d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a point 3d parameter</td>
      <td style="text-align:left"><code>var myP3DParam = script.addPoint3DParameter(&quot;My P3D Param&quot;,&quot;Description of my p3d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a target parameter (to reference another parameter)</td>
      <td style="text-align:left"><code>var myTargetParam = script.addTargetParameter(&quot;My Target Param&quot;,&quot;Description of my target param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description, </em>[directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Add a file parameter (to reference file or folder on the disk).</p>
        <p>If directoryMode is set to true a folder instead of a file can be selected.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = script.addFileParameter(&quot;My File Param&quot;,&quot;Description of my file param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>add a enum parameter (dropdown with options)</p>
        <p>Each pair of values after the first 2 arguments define an option and its
          linked data</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = script.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;, &quot;Option 1&quot;, 1,&quot;Option 2&quot;, 5, &quot;Option 3&quot;, &quot;banana&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>log(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Logs a message (must activate &quot;Log&quot; in the script parameters)</td>
      <td
      style="text-align:left"><code>script.log(&quot;This is a message&quot;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logWarning(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Logs a message as a warning</td>
      <td style="text-align:left"><code>script.logWarning(&quot;This is a warning&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logError(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Logs a message as an error</td>
      <td style="text-align:left"><code>script.logError(&quot;This is an error&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setUpdateRate(</b><em>rate</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the rate at which the update() function is called</td>
      <td style="text-align:left"><code>script.setUpdateRate(50);</code>
      </td>
    </tr>
  </tbody>
</table>### Local object

The local object depends on where the scripts is running.

* If the script is running inside a module, the local variable will referring to the module. You can find all the module functions in the [Module Scripts](module-scripts.md) section. 
* If the script is running inside a condition, the local variable will be referring to the condition. You can find all the condition functions in the [Condition Scripts](condition-scripts.md) section. 
* If the script is running inside a filter, the local variable will be referring to the filter. You can find all the filter functions in the [Filter Scripts](filter-scripts.md)[ ](condition-scripts.md)section.

### **Util object**

The util object provides helpers and utility functions like time or conversion.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Method</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>getTime()</b>
      </td>
      <td style="text-align:left">Returns the time since system start in seconds</td>
      <td style="text-align:left"><code>var time = util.getTime();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getTimestamp()</b>
      </td>
      <td style="text-align:left">Returns the time since January 1st 1970 in seconds</td>
      <td style="text-align:left"><code>var timestamp = util.getTimestamp();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getFloatFromBytes(</b><em>byte1, byte2, byte3, byte4</em><b>)</b>
      </td>
      <td style="text-align:left">Returns a float from 4 bytes (big endian, byte1 is most significant)</td>
      <td
      style="text-align:left"><code>var value = util.getFloatFromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt32FromBytes(</b><em>byte1, byte2, byte3, byte4</em><b>)</b>
      </td>
      <td style="text-align:left">Returns a 32-bit integer from 4 bytes (big endian, byte1 is most significant)</td>
      <td
      style="text-align:left"><code>var value = util.getInt32FromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt64FromBytes(</b><em>byte1, byte2, byte3, byte4, byte5, byte6, byte7, byte8</em><b>)</b>
      </td>
      <td style="text-align:left">Returns a 64-bit integer from 8 bytes (big endian, byte1 is most significant)</td>
      <td
      style="text-align:left"><code>var value = util.getInt64FromBytes(0, 5, 7, 22, 0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getIPs()</b>
      </td>
      <td style="text-align:left">Returns an array of all IP addresses found</td>
      <td style="text-align:left">
        <p><code>var ips = util.getIPs();</code>
        </p>
        <p><code>for(var i=0; i&lt;ips.length; i++) { script.log(ips[i]); }</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>encodeHMAC_SHA1(</b><em>text, key</em><b>)</b>
      </td>
      <td style="text-align:left">Returns a HMAC-SHA1 encoded string</td>
      <td style="text-align:left"><code>var encoded = util.encodeHMAC_SHA1(&quot;my text&quot;, &quot;my key&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>toBase64(</b><em>value</em><b>);</b>
      </td>
      <td style="text-align:left">Returns a converted base-64 string from an utf8 string.</td>
      <td style="text-align:left"><code>var str64 = util.toBase64(&quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>path,</em><b> </b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Get the content of the file at <em><b>path</b></em>. If <em><b>asJSON </b></em>is <em>true, </em>then
        the content will be parsed and returned as an Object.</td>
      <td style="text-align:left"><code>var myTextContent = util.readFile(&quot;myfile.txt&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(</b><em>path, data</em><b>, </b><em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Write the content of a string or an Object to the file at <em><b>path</b></em> .
        If the file exists, <em><b>overwriteIfExists </b></em>will let you decide
        whether to overwrite it or not (false by default).</td>
      <td style="text-align:left">
        <p><code>var data = &quot;super&quot;;</code>
        </p>
        <p><code>util.writeFile(&quot;myfile.txt&quot;, data, true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>createDirectory(</b><em>folderPath</em><b>)</b>
      </td>
      <td style="text-align:left">Creates a directory at the path specified.</td>
      <td style="text-align:left">util.createDirectory(&quot;path/to/dir&quot;);</td>
    </tr>
  </tbody>
</table>The root object refers to Chataigne's engine, which is the root object of all parent.  
It allows you to access any object in Chataigne's hierarchy. The best way to access them is to right click on a parameter's UI and select "Copy Script control address". Then you can past the address in your script and you will be able to control this parameter.

