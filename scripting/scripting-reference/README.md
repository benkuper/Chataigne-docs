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


| **get\(\)** | Returns the value of this parameter | `var value = myColorParam.get();` |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>set(</b><em>r, g, b, [a]</em><b>)</b>
      </th>
      <th style="text-align:left">Sets the value of this parameter</th>
      <th style="text-align:left">
        <p><code>myColorParam.set(1, 0, 0); //Red full opaque</code>
        </p>
        <p><code>myColorParam.set(0, 0, 1, .5); // Blue half transparent</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>#### Target Parameter

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
      <td style="text-align:left">Write the content of a string of an Object to the selected file. If the
        file exists, <em><b>overwriteIfExists </b></em>will let you decide whether
        to overwrite it or not (false by default).</td>
      <td style="text-align:left">
        <p><code>var data = &quot;super&quot;;</code>
        </p>
        <p><code>myFileParam.write(data, true);</code>
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

| Method | Description | Example |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>addItem(</b><em>[type]</em><b>)</b>
      </th>
      <th style="text-align:left">
        <p>Adds an item to the manager and returns it.</p>
        <p>Some managers like the Module manager or the layer manager can create
          multiple types of items. Thus they need a type of item to create, which
          you must set in the <em><b>type</b></em> argument.</p>
        <p>Other managers like the Sequence manager don&apos;t need this argument
          because there is only one type of sequence. In these cases you don&apos;t
          need to provide an argument when calling the function.</p>
      </th>
      <th style="text-align:left">
        <p><code>var newOSCModule = root.modules.addItem(&quot;OSC&quot;);</code>
        </p>
        <p>&lt;code&gt;&lt;/code&gt;</p>
        <p><code>var newSequence = root.sequences.addItem();</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **removeItem\(**_item_**\)** | Removes an item. _**item**_ must be a item managed by this manager. | `root.modules.removeItem(myModule);` |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>items</b>
      </th>
      <th style="text-align:left">This is an array containing all the it</th>
      <th style="text-align:left">
        <p><code>var items = root.sequences.items;</code>
        </p>
        <p><code>script.log(&quot;Num sequences : &quot;+items.length);</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>### Script object

The script object refers to the script container. You can add your own custom parameters here, as well as logging informations, warnings and errors.

| Method | Description | Example |
| :--- | :--- | :--- |


| **addTrigger\(**_name, description_**\)** | This will add a trigger \(button\) | `var myTrigger = script.addTrigger("My Trigger", "Trigger description");` |
| :--- | :--- | :--- |


| **addFloatParameter\(**_name, description, default, min max_**\)** | This will add a float number parameter \(slider\). | `var myFloatParam = script.addFloatParameter("My Float Param","Description of my float param",.1,0,1);` |
| :--- | :--- | :--- |


| **addIntParameter\(**_name, description, default, min max_**\)** | add an integer number parameter \(stepper\), default value of 2, with a range between 0 and 10 | `var myIntParam = script.addIntParameter("My Int Param","Description of my int param",2,0,10);` |
| :--- | :--- | :--- |


| **addBoolParameter\(**_name, description, default_**\)** | add a boolean parameter \(toggle\) | `var myBoolParam = script.addBoolParameter("My Bool Param","Description of my bool param",false);` |
| :--- | :--- | :--- |


| **addStringParameter\(**_name, description, default_**\)** | add a string parameter \(text field\) |  `var myStringParam = script.addStringParameter("My String Param","Description of my string param", "cool");` |
| :--- | :--- | :--- |


| **addColorParameter\(**_name, description, default_**\)** | add a color parameter \(color picker\) | `var myColorParam = script.addColorParameter("My Color Param","Description of my color param",0xff0000ff);` |
| :--- | :--- | :--- |


| **addPoint2DParameter\(**_name, description_**\)** | add a point 2d parameter | `var myP2DParam = script.addPoint2DParameter("My P2D Param","Description of my p2d param");` |
| :--- | :--- | :--- |


| **addPoint3DParameter\(**_name, description_**\)** | add a point 3d parameter | `var myP3DParam = script.addPoint3DParameter("My P3D Param","Description of my p3d param");` |
| :--- | :--- | :--- |


