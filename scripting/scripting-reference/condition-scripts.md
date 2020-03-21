# Condition Scripts

Condition Scripts use cases are more rare but can prove convenient in very specific and complex setups. Some situations are just too complex or weird to reduce them to an "if-then" behavior. Then you can use a script and decide to activate this part of the condition as you wish.

For instance, if I want to detect a suite of notes to sing, I could easily create a script that will automatically check the next note to sing in order to validate the condition.

## Condition specific methods \(the local object\)

When scripts are running as a condition, the **local** Javascript object has specific methods to change the validation state of this condition.

| Method | Description | Example |
| :--- | :--- | :--- |
| **setValid\(**_value_**\)** | This sets the validation state of the condition to the _**value**_ | `local.setValid(true);` |

