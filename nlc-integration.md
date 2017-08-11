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

# IBM Watson Natural Language Classifier service integration
{: #nlc-integration}

Integration of the {{site.data.keyword.nlclassifiershort}} service with the {{site.data.keyword.dialogshort}} service provides new options for matching user input.
{: shortdesc}

You can use a trained natural language classifier statistical model in your dialog to route user input during a conversation. Classifiers are called from the search node, which operates by one of the following search strategies:

-   Rules-based matching
-   Classifier-only matching
-   Exact match first. This strategy is a combination of rules-based and classifier-only matching. The system tries rules-based matching first, and if a match is not found, it uses classifier-only matching.

For more information about these options and classifier settings, see the [classifier](/docs/services/dialog/classifier.html) and [setting](/docs/services/dialog/setting.html) elements.

The labels in the classifier training data are routed to dialog input nodes in the following ways:

-   The class name must be an &lt;item&gt; element in the input rules that contains the prefix `INTENT:`. For example, For example, if you have an intent for LOCATION, you need the following &lt;item&gt; element: would need a corresponding &lt;item&gt; in one of your inputs for INTENT: LOCATION
-   A variation that is prefixed by the INTENT keyword represents a label from the classifier (e.g. INTENT: OpeningTalk).

> **Important:** To integrate a classifier into your dialogs, you must create an instance of the {{site.data.keyword.nlclassifiershort}} service, get your service credentials, and train the classifier to be used with your data. For more information, see [Getting started with the {{site.data.keyword.nlclassifiershort}} service](http://www.ibm.com/watson/developercloud/doc/nl-classifier/get_start.shtml).

The following sample code shows how to call the classifier.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dialog xsi:noNamespaceSchemaLocation="WatsonDialogDocument_1.1.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <flow>
    <folder label="Main">
      <output>
        <prompt selectionType="RANDOM">
          <item>Hello, I'm here to help. Just ask your question.</item>
        </prompt>
        <goto ref="output_2502686"/>
      </output>
      <output isInsertDNRStatement="false" id="output_2502686">
        <prompt selectionType="RANDOM"/>
          <getUserInput>
            <search ref="folder_2517136">
              <classifier policy="SEARCHMODE_CLASSIFIER"
                threshold="0.6" exactMatchFirst="true"
                fuzzyThreshold="0.1">
                <customParams></customParams>
              </classifier>
            </search>
            <default>
              <output>
                <prompt selectionType="RANDOM">
                  <item>NO_MATCH</item>
                </prompt>
              </output>
            </default>
          </getUserInput>
      </output>
    </folder>
    <folder label="Library">
      <folder label="Movies" id="folder_2517136">
        <input>
          <grammar>
            <item>INTENT: LookupDirectors</item>
            <item>how are you?</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was LookUpDirectors</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: LookupActors</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was LookUpActors</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: SmallTalk</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was SmallTalk</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: CheckShowtimes</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was CheckShowtimes</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: SearchMovies</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was SearchMovies</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: GiveName</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was GiveName</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: ClosingTalk</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
             <item>It was ClosingTalk, cls: {CLASSIFIER_CLASS_0}, conf: {CLASSIFIER_CONF_0}, {CLASSIFIER_CLASS_9}</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: PreSequence</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was PreSequence</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: OpeningTalk</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was OpeningTalk</item>
            </prompt>
          </output>
        </input>
        <input>
          <grammar>
            <item>INTENT: OtherClass</item>
          </grammar>
          <output>
            <prompt selectionType="RANDOM">
              <item>It was OtherClass</item>
            </prompt>
          </output>
        </input>
      </folder>
      <folder label="Storage"/>
    </folder>
    <folder label="Global"/>
    <folder label="Concepts">
      <folder label="Parent Concepts"/>
    </folder>
  </flow>
  <constants>
    <var_folder name="Home"/>
  </constants>
  <variables>
    <var_folder name="Home">
      <var name="CLASSIFIER_CLASS_1" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_1" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_2" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_2" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_3" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_3" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_4" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_4" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_5" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_5" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_6" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_6" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_7" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_7" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_8" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_8" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_9" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_9" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CLASS_0" type="TEXT" description="auto-created"/>
      <var name="CLASSIFIER_CONF_0" type="TEXT" description="auto-created"/>
    </var_folder>
  </variables>
  <settings>
    <setting name="AUTOLEARN" type="USER">false</setting>
    <setting name="RESPONSETIME" type="USER">-2</setting>
    <setting name="MAXAUTOLEARNITEMS" type="USER">4</setting>
    <setting name="NUMAUTOSETRELATED" type="USER">0</setting>
    <setting name="TIMEZONEID" type="USER">Australia/Sydney</setting>
    <setting name="AUTOSETRELATEDNODEID" type="USER">2158864</setting>
    <setting name="CONCEPTMATCHING" type="USER">1</setting>
    <setting name="DNR_NODE_ID">-16</setting>
    <setting name="USE_CONCEPTS">3</setting>
    <setting name="PARENT_ACCOUNT">en-US</setting>
    <setting name="AL_NONE_LABEL">None of the above</setting>
    <setting name="DEFAULT_DNR_RETURN_POINT_CANDIDATE">-1</setting>
    <setting name="ENTITIES_SCOPE">3</setting>
    <setting name="DEFAULT_POINT_NODE_ID">2502688</setting>
    <setting name="USER_LOGGING">2</setting>
    <setting name="CLS_SEARCH_MODE">0</setting>
    <setting name="CLS_MODEL">0</setting>
    <setting name="CLS_ENDPOINT"></setting>
    <setting name="CLS_USERNAME"></setting>
    <setting name="CLS_PASSWORD"></setting>
    <setting name="CLS_MODELNAME">1CC095x161-nlc-13</setting>
    <setting name="CLS_ADVANCED_SETTINGS">false</setting>
    <setting name="CLS_MAXNBEST">3</setting>
    <setting name="PLATFORM_VERSION">10.1</setting>
    <setting name="USE_TRANSLATIONS">2</setting>
    <setting name="USE_SPELLING_CORRECTIONS">2</setting>
    <setting name="USE_STOP_WORDS">2</setting>
    <setting name="USE_AUTOMATIC_STOPWORDS_DETECTION">0</setting>
  </settings>
  <specialSettings>
    <specialSetting label="AutoLearn Statement" selectionType="SEQUENTIAL">
      <variations/>
    </specialSetting>
    <specialSetting label="DNR Join Statement" selectionType="RANDOM">
      <variations/>
    </specialSetting>
  </specialSettings>
</dialog>
```
{: codeblock}
