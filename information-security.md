---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-09"

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

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## Deleting data in Dialog
{: #gdpr-dialog}

Do not add personal data to the training data (entities and intents, including user examples) that you create.

If you need to remove a customer's message data from a Dialog service instance, create a support ticket to request the deletion.

### Deleting data
To request the deletion of data that was added to the service by a specific user, create a support request. Go to [IBM Cloud service support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson.service-now.com/wcp), and then enter a ticket to request the data deletion.

If you know the `client_id` that was passed with POST requests sent to the `/conversation` endpoint, the `conversation_id`, or the time frame in which conversations were created by this user, add the information to the ticket.

To take advantage of feature enhancements, including the ability to delete message data associated with specific customer IDs yourself, consider upgrading to the [{{site.data.keyword.conversationshort}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/conversation/index.html).
