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

# entities
{: #entities}

The `<entities>` node contains one or more entity nodes.
{: shortdesc}

## Example

```xml
<entities>
  <entity name="VIRTUAL_AGENTS">
    <value name="Watson" value="Watson" />
    <value name="Siri" value="Siri" />
    <value name="Cortana" value="Cortana" />
    <value name="Google Now" value="Google Now" />
    <value name="HAL" value="HAL" />
    <value name="Glados" value="Glados" />
    <value name="Skynet" value="Skynet" />
    <value name="Agent Smith" value="Agent Smith" />
  </entity>
</entities>
```
{: codeblock}

## Contained by

[dialog](/docs/services/dialog/dialog.html)

## Contains

[entity](/docs/services/dialog/entity.html)

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
<tr><td><p>name</p></td>
<td><p>Specifies the name of the group of entities.</p></td>
</tr>
</tbody>
</table>
