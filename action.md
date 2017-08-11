---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-10"

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

# action
{: #action}

The `<action>` node uses profile rules to set values for profile variables.
{: shortdesc}

## Example

```xml
<action varName="PostalCode" operator="SET_TO">
  33801
</action>
```
{: codeblock}

## Contained by

[default](/docs/services/dialog/default.html) | [folder](/docs/services/dialog/folder.html) | [function](/docs/services/dialog/function.html) | [getUserInput](/docs/services/dialog/getUserInput.html) | [goto](/docs/services/dialog/goto.html) | [if](/docs/services/dialog/if.html) | [input](/docs/services/dialog/input.html) | [output](/docs/services/dialog/output.html) | [random](/docs/services/dialog/random.html) | [search](/docs/services/dialog/search.html)

## Contains

None

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<tr><th>Name</th>
<th>Description</th>
</tr>
<tr><td><p>
gid
</p></td>
<td><p>
Specifies the numeric ID for an
object that is used to store data in the database. Internally, GIDs
link together dialog nodes and link conversation history with dialog
nodes. If you specify GIDs, ensure that the values throughout the
dialog document are unique. Otherwise, the dialog document cannot
be imported into the system. The scope of the GID is the dialog ID.
</p></td>
</tr>
<tr><td><p>
operator
</p></td>
<td><p>
Specifies the setting of profile variables. The following values are valid:
</p><dl><dt>DO_NOTHING_STR</dt>
<dd><p>Does not change the value of the target variable.</p></dd>
<dt>SET_TO</dt>
<dd><p>Sets the node text to the target variable that is
                                            specified by the varName attribute.</p></dd>
<dt>SET_TO_USER_INPUT</dt>
<dd><p>Sets the node text to the current user input. The node
                                            that follows it uses the overwritten input.</p></dd>
<dt>SET_TO_USER_INPUT_CORRECTED</dt>
<dd><p>Sets the node text to the current user input after a
                                            spellchecker applies corrections.</p></dd>
<dt>INCREMENT_BY</dt>
<dd><p>Increments the value of the target variable at the
                                            varName attribute by the value that is specified in the
                                            node value.</p></dd>
<dt>DECREMENT_BY</dt>
<dd><p>Decrements the value of the target variable at the
                                            varName attribute by the value specified in the node
                                            value.</p></dd>
<dt>SET_TO_YES</dt>
<dd><p>Sets the target variable at the varName attribute to
                                            YES.</p></dd>
<dt>SET_TO_NO</dt>
<dd><p>Sets the target variable at the varName attribute to
                                            NO.</p></dd>
<dt>YES</dt>
<dd><p>YES is a legacy value. Use SET_TO_YES instead.</p></dd>
<dt>NO</dt>
<dd><p>NO is a legacy value. Use SET_TO_NO instead.</p></dd>
<dt>SET_AS_USER_INPUT</dt>
<dd><p>Sets the current value of the profile variable as the
                                            user input. The user input value equals the value of the
                                            profile variable. This value is the opposite of
                                            SET_TO_USER_INPUT.</p></dd>
<dt>SET_TO_BLANK</dt>
<dd><p>Clears the value of the target variable at the varName
                                            attribute.</p></dd>
<dt>APPEND</dt>
<dd><p>Appends the node value to the end of current string in
                                            the variable that is specified at the varName
                                            attribute.</p></dd>
</dl>
</td>
</tr>
<tr><td><p>
varName
</p></td>
<td><p>
Specifies the name of a variable.
</p></td>
</tr>
</table>
