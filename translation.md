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

# translation
{: #translation}

The `<translation>` node defines a single translation. It functions the same as the `<translationSet>` node, but it uses a `<src>` and a `<tgt>` node to define each translation while the `<translationSet>` node uses a delimiter to specify each translation on a new line.
{: shortdesc}

## Example

```xml
<translations>
  <translation>
    <src>:)</src>
    <tgt>smile</tgt>
  </translation>
</translations>
```
{: codeblock}

## Contained by

[translations](/docs/services/dialog/translations.html)

## Contains

[src](/docs/services/dialog/src.html) | [tgt](/docs/services/dialog/tgt.html)

## Attributes

None
