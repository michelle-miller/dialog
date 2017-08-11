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

# Nodes
{: #layout_nodes}

The following information describes the most commonly used dialog nodes.
{: shortdesc}

## action
{: #layout_action}

The action node uses profile rules to set values for profile variables.

Use the varName attribute to specify the profile variable, and use the operator attribute to set values. The default setting is DO_NOTHING_STR, which means that profile variable remains as-is when the node is processed by the system.

Only the most recent value is stored for each profile variable. Outside systems to load a user's profile at the beginning of a conversation can be called to begin with specific context.

Profile variables are stored as part of the conversation history. They last as long as the conversation.

The following code shows an example of an action node with an operator attribute value that sets the value of the AreaCode profile variable to 615.

```xml
<action varName="AreaCode" operator="SET_TO">
  615
</action>
```
{: codeblock}

## concept
{: #layout_concept}

Concept nodes group concepts in lists.

A concept node is used by the {{site.data.keyword.dialogshort}} service to replace a specific word with the words in the list. All concept nodes are stored in the Concepts folder.

For example, the word bot is a concept. It is the concept of a virtual agent. In this scenario, you might create a concept node in the Concepts folder to list all the concepts for the phrase virtual agent.

With this concept in place, submitted questions like "What is a VA?", "What is a Digital Agent?" and "What is a dialogbot?" are matched to the input "What is a {{site.data.keyword.virtualagentshort}}?", and the appropriate response is given because the system uses the concept node to know that the words all mean the same thing. Concepts are used to expand variations for every node on a dialog level. They are all stored in the Concepts folder because they are active in the dialog flow no matter where they are placed. Keeping them in their separate folder simplifies organization.

The following code shows the virtual agent concept.

```xml
<folder label="Concepts">
  <concept>
    <grammar>
      <item>Virtual Agent</item>
      <item>VA</item>
      <item>Digital Agent</item>
      <item>Digital Virtual Agent</item>
      <item>bot</item>
      <item>dialogbot</item>
      <item>cyberbot</item>
    </grammar>
  </concept>
</folder>
```
{: codeblock}

## default
{: #layout_default}

The default node indicates the default actions of the dialog.

Default nodes take precedence over all other nodes, so where you place default nodes is important. For example, a default node above a search node means that the dialog always does the default function and never does a search. A default node is ideal after all searches are run and the dialog does not understand a user's submission. For an example, see the following figure.

```xml
<output>
  <prompt>
    <item>Hi, what is your question?</item>
  </prompt>
  <getUserInput>
    <search ref="about"></search>
    <search ref="library"></search>
    <default>
      <output>
        <prompt>
          <item>I'm sorry. I don't understand your question.</item>
        </prompt>
      </output>
    </default>
  </getUserInput>
</output>
```
{: codeblock}

Default nodes are used mainly to capture input that doesn't have an input node. Default nodes inform users that the system realizes that the user submitted a question or comment, but the submission is outside the dialog's domain of expertise.

## entities
{: #layout_entities}

The entities node is used to capture several variations of user input without you needing to write multiple variations in the input nodes of the dialog.

When an entity is matched, profile variables capture the information.

The following code shows an example of an entity for types of pizza sauce.

```xml
<entity name="Sauce">
  <value name="Tomato Sauce" value="Tomato">
    <grammar>
      <item>gravy</item>
      <item>Red Sauce</item>
    </grammar>
  </value>
  <value name="Alfredo Sauce" value="Alfredo">
    <grammar>
      <item>Cheese</item>
      <item>White</item>
    </grammar>
  </value>
</entity>
```
{: codeblock}

## folder
{: #layout_folder}

The folder node groups similar content.

Folder nodes are the first nodes that you must create for a dialog. They are not shown to the user. They are used only for dialog organization and maintenance and to limit search terms to specific areas of the dialog.

Ensure that your dialog contains the following types of folder nodes:

-   **Main**

    Stores the nodes that are run as soon as a dialog is started. Usually this folder contains a welcome message, followed by an opportunity for the user to enter data to begin a conversation. The main folder can store different functions beyond simple welcome messages, such as search, function calls, and more.
-   **Library**

    Stores the core information that is used by the dialog. It stores all the dialog structures, the pairs of input nodes and output nodes, and various other nodes that are used to run a dialog. This folder can also be used to store information that has yet to be approved by the customer for use in a dialog and for other dialog structures you might need to test later.
-   **Global**

    Stores any nodes/functions you want run every time that the dialog must do a function. A search node searches this folder first.
-   **Concepts**

    Stores all the local concepts that are used by a dialog. Store only concept nodes in this folder.

The following code shows these folder nodes in XML format:

```xml
<flow>
  <folder label="Main"></folder>
  <folder label="Library"></folder>
  <folder label="Global"></folder>
  <folder label="Concepts"></folder>
</flow>
```
{: codeblock}

Consider a scenario for designing a dialog for a system that can answer questions about virtual agents. In this scenario, you might create a new folder as a child of the Library folder, and specify "About {{site.data.keyword.virtualagentshort}}s" for the label attribute, as shown in the following code. You would use this folder to store all the dialog nodes that refer to ordering pizzas.

```xml
<folder label="Library">
  <folder label="About Virtual Agents"></folder>
</folder>
```
{: codeblock}

## getUserInput
{: #layout_getuserinput}

The getUserInput node enables users to communicate with the {{site.data.keyword.dialogshort}} service.

This node receives the input that is submitted by the user. The getUserInput node causes the {{site.data.keyword.dialogshort}} service to wait for a response from the end user, and {{site.data.keyword.dialogshort}} service does not respond until the user submits some text into the dialog window.

The getUserInput node is different from the input node. While the input node is used as a matching criteria, the getUserInput node is used to get information from the user. It is always specified after the initial welcome message. For example, a welcome message that says, "Hi, what is your question?" is followed by a getUserInput node, as shown in the following code:

```xml
<output>
  <prompt>
    <item>Hi, what is your question?</item>
  </prompt>
  <getUserInput></getUserInput>
</output>
```
{: codeblock}

Consider using text that is 150 characters or less. Otherwise, the system processes the input slowly.

## goto
{: #layout_goto}

The goto node directs the system to go to a specific part of the folder tree or to a specific output node.

Consider the following example. If a user asks "Is {{site.data.keyword.watson}} a {{site.data.keyword.virtualagentshort}}?", an input node must be created to match the question. In this example, you want your response to be the same response that matches the question "What is a dialog?". If you had to use only input nodes, you would copy and paste the original answer into an output node for this new input node. However, this solution creates a maintenance problem. If the answer changes in the original output, and six or seven input nodes use the same output, the maintenance that is required to ensure they all have the same response increases. Maintenance increases especially if the nodes are scattered throughout the dialog.

A better solution is the goto node. Goto nodes tell the {{site.data.keyword.dialogshort}} service to go to the output node and do the function. In this case, the function is to provide output to the user. By pointing the dialog to the original output response, you need to maintain only the content for one output node instead of multiple outputs that have the same text response. The following code shows how the goto node works

```xml
<input>
  <grammar>
    <item>What is a virtual agent?</item>
    <item>What * virtual agent?</item>
    <item>$ what is a virtual agent?</item>
    <item>$ tell me * virtual agent</item>
  </grammar>
  <output id="va_definition">
    <prompt>
      <item>
        A virtual agent is an automated system that can
        be used to increase customer satisfaction.
      </item>
    </prompt>
  </output>
</input>
<input>
  <grammar>
    <item>Is Watson a virtual agent?</item>
  </grammar>
  <goto ref="va_definition"></goto>
</input>
```
{: codeblock}

## if
{: #layout_if}

The if node checks whether a specific event or requirement is met.

This check is called a profile check, and it uses profile variables to determine the next step that the system takes.

For example, if you want the system to check whether a person previously asked, "What is a {{site.data.keyword.virtualagentshort}}?", create a profile check to see whether the user received the normal response to the question. If they received the normal response, you can provide some other piece of information.

Profile checks are used to determine the number of deflections to a call center and the number of sales queries, and to track topics that users discuss. They are also used to give different responses based on a user's profile, such as age, gender, or location.

If the profile check is true, the system continues to process the child nodes. If the profile check is false, the system moves on to the next step. In this case, if a user asks, "What is a virtual agent?", the system displays "As I mentioned before ..." If the profile check is false, the system displays "A {{site.data.keyword.virtualagentshort}} is an automated ..."

The following code shows this example:

```xml
<input>
  <grammar>
    <item>What is a virtual agent?</item>
  </grammar>
  <if>
    <cond varName="Already Answered" operator="EQUALS">
      Yes
    </cond>
  </if>
  <output>
    <prompt>
      <item>
        As I mentioned before, a virtual agent is an automated system
        that can answer questions and help you solve problems.
      </item>
    </prompt>
  </output>
</input>
```
{: codeblock}

Multiple profile checks can occur in a single profile check node, and they can be set to require any checks to be true or all checks to be true.

## input
{: #layout_input}

The input node matches the input, or the question, that users submit during a conversation with the system.

Consider the virtual agent scenario. When users submit the question "What is a {{site.data.keyword.virtualagentshort}}?", the dialog must have an input node that has a child grammar node, and the grammar node must have a child item node. The item node contains the text, "What is a virtual agent." The content of the first item node is the primary variation. The additional item nodes contain permutations of the primary variation, and they are called variations. Instead of writing complete words in variations, use wildcards. The following code shows an example of an input node that contains variations that use wildcards.

```xml
<folder label="Library">
  <folder label="Live Content" id="Live Content">
    <input>
      <grammar>
        <item>What is a virtual agent?</item>
        <item>$ What is a virtual agent?</item>
        <item>$ Tell me * virtual agent</item>
      </grammar>
    </input>
  </folder>
</folder>
```
{: codeblock}

You can use the following wildcard characters:

-   **Asterisk (*)**

    Replaces a word or set of words in the position the * occupies.

    For example, "What is * dialog" matches the following variations:
    -   "What is a dialog"
    -   "What is this thing called a dialog"
    -   "What is the meaning of a dialog"
    -   And so on

    The asterisk tells the system that the number of words between "is" and "{{site.data.keyword.dialogshort}}" do not matter. Users need to type only the sentence that begins with "what is" and ends with "{{site.data.keyword.dialogshort}}."

    However, if you place an asterisk it does not match to a sentence where there aren't any words in place of the asterisk. For example, "What is dialog" does not match to "What is * dialog". The asterisk is used to indicate that a word, or words, must occupy that space.
-   **Dollar sign ($)**

    Indicates that the phrase after it must appear exactly as it is written, but any words can precede it or follow it.

    For example, "$ is a dialog" matches the following variations:
    -   "So, can you tell me what is a dialog, please"
    -   "I've heard about virtual agents, but is a dialog one of those"
    -   "Tell me, is a dialog something I can create"
    -   "Is a dialog something I can use for my business"
    -   And so on

    Each example has the exact phrase "is a dialog" in it. If the phrase doesn't appear in the user's text exactly as it was written after the dollar sign, a match is not made.
    {: tip}

    Always use correct grammar, spelling, and punctuation in the primary version because it can be shown to the user during Auto-learn, and being correct looks professional.

-   **Combinations of wildcards**

    You can use both wildcards together too. For example, the variation "$ what is * {{site.data.keyword.dialogshort}}" matches a greater variety of user text to the input. However, be careful when you use wildcards, especially the asterisk, because users can ask questions that might be different from the meaning of the specific input. For example, "$ what is * dialog" can also match to the question "So what is a dialog, can I use it to cheat on an exam".

If no input nodes match the question that is submitted by the user, the system usually does not respond.

Input strings are represented by Java strings. The maximum length of a Java string is 2\*\*31 - 1.

## output
{: #layout_output}

The output node displays information from the system to the user. Output nodes are the messages that the system returns to a user's input.

They contain the messages that the system returns to a user's input. The output node is a child of the input node. The output node contains a child prompt node, and the prompt node contains a child item node that contains the text for the system's response. In the scenario, the output node might include this text, "A virtual agent is an automated system that can be used to increase customer satisfaction." The following code shows examples of the input and output nodes:

```xml
<input>
  <grammar>
    <item>What is a virtual agent?</item>
    <item>What * virtual agent?</item>
    <item>$ what is a virtual agent?</item>
    <item>$ tell me * virtual agent</item>
  </grammar>
  <output>
    <prompt>
      <item>
        A virtual agent is an automated system that can
        be used to increase customer satisfaction.
      </item>
    </prompt>
  </output>
</input>
```
{: codeblock}

The output node can contain multiple item nodes. When multiple item nodes are specified, the system can return slightly different but always accurate responses to the same question. This feature is useful when you use the default node because you can provide other ways to indicate that the system does not understand the question that the user asked.

Additionally, the system can display the various outputs randomly or sequentially by specifying the selectionType attribute on the prompt node. Specifying random for the means that each time that node is processed, the dialog displays a random option from the list of item nodes. Specifying sequential means that each time the output node is processed, the dialog displays the next output item in the list.

When the the random and sequential options are used, the system processes the same nodes while the conversation is kept fresh without sounding robotic.

If only one item is in the list, these options are redundant.

Output strings are represented by Java strings. The maximum length of a Java string is 2\*\*31 - 1.

## search
{: #layout_search}

After a user submits a question or comment in the dialog window, the search node tells the system {{site.data.keyword.dialogshort}} service in which areas to search for a match.

For example, if a user submits, "What is a {{site.data.keyword.virtualagentshort}}?", a search node tells to search in the "About {{site.data.keyword.virtualagentshort}}s" folder to find a match, as shown in the following code. The value of the ref attribute on the search node matches the value of the gid attribute on the folder node to be searched.

```xml
<folder label="Main">
  <output>
    <prompt>
      <item>Hi, what is your question?</item>
    </prompt>
    <getUserInput>
      <search ref="about"></search>
    </getUserInput>
  </output>
</folder>
<folder label="Library">
  <folder label="About Virtual Agents" id="about"></folder>
</folder>
```
{: codeblock}

However, remember the {{site.data.keyword.dialogshort}} service does not need to search each folder to find a match. You can tell the to search the entire library folder for a match to an input node, as shown in the following code. When a folder is searched, all subfolders are searched too.

```xml
<folder label="Main">
  <output>
    <prompt>
      <item>Hi, what is your question?</item>
    </prompt>
    <getUserInput>
      <search ref="about"></search>
      <search ref="library"></search>
    </getUserInput>
  </output>
</folder>
<folder label="Library" id="library">
  <folder label="About Virtual Agents" id="about"></folder>
</folder>
```
{: codeblock}

{{site.data.keyword.dialogshort}} service does its own constant search function in the global folder. When you tell to do a function, such as a search, the system first checks the global folder for any functions it needs to perform first, then it performs the search in the area you specify. If the user submits a question or a comment in the dialog window, the global folder is automatically searched too.

## variables
{: #layout_variables}

The variables node contains profile variables that you create to store information that users provide during conversations.

Profile variables are stored as part of the conversation history. They last as long as the conversation.

The following code shows an example of a profile variable for a type of phone a user intends to buy.

```xml
<variables>
  <var_folder name="Phones">
    <var name="PhoneType" type="TEXT" description="The user's phone preference."></var>
  </var_folder>
</variables>
```
{: codeblock}

Use the following guidelines when you specify the name attribute:

-   The names are case-sensitive.
-   Do not include spaces. Use either a single word without spaces, such as PhoneType, or words that are separated by underscores, such as Phone_Type.
