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

# folder
{: #folder}

The `<folder>` node groups content.
{: shortdesc}

## Example

```xml
<folder label="Library">
  <folder label="About"></folder>
  <folder label="Use"></folder>
</folder>
```
{: codeblock}

## Contained by

[default](/docs/services/dialog/default.html) | [flow](/docs/services/dialog/flow.html) | folder | [function](/docs/services/dialog/function.html) | [getUserInput](/docs/services/dialog/getUserInput.html) | [goto](/docs/services/dialog/goto.html) | [if](/docs/services/dialog/if.html) | [input](/docs/services/dialog/input.html) | [output](/docs/services/dialog/output.html) | [random](/docs/services/dialog/random.html) | [search](/docs/services/dialog/search.html)

## Contains

[action](/docs/services/dialog/action.html) | [concept](/docs/services/dialog/concept.html) | [default](/docs/services/dialog/default.html) | folder | [function](/docs/services/dialog/function.html) | [getUserInput](/docs/services/dialog/getUserInput.html) | [goto](/docs/services/dialog/goto.html) | [if](/docs/services/dialog/if.html) | [input](/docs/services/dialog/input.html) | [output](/docs/services/dialog/output.html) | [random](/docs/services/dialog/random.html) | [search](/docs/services/dialog/search.html)

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>
comment
</p></td>
<td><p>
Specifies comment about the node.
</p></td>
</tr>
<tr><td><p>
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
isOffline
</p></td>
<td><p>
Specifies whether the node is processed
or ignored by the system. Valid values are true and false.
</p></td>
</tr>
<tr><td><p>
label
</p></td>
<td><p>
Specifies a unique name for a node.
</p></td>
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
