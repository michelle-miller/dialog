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

# translationSet
{: #translationSet}

The `<translations>` node defines translations on new lines. It functions the same as the `<translation>` node, but it uses a delimiter to define the translation on a new line while the `<translation>` node uses a `<src>` and a `<tgt>` node for each translation.
{: shortdesc}

## Example

```xml
<translations>
  <translationSet>
    ^^ ~ smile
    ^_^ ~ smile
    - ~ subtract
    ; - ) ~ wink
    ; ) ~ wink
    ;_; ~ sad
    ;-) ~ wink
    ;-)) ~ wink
    ;-))) ~ wink
    ;-p ~ stick out tongue
    ;) ~ wink
    ;)) ~ wink
    ;))) ~ wink
    ;o) ~ wink
    ;op ~ stick out tongue
    ;opp ~ stick out tongue
    ;oppp ~ stick out tongue
    ;p ~ stick out tongue
    : ( ~ sad
    : ) ~ smile
    : ] ~ smile
    : d ~ smile
    : o ~ surprise
    : p ~ stick out tongue
    :-( ~ sad
    :-(( ~ sad
    :-((( ~ sad
    :-) ~ smile
    :-)) ~ smile
    :-))) ~ smile
    :-d ~ smile
    :-dd ~ smile
    :-ddd ~ smile
    :-o ~ surprise
  </translationSet>
</translations>
```
{: codeblock}

In translation sets, the tilde (~) means "translates to." New lines are delimiters between translations. The language packs contain many language-specific predefined translations in their definitions.

### Contained by

[dialog](/docs/services/dialog/dialog.html)

### Contains

[translation](/docs/services/dialog/translation.html) | [translationSet](/docs/services/dialog/translationSet.html)

### Attributes

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
The name of the translation set.
</p></td>
</tr>
</tbody>
</table>
