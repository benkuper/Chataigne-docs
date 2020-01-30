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
      <td style="text-align:left">init()</td>
      <td style="text-align:left">If present, this function will be called right after the script is loaded.</td>
      <td
      style="text-align:left">
        <p><code>function init() {</code>
        </p>
        <p><code>  //init your values, log things and assign variables</code>
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
        from the script by calling <em>script.updateRate(rate). </em>see below for
        more informations.</td>
      <td style="text-align:left">
        <p><code>function update(deltaTime)</code>
        </p>
        <p><code>{</code>
        </p>
        <p><code>  script.log(&quot;Delta time : &quot; + deltaTime);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>## Standard objects

### Parameters and triggers

All parameters and triggers have common methods and specific methods

#### Common methods

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
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Returns the value of this parameter</td>
      <td style="text-align:left"><code>var value = myColorParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>r, g, b, [a]</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the value of this parameter</td>
      <td style="text-align:left">
        <p><code>myColorParam.set(1, 0, 0); //Red full opaque</code>
        </p>
        <p><code>myColorParam.set(0, 0, 1, .5); // Blue half transparent</code>
        </p>
      </td>
    </tr>
  </tbody>
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

#### Point2D Parameter

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

### Manager

## Special objects

### Script object

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
      <td style="text-align:left"><code>var myFloatParam = script.addFloatParameter(&quot;My Float Param&quot;,&quot;Description of my float param&quot;,.1,0,1); </code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">add an integer number parameter (stepper), default value of 2, with a
        range between 0 and 10</td>
      <td style="text-align:left"><code>var myIntParam = script.addIntParameter(&quot;My Int Param&quot;,&quot;Description of my int param&quot;,2,0,10); </code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a boolean parameter (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = script.addBoolParameter(&quot;My Bool Param&quot;,&quot;Description of my bool param&quot;,false); </code>
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
      <td style="text-align:left"><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff); </code>
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
      <td style="text-align:left"><code>var myTargetParam = script.addTargetParameter(&quot;My Target Param&quot;,&quot;Description of my target param&quot;); </code>
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
      <td style="text-align:left"><code>var myEnumParam = script.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;,  &quot;Option 1&quot;, 1,&quot;Option 2&quot;, 5, &quot;Option 3&quot;, &quot;banana&quot;);</code>
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
      <td style="text-align:left">getTime()</td>
      <td style="text-align:left">Returns the time since system start in seconds</td>
      <td style="text-align:left"><code>var time = util.getTime();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">getTimestamp()</td>
      <td style="text-align:left">Returns the time since January 1st 1970 in seconds</td>
      <td style="text-align:left"><code>var timestamp = util.getTimestamp();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">getFloatFromBytes(byte1, byte2, byte3, byte4)</td>
      <td style="text-align:left">Returns a float from 4 bytes (big endian, byte1 is most significant)</td>
      <td
      style="text-align:left"><code>var value = util.getFloatFromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">getInt32FromBytes(byte1, byte2, byte3, byte4)</td>
      <td style="text-align:left">Returns a 32-bit integer from 4 bytes (big endian, byte1 is most significant)</td>
      <td
      style="text-align:left"><code>var value = util.getInt32FromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">getInt64FromBytes(byte1, byte2, byte3, byte4, byte5, byte6, byte7, byte8)</td>
      <td
      style="text-align:left">Returns a 64-bit integer from 8 bytes (big endian, byte1 is most significant)</td>
        <td
        style="text-align:left"><code>var value = util.getInt64FromBytes(0, 5, 7, 22, 0, 0, 2, 10);</code>
          </td>
    </tr>
    <tr>
      <td style="text-align:left">getIPs()</td>
      <td style="text-align:left">Returns an array of all IP addresses found</td>
      <td style="text-align:left">
        <p><code>var ips = util.getIPs();</code>
        </p>
        <p><code>for(var i=0; i&lt;ips.length; i++) { script.log(ips[i]); }</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">encodeHMAC_SHA1(text, key)</td>
      <td style="text-align:left">Returns a HMAC-SHA1 encoded string</td>
      <td style="text-align:left"><code>var encoded = util.encodeHMAC_SHA1(&quot;my text&quot;, &quot;my key&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">toBase64(value);</td>
      <td style="text-align:left">Returns a converted base-64 string from an utf8 string.</td>
      <td style="text-align:left"><code>var str64 = util.toBase64(&quot;cool&quot;);</code>
      </td>
    </tr>
  </tbody>
</table>### Root object

The root object refers to Chataigne's engine, which is the root object of all parent.  
It allows you to access any object in Chataigne's hierarchy.  The best way to access them is to right click on a parameter's UI and select "Copy Script control address". Then you can past the address in your script and you will be able to control this parameter.



