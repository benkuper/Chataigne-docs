# Scripting Reference

Here you can find an almost exhaustive reference on Chataigne specific functions.

{% hint style="success" %}
Scripts in Chataigne are based on a simplified version of Javascript. Most functions are available, but some might be missing.  If you're missing some functions, please contact me and consider [donating](https://github.com/sponsors/benkuper) so I can spend more time improving Chataigne !
{% endhint %}

{% hint style="info" %}
This documentation only shows functions that I have added on top of JUCE's Javascript Engine. To know all the base functions that are available, you can take a look at the [JavascriptEngine's source code](https://github.com/benkuper/JUCE/blob/develop-local/modules/juce_core/javascript/juce_Javascript.cpp)
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
        <p><code>//init your values, log things and assign variables</code>
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
        from the script by calling <b>script.setUpdateRate</b><em>(rate).</em> see
        below for more informations.</td>
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
</table>

## Parameters and triggers

All parameters and triggers have common methods and specific methods

#### Common methods and properties

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
      <td style="text-align:left">
        <p>Sets a parameter&apos;s attribute.</p>
        <p>All parameters get :
          <br /><em><b>readonly : </b></em>sets the parameter as not editable</p>
        <p><em><b>description : </b></em>change the tooltip description</p>
        <p><em><b>enabled : </b></em>enable or disable this parameter</p>
        <p><em><b>alwaysNotify : </b></em>set the alwaysNotify flag (if true, this
          will trigger updates even if setting the same value than before).
          <br />More information for specific parameters in each parameter&apos;s section.</p>
      </td>
      <td style="text-align:left">
        <p><code>myParam.setAttribute(&quot;readonly&quot;,true);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;description&quot;,&quot; new description&quot;);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;enabled&quot;,false);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;alwaysNotify&quot;, true);</code>
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
    <tr>
      <td style="text-align:left"><b>getControlAddress (</b>[reference]<b>)</b>
      </td>
      <td style="text-align:left">Returns the OSC-style control address of this element. Optional <em><b>reference </b></em>parameter
        allows you to specify a root container to generate the address from.</td>
      <td
      style="text-align:left"><code>script.log( myParam.getControlAddress());</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getScriptControlAddress()</b>
      </td>
      <td style="text-align:left">Returns the script control address of this element.</td>
      <td style="text-align:left"><code>script.log( myParam.getScriptControlAddress());</code>
      </td>
    </tr>
  </tbody>
</table>

### Trigger

| Method | Description | Example |
| :--- | :--- | :--- |
| **trigger\(\)** | Returns the value of this parameter | `myTrigger.trigger();` |

### Float Parameter

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
      <td style="text-align:left"><code>var value = myFloatParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the value of this parameter</td>
      <td style="text-align:left"><code>myFloatParam.set(.5);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Specific attributes :</p>
        <p><em><b>ui : </b></em>The UI to use to show this parameter. Accepted values
          are : <em><b>time, slider,  stepper, label</b></em>
        </p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;ui&quot;, &quot;time&quot;);</code>
      </td>
    </tr>
  </tbody>
</table>

### Integer Parameter

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
      <td style="text-align:left"><code>var value = myIntParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the value of this parameter</td>
      <td style="text-align:left"><code>myIntParam.set(2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Specific attributes :</p>
        <p><em><b>hexMode : </b></em>Whether to show the value as decimal or hexadecimal.</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;hexMode&quot;, true);</code>
      </td>
    </tr>
  </tbody>
</table>

### Boolean Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myBoolParam.get();` |
| **set\(**_value_**\)** | Sets the value of this parameter | `myBoolParam.set(true);` |

### String Parameter

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
      <td style="text-align:left"><code>var value = myStringParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the value of this parameter</td>
      <td style="text-align:left"><code>myStringParam.set(&quot;super&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Specific attributes :</p>
        <p><em><b>multiline</b></em>: whether the parameter can be multiline</p>
        <p><em><b>prefix</b></em>: add a prefix before the value</p>
        <p><em><b>suffix</b></em>: add a suffix after the value</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;multiline&quot;, true);</code>
      </td>
    </tr>
  </tbody>
</table>

