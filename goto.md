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

# goto
{: #goto}

The `<goto>` node directs the system to other dialog nodes, often because other output applies to more than one input.
{: shortdesc}

## Example

```xml
<input>
  <grammar>
    <item>Do you provide insurance?</item>
  </grammar>
  <goto ref="insurance_provided"></goto>
</input>
```
{: codeblock}

## Contained by

[default](/docs/services/dialog/default.html) | [folder](/docs/services/dialog/folder.html) | [function](/docs/services/dialog/function.html) | [getUserInput](/docs/services/dialog/getUserInput.html) | goto | [if](/docs/services/dialog/if.html) | [input](/docs/services/dialog/input.html) | [output](/docs/services/dialog/output.html) | [random](/docs/services/dialog/random.html) | [search](/docs/services/dialog/search.html)

## Contains

[action](/docs/services/dialog/action.html) | [default](/docs/services/dialog/default.html) | [folder](/docs/services/dialog/folder.html) | [function](/docs/services/dialog/function.html) | [getUserInput](/docs/services/dialog/getUserInput.html) | goto | [if](/docs/services/dialog/if.html) | [input](/docs/services/dialog/input.html) | [output](/docs/services/dialog/output.html) | [random](/docs/services/dialog/random.html) | [search](/docs/services/dialog/search.html)

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
ref
</p></td>
<td><p>
Specifies a reference point that
matches the value of the id attribute for a node.
</p></td>
</tr>
</tbody>
</table>
