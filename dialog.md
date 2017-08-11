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

# dialog
{: #dialog}

The `<dialog>` node defines a top-level container for the dialog that you design.
{: shortdesc}

## Example

```xml
<dialog xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:noNamespaceSchemaLocation="DialogDocFormat_v0.8_manual.xsd">
  <flow>
    <folder label="Main"></folder>
    <folder label="Library"></folder>
  </flow>
  <entities></entities>
  <constants></constants>
  <variables></variables>
</dialog>
```
{: codeblock}

## Contained by

None

## Contains

[flow](/docs/services/dialog/flow.html) | [entities](/docs/services/dialog/entities.html) | [settings](/docs/services/dialog/settings.html) | [variables](/docs/services/dialog/variables.html)

## Attributes

None
