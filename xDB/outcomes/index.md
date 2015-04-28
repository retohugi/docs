---
layout: default
title: Sitecore 8 Outcomes
category: xdb
---

# Outcomes

## What is an Outcome?

“An outcome is the business significant result of a dialogue between a contact and a brand.”

A business significant result could mean the following:

Think of an organisation looking to run a campaign to get sign ups for a website; marketers can run MV tests and personalisation across the site to try and push people to the sign up. 
So in this instance the sign up of users is the business significant result.

Essentially, Outcomes are similar to Sitecore Goals, but they offer a more meaningful way of recording the result of a user's interactions.

Typical examples of Outcomes are Contact Acquisition or Sales Lead.

The Outcome items are housed in the new Marketing Control Panel 

![Marketing Control Panel]({{ site.baseurl }}/images/Outcomes/Marketing center.JPG)

When Outcomes are triggered they are stored in the xDB database and they can be viewed on a contact's activity tab.

![Activity Tab]({{ site.baseurl }}/images/Outcomes/xdb_outcome.JPG)

## How do I trigger an Outcome?

At present, an Outcome can only be triggered by using the analytics API and there is no out-of-the-box way for a marketer to trigger a Goal.

The code for triggering an Outcome is as follows.The new libraries for the OutcomeManager can be found in Sitecore.Analytics.Outcome.dll.

	ID id =  Sitecore.Data.ID.NewID;
	ID interactionId =  Sitecore.Data.ID.NewID;
	ID contactId =  Sitecore.Data.ID.NewID;
	 
	// definition item for Sales Lead
	var definitionId = new ID("{C2D9DFBC-E465-45FD-BA21-0A06EBE942D6}");
	 
	var outcome = new ContactOutcome(id, definitionId, contactId)
	{
	   DateTime = DateTime.UtcNow.Date,
	   MonetaryValue = 10,
	   InteractionId = interactionId
	};
	 
	var manager = Factory.CreateObject("outcome/outcomeManager",true) as OutcomeManager;
	manager.Save(outcome);

However, it is possible to use the API to create a custom Rule Action to trigger an Outcome.

An example of this is listed here: [https://github.com/ianjohngraham/CoreBlimey.Utils/tree/master/CoreBlimey.OutcomeRules](https://github.com/ianjohngraham/CoreBlimey.Utils/tree/master/CoreBlimey.OutcomeRules
)


