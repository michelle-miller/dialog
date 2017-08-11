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

# var_folder
{: #var_folder}

The `<var_folder>` node contains profile variable values.
{: shortdesc}

## Example

```xml
<var_folder>
  <var name="Sauce" type="TEXT"
    description="Describes the type of sauce to top a pizza with"/>
</var_folder>
```
{: codeblock}

## Contained by

[constants](/docs/services/dialog/constants.html) | [variables](/docs/services/dialog/variables.html)

## Contains

[var](/docs/services/dialog/var.html)

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
id
</p></td>
<td><p>
Specifies a unique ID that is used
as an anchor point, especially for GoTo nodes and Search nodes.
</p></td>
</tr>
<tr><td><p>name</p></td>
<td><p>Specifies the name of the folder.</p></td>
</tr>
<tr><td><p>type</p></td>
<td><p>Specifies the type of folder. The following values are valid:</p><dl><dt>VAR</dt>
<dd><p>Specifies that the variable can be changed by the action
                                            node during the Dialog session. VAR is the default
                                            value.</p></dd>
<dt>CONST</dt>
<dd><p>Specifies that the variables are defined as constant,
                                            and users cannot overwrite them during the Dialog
                                            session.</p></dd>
</dl>
</td>
</tr>
</tbody>
</table>
