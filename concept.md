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

# concept
{: #concept}

The `<concept>` node store variations of input as a single word.
{: shortdesc}

## Example

```xml
<concept>
  <grammar>
    <item>Hello</item>
    <item>Hi</item>
    <item>Hola</item>
    <item>Howdy</item>
    <item>Hiya</item>
    <item>Hey</item>
    <item>Heya</item>
    <item>yello</item>
    <item>aloha</item>
  </grammar>
</concept>
```
{: codeblock}

## Contained by

[folder](/docs/services/dialog/folder.html)

## Contains

[grammar](/docs/services/dialog/grammar.html)

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
description
</p></td>
<td><p>
Specifies a description of the node.
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
isOffline
</p></td>
<td><p>
Specifies whether the node is processed
or ignored by the system. Valid values are true and false.
</p></td>
</tr>
</tbody>
</table>
