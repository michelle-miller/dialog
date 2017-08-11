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

# cond
{: #cond}

The `<cond>` node sets a condition for a profile check.
{: shortdesc}

## Example

```xml
<if>
  <cond varName="Topic" operator="Equals">Order Placed</cond>
</if>
```
{: codeblock}

## Contained by

[if](/docs/services/dialog/if.html)

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
Specifies the setting of profile variables. The following
                                    values are valid:
</p><dl><dt>EQUALS</dt>
<dd><p>Checks whether the text of the variable at the varName
                                            attribute matches the node value or text.</p></dd>
<dt>CONTAINS</dt>
<dd><p>Checks whether the text of the variable at the varName
                                            attribute contains the node text.</p></dd>
<dt>MATCHES_PATTERN</dt>
<dd><p>Checks whether the text of the variable at the varName
                                            attribute matches the regular expression in the node
                                            text.</p></dd>
<dt>LESS_THEN</dt>
<dd><p>Checks whether the value of the variable at the varName
                                            attribute is less than the node value.</p></dd>
<dt>GREATER_THEN</dt>
<dd><p>Checks whether the value of the variable at the varName
                                            attribute is greater than the node value.</p></dd>
<dt>EQUAL_TO_YES</dt>
<dd><p>Checks whether the variable at the varName attribute
                                            contains Yes.</p></dd>
<dt>EQUAL_TO_NO</dt>
<dd><p>Checks whether the variable at the varName attribute
                                            contains No.</p></dd>
<dt>IS_BLANK</dt>
<dd><p>Checks whether the variable at the varName attribute is
                                            empty.</p></dd>
<dt>HAS_VALUE</dt>
<dd><p>Checks whether the variable at the varName attribute is
                                            not empty.</p></dd>
<dt>SET_TO</dt>
<dd><p>SET_TO is a legacy value. Do not use it.</p></dd>
<dt>SET_TO_BLANK</dt>
<dd><p>SET_TO_BLANK is a legacy value. Do not use it.</p></dd>
</dl>
</td>
</tr>
<tr><td><p>
varName
</p></td>
<td><p>
The name of the conditional variable.
</p></td>
</tr>
</tbody>
</table>
