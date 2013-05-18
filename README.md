Yii-Extension-ReCopy
====================

Yii PHP Framework extension for duplicate form fields


Duplicate form fields, using jQuery relCopy plugin version 1.1.0 from Andres Vidal.
##Requirements
- jQuery
- Yii 1.1 or above

##Installation

- Extract 'reCopy' folder to **protected/extensions/widgets**.

##Usage

Call this widget in the view file, as in the examples, where this widget itself will display the 'add more' link text.      
###Example 1
~~~
<p class="clone">
  First name: <input type="text" name="firstname[]" class='input'/>
  Last name: <input type="text" name="lastname[]" class='input'/>
</p>

<?php 
  $this->widget('ext.widgets.reCopy.ReCopyWidget', array(
     'targetClass'=>'clone',
  )); 
?>
~~~

###Example 2: Customization
~~~
<div class="clone-this">
  First name: <input type="text" name="firstname[]" class='input'/>
  Last name: <input type="text" name="lastname[]" class='input'/>
  Gender: <select name="gender[]">
             <option value="male">Male</option>
             <option value="female">Female</option>
          </select>
</div>

<?php 
  $this->widget('ext.widgets.reCopy.ReCopyWidget', array(
     'targetClass'=>'clone-this',
     'addButtonLabel'=>'Add new',
     'addButtonCssClass'=>'add-clone',
     'removeButtonLabel'=>'Remove this',
     'removeButtonCssClass'=>'remove-clone',
     'limit'=> 5,
  )); 
?>
~~~

###Example 3: Multiple widget call per page
Assign each widget call with unique 'targetClass' and 'addButtonId'.
~~~
[php]
<p class="education-history">
  School attended: <input type="text" name="school[]" class='input'/>
  Year: <input type="text" name="school_year[]" class='input'/>
</p>

<?php 
  $this->widget('ext.widgets.reCopy.ReCopyWidget', array(
     'targetClass'=>'education-history',
     'addButtonId'=>'add-new-education',
     'limit'=>3,
  )); 
?>

<p class="qualification">
  Certificate: <input type="text" name="certificate[]" class='input'/>
  Year: <input type="text" name="cert_year[]" class='input'/>
</p>
 
<?php 
  $this->widget('ext.widgets.reCopy.ReCopyWidget', array(
     'targetClass'=>'qualification',
     'addButtonId'=>'add-new-qualification',
     'removeButtonLabel'=>'Remove this',
     'removeButtonCssClass'=>'remove-clone',
     'limit'=>5,
  )); 
?>
~~~

##Parameters

- **targetClass**: Targeted CSS class for duplication.
- **limit**: The number of allowed copies. Default: 0 is unlimited
- **addButtonId** (>= v1.0.3): Add button id. **Set id differently if this widget is called multiple times per page**.
- **addButtonLabel**: Add more button text.
- **addButtonCssClass**: Add more button CSS class.
- **removeButtonLabel**: Remove button text.
- **removeButtonCssClass**: Remove button CSS class.
- **excludeSelector**: A jQuery selector used to exclude an element and its children. Example: ".exclude"
- **copyClass**: A class to attach to each copy. Default: "copy"
- **clearInputs**: Boolean option to clear each copies text input fields or textarea.

##Change Log
###Version 1.0.3
- Bug fixed: multiple call this widget per page doesn't work.
- Added param 'addButtonId' to handle multiple call this widget per page.

###Version 1.0.2
- Hide 'add more' link button when limit = 1
- Bug fixed: clearInputs=false is not working.

###Version 1.0.1
- Added relCopy.js minified version.
- Added other useful params: limit, excludeSelector, copyClass, clearInputs.

###Version 1.0
- Initial release.

##Resources
 * [Project page](http://www.andresvidal.com/labs/relcopy.html)
 * [Try out a demo](http://demos.9lessons.info/clone.php)
