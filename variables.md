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

# variables
{: #variables}

The `<variables>` node contains profile variables.
{: shortdesc}

## Example

```xml
<variables>
  <var_folder name="Home">
    <var_folder name="Phones" type="VAR">
      <var name="Color" type="TEXT" description="Phone color preference"/>
      <var name="Storage" type="TEXT" description="Storage size preference"/>
      <var name="Carrier" type="TEXT" description="Carrier preference"/>
    </var_folder>
  </var_folder>
</variables>
```
{: codeblock}

## Contained by

[dialog](/docs/services/dialog/dialog.html)

## Contains

[var_folder](/docs/services/dialog/var_folder.html)

## Attributes

None
