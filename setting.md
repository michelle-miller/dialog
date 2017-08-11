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

# setting
{: #setting}

The `<setting>` node contains a preference for the dialog. The settings turn features on and off, determine the dialog's behavior, and set up other settings.
{: shortdesc}

## Example

The following example shows the minimal required settings and their attributes.

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

[settings](/docs/services/dialog/settings.html)

## Contains

None

## Attributes

<table>
<caption>Table 1. Attributes</caption>
<thead><tr><th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>name</p></td>
<td><p>Specifies the name of the setting. The following names and values are valid:</p><dl><dt>AUTOLEARN</dt>
<dd><p>Controls whether the dialog suggests other nodes when the input is not matched to a
particular node. Valid values are true and false. The default value is false. When false is
specified, the dialog does not suggest other nodes when autolearn is not set.</p></dd>
<dt>LANGUAGE</dt>
<dd><p>The account language. The following values are valid:</p><ul><li><p>en-US</p></li>
<li><p>es-ES</p></li>
<li><p>pt-BR</p></li>
</ul>
</dd>
<dt>MAXAUTOLEARNITEMS</dt>
<dd><p>The maximum amount of autolearn items that are displayed
                                            when the AUTOLEARN setting is on and input was not
                                                matched
If you add this attribute, do
                                                not leave the value of it empty.

Valid values are 1 - 10. The default value is
                                                4.
.</p></dd>
<dt>TIMEZONEID</dt>
<dd><p>Sets the time zone.</p></dd>
<dt>INPUTMASKTYPE</dt>
<dd><p>Controls whether to mask user input. When true is specified,  the numeric characters
in conversation history are masked. If you add this attribute, do not leave the value of it empty.
The following values are valid:</p><dl><dt>0</dt>
<dd><p>False. It is the default value.</p></dd>
<dt>1</dt>
<dd><p>True.</p></dd>
</dl>
</dd>
<dt>PARENT_ACCOUNT</dt>
<dd><p>Sets the name of the parent account of an account. The
                                            parent account defines general concepts that can be
                                            reused by other accounts. It is required.</p></dd>
<dt>CONCEPTMATCHING</dt>
<dd><p>Sets the dialog concept matching.
If you
                                                add this attribute, do not leave the value of it
                                                empty.
 The following values are valid:</p><dl><dt>0</dt>
<dd><p>Matching that uses auto select.</p></dd>
<dt>1</dt>
<dd><p>Strict matching.</p></dd>
<dt>2</dt>
<dd><p>Fuzzy matching.</p></dd>
</dl>
</dd>
<dt>USE_CONCEPTS</dt>
<dd><p>Determines whether to use concepts. The following values
                                            are valid:</p><dl><dt>0</dt>
<dd><p>Concepts are not used.</p></dd>
<dt>1</dt>
<dd><p>Only local concepts are used. Local concepts
                                                are concepts that are defined in the current
                                                dialog account.</p></dd>
<dt>2</dt>
<dd><p>Only concepts from the parent account are
                                                used.</p></dd>
<dt>3</dt>
<dd><p>The concepts from both the current account and
                                                the parent account are used. It is the default
                                                value.</p></dd>
</dl>
</dd>
<dt>AL_NONE_LABEL</dt>
<dd><p>Specifies the text that is displayed when the auto learn
                                            dialog feature is triggered.</p></dd>
<dt>DEFAULT_DNR_RETURN_POINT_CANDIDATE</dt>
<dd><p>Sets the default behavior during a check to determine
                                            whether a node is a DNR return point candidate. The
                                            following values are valid:</p><dl><dt>0</dt>
<dd><p>False.</p></dd>
<dt>1</dt>
<dd><p>True. Each node is considered to be a DNR
                                                candidate. It is the default value.</p></dd>
</dl>
                                        </dd>
<dt>ENTITIES_SCOPE</dt>
<dd><p>Controls entities. The following values are valid:</p><dl><dt>0</dt>
<dd><p>Entities for both the system and the local
                                                account are off.</p></dd>
<dt>1</dt>
<dd><p>Only local entities are on.</p></dd>
<dt>2</dt>
<dd><p>Only system entities are on.</p></dd>
<dt>3</dt>
<dd><p>Entities for both the system and the local
                                                account are on.</p></dd>
</dl>
</dd>
<dt>MULTISENT</dt>
<dd><p>Controls multiple-sentence matching. The following
                                            values are valid:</p><dl><dt>0</dt>
<dd><p>Multiple-sentence matching is off. It is the
                                                default value.</p></dd>
<dt>1</dt>
<dd><p>Multiple-sentence matching is on.</p></dd>
<dt>2</dt>
<dd><p>Multiple sentence single answer sub matching
                                                is on.</p></dd>
</dl><p>
:</p></dd>
<dt>REPORT_SCRIPT_ID</dt>
<dd><p>This legacy setting is required. The value is 0.</p></dd>
<dt>DNR_NODE_ID</dt>
<dd><p>Sets the type of node to which the DNR mechanism should
                                            return. The following values are valid:</p><dl><dt>blank</dt>
<dd><p>If a value is not specified, the default
                                                value, -15, is used. DNR returns to the previous
                                                getUserInput node and displays the text of the
                                                nearest output node that precedes the getUserInput
                                                node.</p></dd>
<dt>-16</dt>
<dd><p>DNR only returns to the previous getUserInput
                                                node.</p></dd>
</dl>
<p>If you are unsure about which value to specify,
                                                use the default value so that other DNR settings
                                                will work correctly.</p>
</dd>
<dt>DEFAULT_POINT_NODE_ID</dt>
<dd><p>The ID of the default DNR return point that is used when
                                            the DNR mechanism is triggered. Specify the gid
                                            attribute value of the getUserInput node to which you
                                            want DNR to return.</p></dd>
</dl>
<dl><dt>USER_LOGGING</dt>
<dd><p>Sets the user-log level in the JSON response to POST
                                            /conversation requests and Hit Nodes table (View
                                            Conversation view). The following values are valid:</p><dl><dt>0</dt>
<dd><p>Off</p></dd>
<dt>1</dt>
<dd><p>Local account only</p></dd>
<dt>2</dt>
<dd><p>Parent account (language pack) only</p></dd>
<dt>3</dt>
<dd><p>Local and parent account</p></dd>
</dl>
</dd>
<dt>CLS_SEARCH_MODE</dt>
<dd><p>Specifies the search mode. The following values are valid:</p><dl><dt>0</dt>
<dd><p>Classifier</p></dd>
<dt>1</dt>
<dd><p>Variations</p></dd>
</dl>
</dd>
<dt>CLS_MODEL</dt>
<dd><p>Specifies that the Natural Language Classifier training
                                            model is used. The value is 0.</p></dd>
<dt>CLS_MODELNAME</dt>
<dd><p>Specifies the classifier ID that is generated during the
                                            training process.</p></dd>
<dt>CLS_MAXNBEST</dt>
<dd><p>Specifies an <em>n</em>-best list of
                                            classifier variables that are retrieved from the Natural
                                            Language Classifier and set as profile variables, where
                                                <em>n</em> is an integer 1 - 10.</p></dd>
<dt>CLS_USE_OFFTOPIC</dt>
<dd><p>Specifies whether to use the Natural Language Classifier
                                            off-topic model. When it is turned on, the implicit or
                                            explicit Natural Language Classifier off-topic model is
                                            used to lower output confidences when the Natural
                                            Language Classifier thinks the question is an off topic.
                                            Valid values are true and false. The default value is
                                            false.</p></dd>
<dt>PLATFORM_VERSION</dt>
<dd><p>Specifies the platform version for maintenance and
                                            upgrades. If you are designing a dialog in XML from
                                            scratch, use the value 10.1.</p></dd>
<dt>USE_TRANSLATIONS</dt>
<dd><p>Uses a translations list to rewrite some words or
                                            phrases in a different format. The following values are valid:</p><dl><dt>0</dt>
<dd><p>Off</p></dd>
<dt>1</dt>
<dd><p>Local account only</p></dd>
<dt>2</dt>
<dd><p>Parent account (language pack) only</p></dd>
<dt>3</dt>
<dd><p>Local and parent account</p></dd>
</dl>
</dd>
<dt>USE_SPELLING_CORRECTIONS</dt>
<dd><p>Specifies whether to use an automatic spellchecker for
                                            user input. Each language has a default LanguageWare
                                            spellchecker dictionary, and a parent and local account
                                            could have additional dictionaries. A Japanese-language
                                            dictionary and spellchecking are not available, so for
                                            Japanese this setting is turned off by default. The
                                            following values are valid: </p><dl><dt>0</dt>
<dd><p>Off</p></dd>
<dt>1</dt>
<dd><p>Uses the standard Languageware
                                                spell-correction dictionary for the language
                                                specified by the LANGUAGE setting and all the
                                                words that are defined in the local account.</p></dd>
<dt>2</dt>
<dd><p>Uses the standard Languageware
                                                spell-correction dictionary for the language
                                                specified by the LANGUAGE setting and all the
                                                words that are defined in the parent account.</p></dd>
<dt>3</dt>
<dd><p>Uses the standard Languageware
                                                spell-correction dictionary for the language
                                                specified by the LANGUAGE setting and all the
                                                words that are defined in the local account and
                                                the parent account.</p></dd>
</dl>
</dd>
<dt>USE_STOP_WORDS</dt>
<dd><p>Specifies whether to use a stop-word list to hide some
                                            common words from processing. Common words on an English
                                            stop-word list are the articles a, an, and the. The
                                            following values are valid: </p><dl><dt>0</dt>
<dd><p>Off</p></dd>
<dt>1</dt>
<dd><p>Local account only</p></dd>
<dt>2</dt>
<dd><p>Parent account (language pack) only</p></dd>
<dt>3</dt>
<dd><p>Local and parent account</p></dd>
</dl>
</dd>
<dt>USE_AUTOMATIC_STOPWORDS_DETECTION</dt>
<dd><p>Specifies whether to use the automatic algorithm based
                                            on a sentence parse tree to detect stop words. This
                                            setting is useful for languages such as Japanese. The
                                            following values are valid: </p><dl><dt>0</dt>
<dd><p>Off</p></dd>
<dt>1</dt>
<dd><p>On</p></dd>
</dl>
</dd>
</dl>
</td>
</tr>
<tr><td><p>type</p></td>
<td><p>Specifies the scope of the setting. Only the USER value is
                                valid.</p></td>
</tr>
</tbody>
</table>