| **addTargetParameter\(**_name, description_**\)** | add a target parameter \(to reference another parameter\) | `var myTargetParam = script.addTargetParameter("My Target Param","Description of my target param");` |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </th>
      <th style="text-align:left">
        <p>add a enum parameter (dropdown with options)</p>
        <p>Each pair of values after the first 2 arguments define an option and its
          linked data</p>
      </th>
      <th style="text-align:left"><code>var myEnumParam = script.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;, &quot;Option 1&quot;, 1,&quot;Option 2&quot;, 5, &quot;Option 3&quot;, &quot;banana&quot;);</code>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **log\(**_message_**\)** | Logs a message \(must activate "Log" in the script parameters\) | `script.log("This is a message");` |
| :--- | :--- | :--- |


| **logWarning\(**_message_**\)** | Logs a message as a warning | `script.logWarning("This is a warning");` |
| :--- | :--- | :--- |


| **logError\(**_message_**\)** | Logs a message as an error | `script.logError("This is an error");` |
| :--- | :--- | :--- |


| **setUpdateRate\(**_rate_**\)** | Sets the rate at which the update\(\) function is called | `script.setUpdateRate(50);` |
| :--- | :--- | :--- |


The local object depends on where the scripts is running.

* If the script is running inside a module, the local variable will referring to the module. You can find all the module functions in the [Module Scripts](module-scripts.md) section. 
* If the script is running inside a condition, the local variable will be referring to the condition. You can find all the condition functions in the [Condition Scripts](condition-scripts.md) section. 
* If the script is running inside a filter, the local variable will be referring to the filter. You can find all the filter functions in the [Filter Scripts](filter-scripts.md)[ ](condition-scripts.md)section.

### **Util object**

The util object provides helpers and utility functions like time or conversion.

| Method | Description | Example |
| :--- | :--- | :--- |


| **getTime\(\)** | Returns the time since system start in seconds | `var time = util.getTime();` |
| :--- | :--- | :--- |


| **getTimestamp\(\)** | Returns the time since January 1st 1970 in seconds | `var timestamp = util.getTimestamp();` |
| :--- | :--- | :--- |


| **getFloatFromBytes\(**_byte1, byte2, byte3, byte4_**\)** | Returns a float from 4 bytes \(big endian, byte1 is most significant\) | `var value = util.getFloatFromBytes(0, 0, 2, 10);` |
| :--- | :--- | :--- |


| **getInt32FromBytes\(**_byte1, byte2, byte3, byte4_**\)** | Returns a 32-bit integer from 4 bytes \(big endian, byte1 is most significant\) | `var value = util.getInt32FromBytes(0, 0, 2, 10);` |
| :--- | :--- | :--- |


| **getInt64FromBytes\(**_byte1, byte2, byte3, byte4, byte5, byte6, byte7, byte8_**\)** | Returns a 64-bit integer from 8 bytes \(big endian, byte1 is most significant\) | `var value = util.getInt64FromBytes(0, 5, 7, 22, 0, 0, 2, 10);` |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>getIPs()</b>
      </th>
      <th style="text-align:left">Returns an array of all IP addresses found</th>
      <th style="text-align:left">
        <p><code>var ips = util.getIPs();</code>
        </p>
        <p><code>for(var i=0; i&lt;ips.length; i++) { script.log(ips[i]); }</code>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| **encodeHMAC\_SHA1\(**_text, key_**\)** | Returns a HMAC-SHA1 encoded string | `var encoded = util.encodeHMAC_SHA1("my text", "my key");` |
| :--- | :--- | :--- |


| **toBase64\(**_value_**\);** | Returns a converted base-64 string from an utf8 string. | `var str64 = util.toBase64("cool");` |
| :--- | :--- | :--- |


The root object refers to Chataigne's engine, which is the root object of all parent.  
It allows you to access any object in Chataigne's hierarchy. The best way to access them is to right click on a parameter's UI and select "Copy Script control address". Then you can past the address in your script and you will be able to control this parameter.

