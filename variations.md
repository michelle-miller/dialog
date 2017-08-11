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

# variations
{: #variations}

The `<variations>` node stores different prompts for the DNR Join Statement and AutoLearn Statement special settings.
{: shortdesc}

## Example

```xml
<specialSettings>
  <specialSetting label="DNR Join Statement" selectionType="RANDOM">
    <variations>
      <item>And here comes the DNR!</item>
      <item>DNR triggers.</item>
      <item>And now for something completely different.</item>
    </variations>
  </specialSetting>
  <specialSetting label="AutoLearn Statement" selectionType="RANDOM">
    <variations>
      <item>Did you mean?</item>
      <item>I am not sure. This could be it:</item>
      <item>I am confused. Is it one of these?</item>
    </variations>
  </specialSetting>
</specialSettings>
```
{: codeblock}

## Contained by

[specialSetting](/docs/services/dialog/specialSetting.html)

## Contains

[item](/docs/services/dialog/item.html)

## Attributes

None
