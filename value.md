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

# value
{: #value}

The `<value>` node specifies the name and the value for a variation of the entity.
{: shortdesc}

## Example

```xml
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
```
{: coeblock}

## Contained by

[entity](/docs/services/dialog/entity.html)

## Contains

[concept](/docs/services/dialog/concept.html) | [grammar](/docs/services/dialog/grammar.html)

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>name</p></td>
<td><p>Specifies the name of the value.
If you add this attribute, do not
                                    leave the value of it empty.
</p></td>
</tr>
<tr><td><p>value</p></td>
<td><p>Specifies the value.</p></td>
</tr>
</tbody>
</table>
