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

# stopwordSet
{: #stopwordSet}

The `<stopwordSet>` node contains a set of defined stopwords that have a low matching score, which means they have little to no effect on whether the user-submitted input matches an input node.
{: shortdesc}

## Example

```xml
<stopwords>
  <stopwordSet>
    after
    afterward
    against
  </stopwordSet>
  <stopwordSet>
    also
    although
    always
  </stopwordSet>
</stopwords>
```
{: codeblock}

Stopwords in user input and input nodes are basically ignored.

You can define multiple stopword sets, but usually only one is necessary. New lines are delimiters between stopwords.

## Contained by

[stopwords](/docs/services/dialog/stopwords.html)

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
The name of the stopword set.
</p></td>
</tr>
</tbody>
</table>
