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

# var
{: #var}

The `<var>` node contains a variable.
{: shortdesc}

## Example in a constants node

```xml
<var name="Sandwich_Type" type="TAG"
  description="The name of the vegetable sandwich">
    Olive You
</var>
```
{: codeblock}

## Example in a `<variables>` node

```xml
<var name="Terminal_Exchange" type="YESNO" initValue="No" description="Has the system already said goodbye?"/>
```
{: codeblock}

## Contained by

[var_folder](/docs/services/dialog/var_folder.html)

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
initValue
</p></td>
<td><p>
Specifies the initial value of the
node.
</p></td>
</tr>
<tr><td><p>name</p></td>
<td><p>Specifies the name of the variable.</p></td>
</tr>
<tr><td><p>type</p></td>
<td><p>Specifies the variable type. The following values are valid:</p><dl><dt>TEXT</dt>
<dd><p>Specifies that the variable accepts a text string.</p></dd>
<dt>NUMBER</dt>
<dd><p>Specifies that the variable accepts a numeric
                                            value.</p></dd>
<dt>YESNO</dt>
<dd><p>Specifies that the variable accepts either yes or
                                            no.</p></dd>
<dt>DATETIME</dt>
<dd><p>Specifies that the variable accepts a date and time
                                            value.</p></dd>
<dt>TAG</dt>
<dd><p>Specifies that the variable accepts defined tags.</p></dd>
</dl>
</td>
</tr>
</tbody>
</table>
