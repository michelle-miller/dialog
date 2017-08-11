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

# entity
{: #entity}

The `<entity>` node contains an entity and its values.
{: shortdesc}

## Example

```xml
<entities>
  <entity name="currency" entityExample="dollar" entityType="GENERIC">
    <value name="USD" value="USD">
      <grammar>
        <item>dollar </item>
        <item>buck</item>
      </grammar>
    </value>
    <value name="EUR" value="EUR">
      <grammar>
        <item>euro</item>
        <item>eur</item>
        <item>european buck</item>
      </grammar>
    </value>
    <entityRules></entityRules>
  </entity>
</entities>
```
{: codeblock}

## Contained by

[entities](/docs/services/dialog/entities.html)

## Contains

[value](/docs/services/dialog/value.html) | [entityRules](/docs/services/dialog/entityRules.html)

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
entityExample
</p></td>
<td><p>
Specifies a valid value of the defined entity. This value is required
                                    by the Japanese language pack. In languages that are not
                                    delimited by white space, it ensures that text is tokenized
                                    correctly when the entity is extracted.
</p></td>
</tr>
<tr><td><p>
entityType
</p></td>
<td><p>
Specifies the type of entity. The following values are valid:
</p><dl><dt>GENERIC</dt>
<dd><p>Identifies a user-specified entity by specifying all the
                                            possible values of the entity by text variations.</p></dd>
</dl>
</td>
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
<td><p>Specifies the name of the entity.
If you add this attribute, do not leave the
                                    value of it empty.
</p></td>
</tr>
</tbody>
</table>