### Color Parameter

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
      <td style="text-align:left">Returns the value of this parameter. The result is an array containing
        [r,g,b,a], values are between 0 and 1</td>
      <td style="text-align:left">
        <p><code>var value = myColorParam.get();</code>
        </p>
        <p><code>script.log(&quot;green : &quot;+value[1]);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the value of this parameter. You can either set the value with ARGB
        hex value, [r,g,b,a] float array, or r,g,b,a separate values. r, g and
        b values are always between 0 and 1 and alpha is optional (you can specify
        r,g,b only);</td>
      <td style="text-align:left">
        <p><code>//this is all set to cyan alpha 100%</code>
        </p>
        <p><code>myColorParam.set(0xff00ffff);</code>
        </p>
        <p><code>myColorParam.set([0,1,1,1]);</code>
        </p>
        <p><code>myColorParam.set(0,1,1,1);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Target Parameter

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
      <td style="text-align:left">Returns the string value of the target address</td>
      <td style="text-align:left"><code>var address = myTargetParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getTarget()</b>
      </td>
      <td style="text-align:left">Returns the actual selected target</td>
      <td style="text-align:left"><code>var target = myTargetParam.getTarget();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the string value of the target&apos;s address.</td>
      <td style="text-align:left"><code>myTargetParam.set (&quot;/root/modules/osc&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribute, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Specific attributes :</p>
        <p><em><b>targetType </b></em>: the type of target to search. This can either
          be &quot;<b>container&quot; </b>or &quot;<b>controllable&quot; </b>
        </p>
        <p><em><b>root </b></em>: the root container from which to search</p>
        <p><em><b>searchLevel </b></em>: specify the max level to search from the
          root</p>
        <p><em><b>showParameters </b></em>: if target is controllable, hide or show
          parameters</p>
        <p><em><b>showTriggers </b></em>: if target is controllable, hide or show
          triggers</p>
        <p><em><b>labelLevel </b></em>: the level of parents to show in the UI.</p>
      </td>
      <td style="text-align:left">
        <p><code>myTargetParam.setAttribute (&quot;searchLevel&quot;,2);</code>
        </p>
        <p><code>myTargetParam.setAttribute (&quot;root&quot;, root.sequences);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Enum Parameter

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
      <td style="text-align:left"><b>addOption(</b><em>label, value</em><b>)</b>
      </td>
      <td style="text-align:left">Add an option to the list</td>
      <td style="text-align:left"><code>myEnumParam.addOption(&quot;new option&quot;,3);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">
        <p>1.6.x : Return the selected key</p>
        <p>1.7.x : Return the selected data</p>
      </td>
      <td style="text-align:left">
        <p><code>var label = myEnumParam.get(); //1.6.x</code>
        </p>
        <p><code>var value= myEnumParam.get(); //1.7.x</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getData() (1.6.x)</b>
      </td>
      <td style="text-align:left">Get the selected data (1.6.x only)</td>
      <td style="text-align:left"><code>var data = myEnumParam.getData(); //1.6</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getKey() (1.7.x)</b>
      </td>
      <td style="text-align:left">Get the selected key (1.7.x only)</td>
      <td style="text-align:left"><code>var key = myEnumParam.getKey(); //1.7</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeOptions()</b>
      </td>
      <td style="text-align:left">Removes all options.</td>
      <td style="text-align:left"><code>myEnumParam.removeOptions();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>key</em><b>)</b>
      </td>
      <td style="text-align:left">This sets the parameter to the corresponding key.</td>
      <td style="text-align:left"><code>myEnumParam.set(&quot;Option 1&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setData(</b><em>data</em><b>)</b>
      </td>
      <td style="text-align:left">This sets the parameter to the corresponding data</td>
      <td style="text-align:left"><code>myEnumParam.setData(&quot;data1&quot;);</code>
      </td>
    </tr>
  </tbody>
</table>

### File Parameter

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
      <td style="text-align:left">
        <p>Specific attributes :</p>
        <p><em><b>directoryMode</b></em>: specify if this parameter should be looking
          for a file or a folder</p>
      </td>
      <td style="text-align:left"><code>myFileParam.setAttribute (&quot;directoryMode&quot;,true);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Get the content of the file. If <em><b>asJSON </b></em>is <em>true, </em>then
        the content will be parsed and returned as an Object.</td>
      <td style="text-align:left">
        <p><code>var myTextContent = myFileParam.readFile ();</code>
        </p>
        <p><code>var myJSONContent = myFileParam.readFile (true);</code>
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
        <p><code>myFileParam.writeFile (data, true);</code>
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
    <tr>
      <td style="text-align:left"><b>launchFile(</b><em>arguments<b>)</b></em>
      </td>
      <td style="text-align:left">This will launch the selected file with the <em><b>arguments</b> </em>provided</td>
      <td
      style="text-align:left"><code>myFileParam.launchFile<br />(&quot;--verbose&quot;)</code>
        </td>
    </tr>
  </tbody>
</table>

### Point2D Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myP2DParam.get();` |
| **set\(**_x, y_**\)** | Sets the value of this parameter | `myP2DParam.set(.5, 2);` |

### Point3D Parameter

| Method | Description | Example |
| :--- | :--- | :--- |
| **get\(\)** | Returns the value of this parameter | `var value = myP3DParam.get();` |
| **set\(**_x, y, z_**\)** | Sets the value of this parameter | `myP3DParam.set(.5, 2, -1);` |

## Container

Containers are any object that contains parameters or other containers. If you're targetting something from the hierarchy \(_root.\*_ ****or _local.\*_\), this will be either a container of a parameter, so if it's not a parameter, then it's a container.

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
      <td style="text-align:left"><b>getChild(</b><em>childName</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the parameter or container with the provided name.</td>
      <td style="text-align:left"><code>var child = myContainer.getChild(&quot;activity&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getParent()</b>
      </td>
      <td style="text-align:left">Returns the parent container</td>
      <td style="text-align:left"><code>var parent = myContainer.getParent();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Changes the name of the container</td>
      <td style="text-align:left"><code>myContainer.setName(&quot;new name&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setCollapsed(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Change the collapsed state of the container, if it can be collapsed.</td>
      <td
      style="text-align:left"><code>myContainer.setCollapsed(false);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">This is the name identifier of the object, as you would target it in a
        script.</td>
      <td style="text-align:left"><code>script.log(myContainer.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">This is the &quot;nice name&quot; of the object, as you see it in the
        Inspector.</td>
      <td style="text-align:left"><code>script.log(myContainer.niceName);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">This will add a trigger (button).</td>
      <td style="text-align:left"><code>var myTrigger = myContainer.addTrigger(&quot;My Trigger&quot;, &quot;Trigger description&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">This will add a float number parameter (slider).</td>
      <td style="text-align:left"><code>var myFloatParam = myContainer.addFloatParameter(&quot;My Float Param&quot;,&quot;Description of my float param&quot;,.1,0,1);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">add an integer number parameter (stepper), default value of 2, with a
        range between 0 and 10</td>
      <td style="text-align:left"><code>var myIntParam = myContainer.addIntParameter(&quot;My Int Param&quot;,&quot;Description of my int param&quot;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a boolean parameter (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = myContainer.addBoolParameter(&quot;My Bool Param&quot;,&quot;Description of my bool param&quot;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">add a string parameter (text field)</td>
      <td style="text-align:left"> <code>var myStringParam = myContainer.addStringParameter(&quot;My String Param&quot;,&quot;Description of my string param&quot;, &quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>add a color parameter (color picker).</p>
        <p>You can either set the default color with ARGB hex value, [r,g,b,a] float
          array, or r,g,b,a separate values. r, g and b values are always between
          0 and 1 and alpha is optional (you can specify r,g,b only);</p>
      </td>
      <td style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff); //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot;,&quot;Description of my color param&quot;,[1,0,1]); //default purple</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a point 2d parameter</td>
      <td style="text-align:left"><code>var myP2DParam = myContainer.addPoint2DParameter(&quot;My P2D Param&quot;,&quot;Description of my p2d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a point 3d parameter</td>
      <td style="text-align:left"><code>var myP3DParam = myContainer.addPoint3DParameter(&quot;My P3D Param&quot;,&quot;Description of my p3d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">add a target parameter (to reference another parameter)</td>
      <td style="text-align:left"><code>var myTargetParam = myContainer.addTargetParameter(&quot;My Target Param&quot;,&quot;Description of my target param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description, </em>[directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Add a file parameter (to reference file or folder on the disk).</p>
        <p>If directoryMode is set to true a folder instead of a file can be selected.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = myContainer.addFileParameter(&quot;My File Param&quot;,&quot;Description of my file param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Add a enum parameter (dropdown with options)</p>
        <p>Each pair of values after the first 2 arguments define an option and its
          linked data</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = myContainer.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;, &quot;Option 1&quot;, 1,&quot;Option 2&quot;, 5, &quot;Option 3&quot;, &quot;banana&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addContainer(</b>name<b>)</b>
      </td>
      <td style="text-align:left">Add a container inside of the container.</td>
      <td style="text-align:left"><code>var childContainer = myContainer.addContainer(&quot;My Child Container&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeContainer(</b>name<b>)</b>
      </td>
      <td style="text-align:left">Remove a child container from the container.</td>
      <td style="text-align:left"><code>myContainer.removeContainer (myChildContainer)</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeParameter(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Remove a parameter from the container.</td>
      <td style="text-align:left"><code>myContainer.removeParameter (myChildParameter);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getControlAddress (</b>[reference]<b>)</b>
      </td>
      <td style="text-align:left">Returns the OSC-style control address of this element. Optional <em><b>reference </b></em>parameter
        allows you to specify a root container to generate the address from.</td>
      <td
      style="text-align:left"><code>script.log( myContainer.getControlAddress());</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getScriptControlAddress()</b>
      </td>
      <td style="text-align:left">Returns the script control address of this element.</td>
      <td style="text-align:left"><code>script.log( myContainer.getScriptControlAddress());</code>
      </td>
    </tr>
  </tbody>
</table>

## Manager

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
        <p><code>var newSequence = root.sequences.addItem();</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeItem(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Removes an item. <em><b>item</b></em> must be a item managed by this manager.</td>
      <td
      style="text-align:left"><code>root.modules.removeItem (myModule);</code>
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
    <tr>
      <td style="text-align:left"><b>getItemWithName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the first item found with <em><b>name. </b></em>This will search
        for exact match of niceName, shortName, and lowercase version.</td>
      <td
      style="text-align:left"><code>var introSeq = root.sequences.getItemWithName (&quot;Intro&quot;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAt(</b><em>index</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the item at the <em><b>index.</b></em>
      </td>
      <td style="text-align:left"><code>var curSequence = root.sequences.getItemAt(1); //0 is first, so this will get the second sequence in the list.</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemIndex(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the index of the specified <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var index= root.sequences.getItemIndex (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemBefore(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the item before the specified <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var prevSequence = root.sequences.getItemBefore (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAfter(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Returns the item after the specified <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var nextSequence = root.sequences.getItemAfter (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>reorderItems()</b>
      </td>
      <td style="text-align:left">Reorders all items in this manager.</td>
      <td style="text-align:left">
        <p><code>var mappingLayer = root.sequences.sequence.layers.mapping;</code>
        </p>
        <p><code>mappingLayer.automation.reorderItems();</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Script object

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
      <td style="text-align:left">
        <p>add a color parameter (color picker).</p>
        <p>You can either set the default color with ARGB hex value, [r,g,b,a] float
          array, or r,g,b,a separate values. r, g and b values are always between
          0 and 1 and alpha is optional (you can specify r,g,b only);</p>
      </td>
      <td style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff); //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot;,&quot;Description of my color param&quot;,[1,0,1]); //default purple</code>
        </p>
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
    <tr>
      <td style="text-align:left"><b>setExecutionTimeout( </b><em>timeInSeconds</em><b>)</b>
      </td>
      <td style="text-align:left">Sets the maximum time that a call in the script can take in seconds.</td>
      <td
      style="text-align:left"><code>script.setExecutionTimeout(10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>function scriptParameterChanged (</b><em>param</em><b>)</b>
      </td>
      <td style="text-align:left">This function will be called each time a parameter of this script has
        changed.</td>
      <td style="text-align:left"><code>function scriptParameterChanged(param){    script.log(&quot;Param changed : &quot;+param.name); }</code>
      </td>
    </tr>
  </tbody>
</table>

## Root object

The root object refers to Chataigne's engine, which is the root object of all parent.  
It allows you to access any object in Chataigne's hierarchy. The best way to access them is to right click on a parameter's UI and select "Copy Script control address". Then you can past the address in your script and you will be able to control this parameter.

## Local object

The local object depends on where the scripts is running.

* If the script is running inside a module, the local variable will referring to the module. You can find all the module functions in the [Module Scripts](module-scripts.md) section. 
* If the script is running inside a condition, the local variable will be referring to the condition. You can find all the condition functions in the [Condition Scripts](condition-scripts.md) section. 
* If the script is running inside a filter, the local variable will be referring to the filter. You can find all the filter functions in the [Filter Scripts](filter-scripts.md)[ ](condition-scripts.md)section.

## **Util object**

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
      <td style="text-align:left"><b>fromBase64(</b><em>value</em><b>);</b>
      </td>
      <td style="text-align:left">Returns a converted data block from a base-64 encoded string</td>
      <td style="text-align:left"><code>var str_decoded = util.toBase64(&quot;sGVsbG8gd29ybGQh&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>fileExists(</b><em>path</em><b>)</b>
      </td>
      <td style="text-align:left">Returns true if a file exists at the path provided, otherwise returns
        false</td>
      <td style="text-align:left"><code>script.log(fileExists(&quot;myfile.txt&quot;));</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>directoryExists(</b><em>path</em><b>)</b>
      </td>
      <td style="text-align:left">Returns true if a directory exists at the path provided, otherwise returns
        false</td>
      <td style="text-align:left"><code>script.log(directoryExists(&quot;myFolder&quot;));</code>
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
      <td style="text-align:left"><code>util.createDirectory(&quot;path/to/dir&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectProperties(</b><em>object, includeParameters, includeObjects</em><b>)</b>
      </td>
      <td style="text-align:left">Returns an array of all the properties names of this <em><b>object</b></em>.
        You can specify if you want to include parameters and/or objects (like
        containers) Default is include all.</td>
      <td style="text-align:left"><code>var propNames = util.getObjectProperties(myObject, true, false); //only get parameters</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectMethods(</b><em>object</em><b>)</b>
      </td>
      <td style="text-align:left">Returns an array of all the method names of this <em><b>object</b></em>.</td>
      <td
      style="text-align:left"><code>var methods= util.getObjectMethods();</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>copyToClipboard(</b><em>data, data2...)</em>
      </td>
      <td style="text-align:left">Copies all data joined into string to the clipboard</td>
      <td style="text-align:left"><code>util.copyToClipboard(&quot;super&quot;,5, myData);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getFromClipboard(</b><em>)</em>
      </td>
      <td style="text-align:left">Returns the content of the clipboard</td>
      <td style="text-align:left"><code>var data = util.getFromClipboard();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>showMessageBox(</b><em>title, message, [icon, buttonText]</em><b>)</b>
      </td>
      <td style="text-align:left">Shows a popup message box with only one button. Additionally to title
        and message, you can provide an <b>icon </b>(accepted values are &quot;<em><b>info&quot;, &quot;warning&quot;, &quot;question&quot; </b></em>)
        and the text of the button.</td>
      <td style="text-align:left"><code>util.showMessageBox(&quot;Super info !&quot;, &quot;This is a message for you&quot;, &quot;info&quot;, &quot;Got it&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>showOkCancelBox(</b><em>title, message, [icon, button1Text, button2Text]</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Shows a popup message box with only one button. Additionally to title
          and message, you can provide an <b>icon </b>(accepted values are &quot;<em><b>info&quot;, &quot;warning&quot;, &quot;question&quot; </b></em>)
          and the text of the button.</p>
        <p>This method will return <b>true</b> if the first button has been clicked, <b>false </b>otherwise</p>
      </td>
      <td style="text-align:left"><code>util.showOkCancelBox(&quot;Super warning!&quot;, &quot;This is a warningfor you&quot;, &quot;warning&quot;, &quot;Got it&quot;,&quot;Naaah&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>showYesNoCancelBox(</b><em>title, message, [icon, button1Text, button2Text, button3Text] </em><b>),</b>
      </td>
      <td style="text-align:left">
        <p>Shows a popup message box with only one button. Additionally to title
          and message, you can provide an <b>icon </b>(accepted values are &quot;<em><b>info&quot;, &quot;warning&quot;, &quot;question&quot; </b></em>)
          and the text of the button.</p>
        <p>This method will return either <b>0,1 or 2 </b>depending on the button
          that has been clicked.</p>
      </td>
      <td style="text-align:left"><code>util.showYesNoCancelBox(&quot;Confirm ?&quot;, &quot;Do you really want to do that ?&quot;, &quot;question&quot;, &quot;Yeah&quot;, &quot;Never&quot;, &quot;Don&apos;t care...&quot;);</code>
      </td>
    </tr>
  </tbody>
</table>

