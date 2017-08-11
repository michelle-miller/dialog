---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Tutorial
{: #tutorial_tutorials}

Use the following tutorial to learn how to design dialogs.
{: shortdesc}

## Creating a simple dialog
{: #tutorial_advanced}

This tutorial uses code examples to teach you about the relationships between various dialog nodes and to explain how to design a dialog that helps Mike's Pizza customers order pizza from a virtual agent.

### Before you begin

Because so many open source and commercial options for XML editors are available, this tutorial does not recommend that you use a specific one. You can use the XML editor of your choice. If you're new to XML or you're simply interested in how one editor compares to another, see [a list of comparisons between XML editors ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/Comparison_of_XML_editors){: new_window}.

To learn about the most commonly used XML elements in dialogs before you start the tutorial, see [Nodes](/docs/services/dialog/nodes.html#layout_nodes).

Download and install [the {{site.data.keyword.dialogshort}} tool ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/dialog-tool){: new_window}. Use the tool to manage and test the dialogs you create.

### Set up a basic XML dialog: a folder, a greeting, and a question-and-answer pair
{: #tutorial_basicsetup}

To begin, set up a folder structure, a greeting, and a question-and-answer pair.

### Before you begin
{: #tutorial_basicsetup__basicsetup_prereq}

-   Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_1_end.xml" download="Exercise_1_end.xml">Exercise 1 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.
-   Create a blank XML file from the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/WatsonDialogDocument_1.1.xsd" download="WatsonDialogDocument_1.1.xsd">XML schema <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.

### Procedure

1.  Create settings for the dialog. To learn more about your options, see the [setting](/docs/services/dialog/setting.html) element. To use default values for all required settings, do not manually specify any settings.
1.  Review the following folder structure, and create it in your XML file.

    ```xml
    <dialog xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="WatsonDialogDocument_1.0.xsd">
      <flow>
        <folder label="Main" id="Main"></folder>
          <folder label="Library" id="Library">
            <folder label="Live Content" id="Live Content"></folder>
            <folder label="Storage" id="Storage"></folder>
          </folder>
        <folder label="Concepts" id="Concepts"></folder>
      </flow>
    </dialog>
    ```
    {: codeblock}

    Ensure that your dialog file contains the opening and closing &lt;dialog&gt; tags.

    For more information about these folders, see [folder](/docs/services/dialog/nodes.html#layout_folder).

1.  Review the following greeting, and create it in your XML file.

    ```xml
    <folder label="Main">
      <output>
        <prompt selectionType="RANDOM">
          <item>Hello, welcome to Mike's Pizza</item>
        </prompt>
        <goto ref="getUserInput_2449614"/>
      </output>
      <getUserInput id="getUserInput_2449614">
        <search ref="folder_2449611"/>
        <default>
          <output>
            <prompt selectionType="RANDOM">
              <item>
                I am sorry, I did not understand your question.
                Please try asking another one.
              </item>
            </prompt>
          </output>
        </default>
      </getUserInput>
    </folder>
    ```
    {: codeblock}

    The first node must be an output to display a message to users so that they have some context of what they are doing. The message is in the item node. The getUserInput node prompts users to ask a question. The search node searches the location that is specified by the ref attribute for a response to user input. The default node provides a response in an output node when the search is unsuccessful.

1.  Review the following question-and-answer pair, and create it in your XML file.

    Every top-line node in Live Content must be an input node so that when the system searches the folder, it looks for a match for the user's input. This input node contains the main question, or primary variation, a user might ask. The additional item nodes are variations of the main question. Some of the variations use wildcards. For more information about wildcards, see [List of wildcards](/docs/services/dialog/nodes.html#layout_input).

    ```xml
    <folder label="Library">
      <folder label="Live Content" id="folder_2449611">
        <input>
          <grammar>
            <item>What type of toppings do you have?</item>
            <item>$ What type of toppings do you have?</item>
            <item>$ list of toppings</item>
            <item>What * toppings * have</item>
            <item>$ list toppings * available</item>
            <item>$ what toppings do you have</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>We have Pepperoni, Mushrooms, and Sausage</item>
            </prompt>
          </output>
        </input>
      </folder>
    </folder>
    ```
    {: codeblock}

### What to do next
{: #tutorial_basicsetup__basicsetup_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML, such as `What type of toppings do you have?`, to see the system's response.

## Create a simple conversation and a concept
{: #tutorial_multiturn}

In this task, create a multi-turn conversation with users that feels natural and a concept to simplify the process of writing variations.

### Before you begin
{: #tutorial_multiturn__multiturn_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_2_end.xml" download="Exercise_2_end.xml">Exercise 2 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### About this task
{: #tutorial_multiturn__multiturn_about}

The conversation that you create in this section is known as a **multi-turn** conversation because it contains multiple input and output nodes. In the context of the {{site.data.keyword.dialogshort}} service , a **concept** is a list of equivalent words or phrases that can make it easier to create flexible dialogs that minimize repeated text.

### Procedure

1.  Review the following information to understand how to create a multi-turn conversation.

    See lines 40 - 116 in the `Exercise_2_end.xml` file to understand where the user asks what Mike's Pizza sells. Rather than list every item, the system asks the user to clarify which part of the meal they want to know about. Then, the conversation can go in different directions. The user's initial question did not have enough context, so a conversation is created to give the user simplified information. Here is the beginning of the conversation:

    ```xml
    <input>
      <grammar>
        <item>What do you sell?</item>
      </grammar>
      <output>
        <prompt selectionType="RANDOM">
          <item>Are you looking for appetizers, entrees, or drinks?</item>
        </prompt>
        <input>
          <grammar>
            <item>drinks</item>
            <item>beverages</item>
            <item>liquid</item>
            <item>libation</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>
                We have
                Coke,
                Sprite,
                Sunkist,
                Root Beer,
                Ginger Ale,
                Fresca,
                Mello Yello,
                Grape,
                Dr Pepper,
                Monster,
                Moxie Energy,
                and Bottled Spring water
              </item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>entrees</item>
            <item>meals</item>
            <item>main course</item>
            <item>food</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>
                We have Chicken Parm,
                Chicken Cutlet and Marinara Sauce,
                Veal Parm,
                Eggplant Parm,
                Eggplant and Marinara Sauce,
                Meatball, Marinara Sauce and Meatball,
                Chicken & Broccoli,
                Chicken Kabob, Alfredo Sauce and Broccoli,
                Steak & Broccoli, and
                Alfredo Sauce and Broccoli.
              </item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>appetizers</item>
            <item>snacks</item>
            <item>finger food</item>
            <item>appertif</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>
                Chose from Fried Calamari, Mozarella Sticks,
                Stuffed potato skins, Jalepeno Poppers or Stuffed
                Mushrooms
              </item>
            </prompt>
          </output>
        </input>
      </output>
    </input>
    <input>
      <grammar>
        <item>What type of pizza do you sell?</item>
      </grammar>
    </input>
    ```
    {: codeblock}

1.  Re-create lines 39 - 115 in your XML file. Use wildcards in the variations.
1.  Review the following information to understand what concepts are and how they are used.

    Concepts are used to expand user inputs and are active no matter where they are placed in the account. Concepts are usually stored in a separate folder so they are easy to navigate to and do not take up space within specific business processes. .

    The following code from the Exercise 2 file shows the concept for the word "pizza".

    ```xml
    <folder label="Concepts">
      <concept>
        <grammar>
          <item>pizza</item>
          <item>pie</item>
          <item>za</item>
          <item>pizza pie</item>
          <item>slice</item>
        </grammar>
      </concept>
    </folder>
    ```
    {: codeblock}

    You can have a concept that is a single word, essentially a synonym, and is also for a part of a sentence. The following examples are concepts that are parts of a sentence:
    -   I want to
    -   I would like to
    -   Tell me how to

    For more information about concepts, see [concept](/docs/services/dialog/nodes.html#layout_concept).

### What to do next
{: #tutorial_multiturn__multiturn_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML, such as `What do you sell?`, to see the system's response.

## Create profile variables
{: #tutorial_profilevar}

In this task, create the structures for profile variables so that users can naturally go through a decision tree, and the system can capture a user's profile information and display the information to the user.

### Before you begin
{: #tutorial_profilevar__profilevar_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_3_end.xml" download="Exercise_3_end.xml">Exercise 3 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### Procedure

1.  Review the following code to understand how to store user information.

    In this code, a user's postal code can be stored in a profile variable that is called PostalCode, and the type of pizza that the user ordered is stored in a profile variable called PizzaType.

    ```xml
    <variables>
      <var_folder name="Home">
        <var name="PostalCode" type="TEXT" description="The user's postal code"/>
        <var name="PizzaType" type="TEXT" description="What type of pizza the user has ordered"/>
      </var_folder>
    </variables>
    ```
    {: codeblock}

1.  Re-create the PostalCode and PizzaType profile variables in your XML file.
1.  Review the following code to understand how the system asks for information, stores it, and retrieves it later.

    In this code, the system asks the user for a postal code, stores it for later, and tells the user whether delivery is available.

    ```xml
    <input>
      <grammar>
        <item>Do you deliver?</item>
      </grammar>
      <output>
        <prompt>
          <item>Yes we do, what is your postal code?</item>
        </prompt>
        <getUserInput>
          <input>
            <grammar>
              <item>12345</item>
            </grammar>
            <action varName="PostalCode" operator="SET_TO">12345</action>
            <output>
              <prompt>
                <item>Yes, we deliver to your area</item>
              </prompt>
              <goto ref="output_2443126"/>
            </output>
          </input>
        </getUserInput>
      </output>
    </input>
    ```
    {: codeblock}

1.  Re-create the previous code example in your own XML file.
1.  Review the following code to understand how to display stored information for users again.

    Capturing and displaying profile variables is a great way to prove to the user that you understood their inputs and captured them correctly. From here, you can grab the information through the API and pass to your back end system.

    Text in brackets ({}) indicates profile variables. A line break is inserted by `&lt;br&gt;`.

    ```xml
    <output id="output_2443138">
      <prompt>
        <item>
          Here is a summary of your order: &lt;br&gt;
          Pizza: {PizzaType}
          Postal code: {PostalCode}
        </item>
      </prompt>
    </output>
    ```
    {: codeblock}

    For more information about profile variables, see [variables](/docs/services/dialog/nodes.html#layout_variables).

1.  Re-create the previous code example in your own XML file.

### What to do next
{: #tutorial_profilevar__profilevar_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML, such as `Do you deliver?`, to see the system's response.

## Create profile checks
{: #tutorial_profilecheck}

In this task, learn how to use profile checks to steer a user through a personalized conversation based on the information that is gathered through conversation.

### Before you begin
{: #tutorial_profilecheck__profilecheck_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_4_end.xml" download="Exercise_4_end.xml">Exercise 4 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### About this task
{: #tutorial_profilecheck__profilecheck_about}

This task uses the information that was captured in the previous task to give the user a personalized conversation. In that task, a user's postal code and type of pizza were captured. Before the system gives the user an order summary, profile checks are used to ensure that the stored information is acceptable. Using profile checks is a way to create a tailored conversation for users that is different for every user based on which information about them is captured and stored.

### Procedure

1.  Review the following code to understand how the first profile check works.

    This code shows only the beginning of the profile check. To see the entire block of code, look at the `Exercise 4` file.

    ```xml
    <if id="profileCheck_2456241">
      <cond varName="PostalCode" operator="HAS_VALUE"/>
      <if matchType="ANY">
        <cond varName="PostalCode" operator="EQUALS">12345</cond>
        <cond varName="PostalCode" operator="EQUALS">23456</cond>
        <cond varName="PostalCode" operator="EQUALS">34567</cond>
      </if>
    </if>
    ```
    {: codeblock}

    This profile check ensures that the user's postal code matches one of the areas where delivery is available.

1.  Re-create the previous code example in your XML file.
1.  Review the following code to understand how the second profile check works.

    This code shows only the beginning of the profile check. To see the entire block of code, look at the `Exercise 4` file.

    ```xml
    <if>
      <cond varName="PizzaType" operator="HAS_VALUE"/>
    </if>
    ```
    {: codeblock}

    This profile check ensures that a value is stored for the PizzaType variable.

    For more information about profile checks, see [if](/docs/services/dialog/nodes.html#layout_if).

1.  Re-create the previous code example in your XML file.

### What to do next
{: #tutorial_profilecheck__profilecheck_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML that guides you through the process of ordering a specific type of pizza and providing a postal code.

## Create a constant
{: #tutorial_createtag}

In this task, create a constant to simplify the creation process when you have items that might need to be changed later.

### Before you begin
{: #tutorial_createtag__createtag_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_5_end.xml" download="Exercise_5_end.xml">Exercise 5 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### About this task
{: #tutorial_createtag__createtag_about}

Consider a scenario in which you have a product name that you want to reuse over and over again in your conversations, but the name might change soon. Use constants so that you need to update only the name in a single place to change it throughout the rest of the dialog.

Constants are useful for storing long URLs, phone numbers, and other types on information that are inconvenient to retype in multiple places in the dialog.

For simplicity's sake, consider using short names without special characters and grouping similar constants by using prefixes, such as user_name and user_age.

### Procedure

1.  Review the following code to understand how constants are defined.

    ```xml
    <constants>
      <var_folder name="Home">
        <var_folder name="General" type="CONST"/>
        <var name="Meat_Pizza" type="TAG"
          description="The name of the meat pizza">Meat Lover's</var>
      </var_folder>
    </constants>
    ```
    {: codeblock}

    For more information about tags, see the [constants](/docs/services/dialog/constants.html) element.

1.  Re-create the previous code in your XML file, and add the rest of the nodes and the changes that are specific to the `Exercise_5_end.xml` file.

### What to do next
{: #tutorial_createtag__createtag_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML that calls the Meat_Pizza constant in the system's output.

## Create an entity
{: #tutorial_entities}

In this task, create an entity to match a wide range of information,

### Before you begin
{: #tutorial_entities__entities_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_6_end.xml" download="Exercise_6_end.xml">Exercise 6 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### About this task
{: #tutorial_entities__entities_about}

By using entities, the system can understand a specific type in a category. In the following procedure, you create an entity for pizza toppings, and each value is a specific topping. When the user asks for a topping during the conversation, the system captures it by using the entity instead of you writing a variation for each individual topping in an input node.

### Procedure

1.  Review the following code to understand how entities are defined.

    ```xml
    <entity name="Toppings">
      <value name="Pepperoni" value="Pepperoni"/>
      <value name="Mushrooms" value="Mushrooms"/>
      <value name="Sausage" value="Sausage"/>
      <value name="Onions" value="Onions"/>
      <value name="Peppers" value="Peppers"/>
      <value name="Anchovy" value="Anchovy"/>
      <value name="Pineapple" value="Pineapple"/>
      <value name="Chicken" value="Chicken"/>
      <value name="Broccoli" value="Broccoli"/>
      <value name="Pesto" value="Pesto"/>
      <value name="Shrimp" value="Shrimp"/>
      <value name="Garlic" value="Garlic"/>
      <value name="Olives" value="Olives"/>
    </entity>
    ```
    {: codeblock}

    Each entity value requires the name and value attributes. You can specify the same value for both of these attributes, as shown in the code, or specify different values, if you want to store a code for the value of the entity. For example, pepperoni might relate to a value of XX in another system, so you might use that value here to recall it later with any value you like.

1.  Re-create the entity in your XML file.
1.  Review the following code to understand how to use an entity to match to user input.

    Specify an entity in parentheses.

    ```xml
    <grammar>
      <item>Do you have (Toppings)?</item>
    </grammar>
    ```
    {: codeblock}

    This single input node matches user input, such as "Do you have Pepperoni?" or "Do you have mushrooms?", for all entity values. After a user asks for a topping, the system can use *(Entity)={ProfileVariable}* to capture that entity as a variable in an XML string as needed.

    When you store an entity as a profile variable, you receive an XML string that needs to be broken down if you want to display it back to the user. You can recall a specific piece of the string by setting your profile variable to either *{ProfVar.value:main}* or *{ProfVar.value:name}*, where *ProfVar* is your specific variable name, and `value:main` stores it as the value in your entity list, and value:name stores it as the name in your variable list. You can store an entity as a profile variable after any output node, including an empty one directly after it to simplify the debugging process.

    You can use entities for regular expressions, such as ! \d{5}, which captures any five-digit input, such as a postal code.

    For more information about entities, see [entities](/docs/services/dialog/nodes.html#layout_entities).

1.  Re-create the input node that uses the entity in your XML file.

### What to do next
{: #tutorial_entities__entities_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML that calls the entity in the system's output.

## Create layers of profile checks
{: #tutorial_advprofcheck}

In this task, create layers of profile checks to ensure the accuracy of stored information.

### Before you begin
{: #tutorial_advprofcheck__advprofcheck_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_7_end.xml" download="Exercise_7_end.xml">Exercise 7 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

The following procedure requires you to understand how profile checks work and how to create them. To refresh your memory about profile checks, refer to the [the basic profile check](#tutorial_profilecheck) you previously created, or see [the if element](/docs/services/dialog/nodes.html#layout_if).

### About this task
{: #tutorial_advprofcheck__advprofcheck_about}

Layers of profile checks are useful for building a specific user profile. Consider an application scenario in which you seek a person of a specific age, sex, and medical history. To ensure that you have the correct type of person, you would need to check the profile variables in multiple layers.

Now, consider the scenario in which users are ordering pizza. To ensure that they don't specify the same toppings multiple times, you need complex layers of profile checks.

### Procedure

1.  Review lines 289 - 356 in the `Exercise_7_end.xml` file.

    The code block is not duplicated here only because it's long.

    This code checks whether any of the Topping profile variables conflict with each other. If any profile variables conflict, the system prompts users to retry their order. Otherwise, the system begins the check-out process.

1.  Re-create these layers of profile checks in your XML file, and ensure that you create a profile variable for Topping1 - Topping4. For a reminder about how to create profile variables, see [Create profile variables](#tutorial_profilevar).

### What to do next
{: #tutorial_advprofcheck__advprofcheck_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML that calls the entity in the system's output.

## Match regular expressions to user input
{: #tutorial_regex}

In this task, use regular expressions to match to various types of user input.

### Before you begin
{: #tutorial_regex__regex_prereq}

Download and open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/Exercise_8_end.xml" download="Exercise_8_end.xml">Exercise 8 <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> as an example of a dialog that is successfully created by completing the following procedure.

### About this task
{: #tutorial_regex__regex_about}

To complete a pizza order, users need to provide a phone number. You can use regular expressions to capture phone numbers in different formats.

### Procedure

1.  Review the following code to understand how regular expressions are specified.

    ```xml
    <grammar>
      <item>My number is</item>
      <item>! \d{10}</item>
      <item>! \d{3}-\d{3}-\d{4}</item>
      <item>! \d{3}.\d{3}.\d{4}</item>
      <item>! \d{3} \d{3} \d{4}</item>
      <item>! \d{3} \d{7}</item>
    </grammar>
    ```
    {: codeblock}

    These regular expressions match different variations of 10 digits, as shown in the following examples:
    -   The expression ! \d{10} matches 10 digits without spaces in between them.
    -   The expression \d{3}-\d{3}-\d{4} matches 10 digits that are separated by dashes.
    -   The expression \d{3}.\d{3}.\d{4} matches 10 digits that are separated by periods.

    To specify a regular expression, type an exclamation point (!) before the regular expression.

    You can use regular expressions is to reformat user inputs. You can't predict in which format users might give their phone numbers, but you can reform their input from different variations and reformat it into the standard form that you prefer.

1.  Re-create the previous code in your XML file.
1.  Review the following code to understand how to use regular expressions to reformat user input.

    This code shows only a portion of the code the function and script elements that are used for reformatting input. To see the entire block of code, look at the `Exercise 8` file.

    ```xml
    <function>
      <script name="Calculate">
        Name=Calculate
        Line= "{Phone_Number}".replace(/-/g, "").replace("(", "").replace(")", "").replace(/ /g, "")
      </script>
      <output>
        <prompt/>
        <action
          varName="Phone_Number" operator="SET_TO">{MCT:CUSTOM:Calculate:value}
        </action>
      <output>
    </function>
    ```
    {: codeblock}

    You can't predict in which format users might give their phone numbers, but you can reform their input from different variations and reformat it into the standard form that you prefer.

    In this code example, all punctuation in user input for a phone number is removed so that the input is reformatted into an unbroken string of 7 digits. The function nodes add parentheses and dashes to the string.

    After the function nodes add the punctuation for your standard format, an empty output node stores the new version of the variable. Use empty output nodes to manipulate variables without displaying system activity to users.

1.  Re-create the previous code example in your XML file, and add the rest of the nodes that are specific to the `Exercise_8_end.xml` file.

### What to do next
{: #tutorial_regex__regex_next}

Test your XML file by uploading it to the {{site.data.keyword.dialogshort}} tool, and submit the input text from the XML that calls the regular expressions to match phone numbers that are specified in various formats.
