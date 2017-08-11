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

# settings
{: #settings}

The `<settings>` node contains the setting preferences for the dialog.
{: shortdesc}

## Example

```xml
<settings>
  <setting name="AUTOLEARN" type="USER">false</setting>
  <setting name="LANGUAGE" type="USER">en-US</setting>
  <setting name="MAXAUTOLEARNITEMS" type="USER">4</setting>
  <setting name="TIMEZONEID" type="USER">Europe/Prague</setting>
  <setting name="INPUTMASKTYPE" type="USER">0</setting>
  <setting name="CONCEPTMATCHING" type="USER">0</setting>
  <setting name="USE_CONCEPTS">3</setting>
  <setting name="AL_NONE_LABEL">None of the above</setting>
  <setting name="DEFAULT_DNR_RETURN_POINT_CANDIDATE">-1</setting>
  <setting name="ENTITIES_SCOPE">3</setting>
  <setting name="MULTISENT">0</setting>
  <setting name="REPORT_SCRIPT_ID">0</setting>
  <setting name="DNR_NODE_ID">-16</setting>
  <setting name="DEFAULT_POINT_NODE_ID">2</setting>
  <setting name="USER_LOGGING">2</setting>
  <setting name="CLS_SEARCH_MODE">0</setting>
  <setting name="CLS_MODEL">0</setting>
  <setting name="CLS_ENDPOINT"></setting>
  <setting name="CLS_USERNAME"></setting>
  <setting name="CLS_PASSWORD"></setting>
  <setting name="CLS_MODELNAME">1CC095x161-nlc-13</setting>
  <setting name="CLS_ADVANCED_SETTINGS">true</setting>
  <setting name="CLS_MAXNBEST">3</setting>
  <setting name="CLS_USE_OFFTOPIC">false</setting>
  <setting name="PLATFORM_VERSION">10.1</setting>
  <setting name="USE_TRANSLATIONS">2</setting>
  <setting name="USE_SPELLING_CORRECTIONS">2</setting>
  <setting name="USE_STOP_WORDS">2</setting>
  <setting name="USE_AUTOMATIC_STOPWORDS_DETECTION">0</setting>
</settings>
```
{: codeblock}

## Contained by

[dialog](/docs/services/dialog/dialog.html)

## Contains

[setting](/docs/services/dialog/setting.html)

## Attributes

None
