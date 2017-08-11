---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-09"

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

# dictionary
{: #dictionary}

The `<dictionary>` node contains a new word for the spellchecker.
{: shortdesc}

## Example

```xml
<dictionaries>
  <dictionary>
    zonal
    zonally
    zone
    zoned
    zonely
    zoner
    zones
    zoning
    zoo
    zoo's
    zoological
    zoologically
    zoom
    zoomed
    zooming
    zooms
    zoos
  </dictionary>
</dictionaries>
```
{: codeblock}

## Contained by

[dictionaries](/docs/services/dialog/dictionaries.html)

## Contains

None

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
name
</p></td>
<td><p>
The name of the dictionary.
</p></td>
</tr>
</tbody>
</table>
