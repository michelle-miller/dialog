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

# Dynamic node resolution (DNR)
{: #dnr}

Dynamic node resolution (DNR) is a mechanism that intelligently determines which node will continue the dialog when the system comes to the end of a node tree.
{: shortdesc}

DNR always returns the system to a getUserInput node only. The getUserInput node to which the system returns to depends on the structure of the dialog. In a typical dialog, a main getUserInput node serves as an entry point to the node tree. This main getUserInput node contains a set of child search nodes that tells the system to search in certain folders and one default node that handles the situations in which the system cannot find a match in the folders that the search nodes searched.

DNR is always enabled, and you control how it works by leveraging the settings that apply to your unique use case.

To see the complete XML file that shows the following examples, open <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/dialog/dnr_example.xml" download="dnr_example.xml">dnr_example.xml <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.

## DNR with getUserInput nodes and search nodes

When the system hits a search node, it looks for a match to the user's input in the folders and subfolders to which the search node directs it. Let's say the user submits `I am bored`. The system finds a match to that input in the ChitChat subfolder of the Library folder and displays the content of the matching output node. Because these output nodes in the ChitChat subfolder are leaf nodes (They don't have child nodes.), the system returns to the nearest getUserInput node that precedes the search node that sent the system to the folder where a match was found. When the default settings are used, the system displays the content of the output node that precedes the getUserInput node to which the system returned. This output node provides the right context for the user, so that the user can understand the system's expectations. The following exchange between a user and the system shows how DNR works in the flow of this conversation:

-   **System:** Hello there! We do insurance, banking and weather.
-   **User:** I am bored
-   **System:** Maybe I can cheer you up by giving you an insurance quote?
-   **System:** Anything else I can do for you?

## DNR in subdialogs with the default node

In this example, when the user asks for her card to be blocked, a subdialog begins so that she can confirm that she does want her card to be blocked. The subdialog is defined by a getUserInput node that follows the system's request for confirmation. The system wants the user to answer yes or no, but the user can say anything she wants to say. In case she submits input that does not match to yes or no, the system hits the default node, a child node of the getUserInput node, so that the user must make a decision whether to block the card. This default node ensures that the subdialog continues until the user gives an answer that matches to yes or no. DNR returns the system to the nearest getUserInput node that precedes this default node. The following exchange between a user and the system shows how DNR works in the flow of this conversation:

-   **System:** Hello there! We do insurance, banking and weather.
-   **User:** Block my card.
-   **System:** Are you sure you want your card 1234 blocked?
-   **User:** What is the weather
-   **System:** Say yes to block your card 1234 or no to cancel.
-   **System:** Are you sure you want your card 1234 blocked?

However, if the user submits input that matches to yes or no, the subdialog ends, and regular DNR rules apply, returning the system to the first getUserInput node in the dialog.

-   **System:** Hello there! We do insurance, banking and weather.
-   **User:** Block my card.
-   **System:** Are you sure you want your card 1234 blocked?
-   **User:** No.
-   **System:** Allright, keeping your card active.
-   **System:** Anything else I can do for you?

## DNR in subdialogs without the default node

In this example, when the user submits input that is out of the context of the current subdialog, the system finds a match to the input, which begins a new subdialog. When this new subdialog ends, DNR returns to the beginning of the original subdialog. The following exchange between a user and the system shows how DNR works in the flow of this conversation:

-   **System:** Hello there! We do insurance, banking and weather.
-   **User:** How are you?
-   *The subdialog begins.*
-   **System:** I am fine. How are you?
-   **User:** Fine.
-   **System:** Glad to hear that!
-   *The subdialog ends, and DNR returns to the original subdialog at this output node.*
-   **System:** Anything else I can do for you?

However, in some cases, a subdialog might not contain matches to submitted input. In these cases, DNR returns to the previous getUserInput node that precedes the search node. When a match is found, the conversation continues from there. When this conversation ends at a leaf node, DNR returns to the original subdialog because it still needs to reach an end. The following exchange between a user and the system shows how DNR works in the flow of this conversation:

-   **System:** Hello there! We do insurance, banking and weather.
-   **User:** How are you?
-   *The subdialog begins.*
-   **System:** I am fine. How are you?
-   **User:** I am bored.
-   *This user input does not have a match in the subdialog, and no default node is in the subdialog. DNR exits the subdialog and returns to the previous getUserInput node that precedes the search node.*
-   **System:** Maybe I can cheer you up by giving you an insurance quote?
-   *The system found a match, and DNR returns to the subdialog because it still needs to finish.*
-   **System:** I am fine. How are you?

## DNR settings

You can change how DNR works by using these settings:

-   **DNR return action**

    The DNR_NODE_ID setting specifies whether DNR returns to the previous getUserInput and displays the content of the previous closest output node to provide context or just returns to the previous getUserInput node without displaying the content of the previous closest output node. For more information, see the description of DNR_NODE_ID in the [setting](/docs/services/dialog/setting.html) element. The default action is to return to the previous getUserInput and display the content of the previous closest output node.
-   **DNR join statement**

    The text to be displayed every time DNR is in action, if the default value is specified for the DNR_NODE_ID setting. For more information, see the [specialSetting](/docs/services/dialog/specialSetting.html) element.
-   **Return point candidates and DNR candidates**

    The following advanced settings are for experienced dialog designers to further customize how DNR works.

    The DEFAULT_DNR_RETURN_POINT_CANDIDATE setting specifies the default behavior during a check to determine whether a getUserInput node is a DNR return point pcandidate. For more information, see the description of DEFAULT_DNR_RETURN_POINT_CANDIDATE in the [setting](/docs/services/dialog/setting.html) element.

    The isDNRCandidate attribute of the getUserInput node specifies whether the getUserInput node is used as a target return point for the DNR process. For more information, see the description of isDNRCandidate in the [getUserInput](/docs/services/dialog/getUserInput.html) element.

    If default values are specified for both the DEFAULT_DNR_RETURN_POINT_CANDIDATE element and isDNRCandidate attribute, all of the getUserInput nodes are DNR candidates, and the regular rules of DNR apply. However, if DEFAULT_DNR_RETURN_POINT_CANDIDATE is false, the getUserInput node is not a DNR candidate, and the system can't find a return point, the system returns to the DNR master point. If the DNR master point is not set, the system returns to the very first getUserInput node.
-   **Master point**

    The DEFAULT_POINT_NODE_ID setting specifies the DNR master point, the node t which you want DNR to ultimately return. For more information, see the description of DEFAULT_POINT_NODE_ID in the [setting](/docs/services/dialog/setting.html) element.

    If search nodes aren't hit, the system returns to the master point. If the master point is not specified, the system returns to the first getUserInput node in the dialog.
