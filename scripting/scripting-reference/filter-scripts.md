---
description: Contributed with love by Benoit Arbelot
---

# Filter Scripts

Filter scripts are JavaScript files that can be used as a filter in a mapping. They are created as separate JavaScript files and can be added in the filter tab by choosing the script option.

![](../../.gitbook/assets/filterscript\_creation.gif)

Filter scripts are useful to add math functions or advanced filtering logic to your mappings.

## Filter specific functions <a href="#condition-specific-methods-the-local-object" id="condition-specific-methods-the-local-object"></a>

When scripts are running as a filter, new function callbacks are called to process the filter.

| Method                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Example                                                                                                                                                                                    |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **function filter(**_inputValue, min, max_**)** | <p>This function is called everytime the mapping is processed and goes through the filter chain.</p><p><em><strong>inputValue</strong></em> is the value from the input or from the preceding filter.</p><p><em><strong>min</strong></em> and <em><strong>max</strong></em> are the range of the <em><strong>inputValue</strong></em>, if applicable. It's useful when filtering the value as a normalized value, or to avoid overshooting the values.<br></p><p><strong>This function must return a value !</strong></p> | <p><code>function filter(inputValue, min, max)</code><br><code>{</code><br><code>var result = inputValue * myFloatParam.get();</code><br><code>return result;</code><br><code>}</code></p> |

In this example, we consider a simple project with a looping audio track. We also have a masterVolume custom variable controlling the audio track volume through a mapping.

![](../../.gitbook/assets/filterscript\_mastervolumeexample\_presentation.gif)

Now we would like to add the ability to fade in and out our audio track. We can do this using sequences which directly control the volume of the audio track. However, in order to respect the current value of the masterVolume, these sequences output need to be remapped from \[0; 1] to \[0; masterVolume].

This can be done with a simple filter script multiplying the output value of the fade sequences mappings by the masterVolume value. We create the following MultiplyByMasterVolume.js script :

```javascript
function filter(inputValue, min, max)
{
    return inputValue*root.customVariables.soundControls.variables.masterVolume.masterVolume.get();
}
```

This filter script returns the input value _**inputValue**_, multiplied by the custom variable masterVolume.

Reminder : You can quickly get the Script address of any variable in Chataigne by right-clicking on it and selecting **Copy Script Control Address**, then you can use the function get() to get the current value of this variable in a script.

We just have to assign this script as a filter script in our fade sequences mappings to get what we want : fading sequences that fade between 0 and the current _masterVolume_ value.

![](../../.gitbook/assets/filterscript\_mastervolumeexample\_withfilterscript.gif)
