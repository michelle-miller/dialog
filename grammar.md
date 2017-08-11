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

# grammar
{: #grammar}

The `<grammar>` node contains lists of `<item>` elements that are used to match to user input.
{: shortdesc}

## Example

```xml
<grammar>
  <item>phone</item>
  <item>cell</item>
  <item>cell phone</item>
  <item>cellular phone</item>
</grammar>
```
{: codeblock}

## Contained by

[concept](/docs/services/dialog/concept.html) | [input](/docs/services/dialog/input.html)

## Contains

[item](/docs/services/dialog/item.html)

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>
type
</p></td>
<td><p>
Specifies the grammar type. The following
values are valid:
</p><dl><dt>VARIATIONS</dt>
<dd><p>Basic dialog grammars. This value is the default.</p></dd>
</dl>
</td>
</tr>
</tbody>
</table>
