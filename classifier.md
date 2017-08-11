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

# classifier
{: #classifier}

The `<classifier>` node enables the dialog to use classifier-based matching of user input in all `<search>` nodes.
{: shortdesc}

## Example

```xml
<classifier policy="SEARCHMODE_CLASSIFIER"
  threshold="0.6" exactMatchFirst="true"
  fuzzyThreshold="0.1">
</classifier>
```
{: codeblock}

## Contained by

[search](/docs/services/dialog/search.html)

## Contains

[customParams](/docs/services/dialog/customParams.html)

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>
exactMatchFirst
</p></td>
<td><p>Specifies whether to use a combination of rules-based matching
                                and classifier matching. When it is enabled, rules-based matching is
                                used first, and if no rule matches, classifier matching is used.
                                Valid values are true and false.</p></td>
</tr>
<tr><td><p>
fuzzyThreshold
</p></td>
<td><p>Specifies the disambiguation threshold. Valid values are 0.0 -
                                1.0.</p></td>
</tr>
<tr><td><p>
policy
</p></td>
<td><p>Specifies the local search mode setting for a search element. The following values are valid:</p><dl><dt>SEARCHMODE_DEFAULT</dt>
<dd><p>Uses the search mode that is specified by the global
                                            settings.</p></dd>
<dt>SEARCHMODE_CLASSIFIER</dt>
<dd><p>Overrides the global setting to use the classifier
                                            search mode.</p></dd>
<dt>SEARCHMODE_VARIATIONS</dt>
<dd><p>Overrides the global setting to use the variations
                                            search mode.</p></dd>
</dl>
</td>
</tr>
<tr><td><p>
threshold
</p></td>
<td><p>Specifies the decision threshold. Valid values are 0.0 -
                                1.0.</p></td>
</tr>
</tbody>
</table>
