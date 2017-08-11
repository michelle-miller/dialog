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

# prompt
{: #prompt}

The `<prompt>` node contains a list of item elements.
{: shortdesc}

## Example

```xml
<output>
  <prompt>
    <item>Do you want the new X-Phone 7?</item>
  </prompt>
</output>
```
{: codeblock}

## Contained by

[output](/docs/services/dialog/output.html)

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
selectionType
</p></td>
<td><p>
Specifies the order in which output
text is sent. The following values are valid:
</p><dl><dt>RANDOM</dt>
<dd><p>If an output node contains multiple variations, RANDOM sets the
output node to randomly display one of the variations when the output
node is hit.</p></dd>
<dt>SEQUENTIAL</dt>
<dd><p>If an output node contains multiple variations, SEQUENTIAL sets
the output node to display these variations one by one in the order
of specification when the output node is hit. When the first output
node is hit, the first variation is displayed. When it is hit for
the second time, the second variation is displayed, and so on.</p></dd>
</dl>
</td>
</tr>
<tr><td><p>
type
</p></td>
<td><p>
Specifies the prompt type. This attribute is not supported. The following values
                                    are valid:
</p><dl><dt>VARIATIONS</dt>
<dd><p>This value is not supported. It sets the type to
                                            VARIATIONS, which is standard dialog text output.</p></dd>
<dt>NLG</dt>
<dd><p>This value is not supported. It sets the type to NLG,
                                            which stands for natural language generation.</p></dd>
</dl>
</td>
</tr>
</tbody>
</table>
