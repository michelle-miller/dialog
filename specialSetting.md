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

# specialSetting
{: #specialSetting}

The `<specialSetting>` node controls settings for the DNR join statement and the AutoLearn statement.
{: shortdesc}

## Example

```xml
<specialSettings>
  <specialSetting label="AutoLearn Statement" selectionType="RANDOM">
    <variations>
      <item>Did you mean?</item>
    </variations>
  </specialSetting>
</specialSettings>
```
{: codeblock}

```xml
<specialSettings>
  <specialSetting label="DNR Join Statement" selectionType="RANDOM">
    <variations>
      <item>This is a return statement.</item>
    </variations>
  </specialSetting>
</specialSettings>
```
{: codeblock}

## Contained by

[specialSettings](/docs/services/dialog/specialSettings.html)

## Contains

[variations](/docs/services/dialog/variations.html)

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>
date
</p></td>
<td><p>
Specifies the date when the node was created.
</p></td>
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
id
</p></td>
<td><p>
Specifies a unique ID that is used
as an anchor point, especially for GoTo nodes and Search nodes.
</p></td>
</tr>
<tr><td><p>
label
</p></td>
<td><p>
Specifies a unique name for a node.

The following
                                    values are valid:
</p><dl><dt>DNR join statement</dt>
<dd><p>Sets the `<output>` node that contains the text to be
                                            displayed when dynamic node resolution (DNR) is on. DNR
                                            returns the dialog to the previous `<getUserInput>`
                                            node.</p></dd>
<dt>AutoLearn statement</dt>
<dd><p>Sets the `<output>` node that contains the text to be
                                            displayed when Auto Learn is on. When Auto Learn is on
                                            and the dialog does gets only some partial matches, it
                                            displays them in a list. The text specified for the
                                            AutoLearn statement is displayed before this list. In
                                            the code example, the text "Did you mean?" would be
                                            displayed before a list of nonidentical matches.</p></dd>
</dl>
</td>
</tr>
<tr><td><p>
selectionType
</p></td>
<td><p>
Specifies the order in which output
text is sent. The following values are valid:
</p><dl><dt>RANDOM</dt>
<dd><p>If an output node contains multiple variations, RANDOM sets the
output node to randomly display one of the variations when the output
node is hit.</p></dd>
<dt>SEQUENTIAL</dt>
<dd><p>If an output node contains multiple variations, SEQUENTIAL sets
the output node to display these variations one by one in the order
of specification when the output node is hit. When the first output
node is hit, the first variation is displayed. When it is hit for
the second time, the second variation is displayed, and so on.</p></dd>
</dl>
</td>
</tr>
</tbody>
</table>
