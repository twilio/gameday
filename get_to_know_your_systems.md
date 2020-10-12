<!-- Copy and paste the converted output. -->



## Gameday Template


### Scenario 1 - Get To Know Your System

* [How To Use This Document](#how-to-use-this-document)

* [Why Gameday?](#why-gameday)

* [Service Context](#service-context)

  * [What does this system do?](#what-does-this-system-do)
  
  * [Who is the customer and what is their primary use case?](#who-is-the-customer-and-what-is-their-primary-use-case)
  * [What is the user flow for the primary use case within this system?](#what-is-the-user-flow-for-the-primary-use-case-within-this-system)
  * [How is the customer impacted when this system is degraded?](#how-is-the-customer-impacted-when-this-system-is-degraded)
  * [What Service Level Objectives (SLOs) have we set in order to achieve the desired customer experience?](#what-service-level-objectives-slos-have-we-set-in-order-to-achieve-the-desired-customer-experience)
  * [What Service Level Indicators (SLIs) do we use to measure the achieved experience?](#what-service-level-indicators-slis-do-we-use-to-measure-the-achieved-experience)
* [Preparation Checklist](#preparation-checklist)
  * [Toolbox](#toolbox)
  * [Before the Game Day](#before-the-gameday)
  * [After the Game Day](#after-the-gameday)
* [Gameday](#gameday)
  * [Roles and Responsibilities](#roles-and-responsibilities)
  * [Scenario 1 - Get To Know Your System](#scenario-1-get-to-know-your-system)
## 


## <a name="how-to-use-this-document"></a>How To Use This Document

**Please start by making a copy of this document.**<br/>
This document is laid out such that it guides a team through the preparation for a Gameday via questions around the context of a service and the preparation of resources for the Gameday, as well as the execution of the Gameday itself including guiding steps and questions to help maximize the value from the exercise.

The preparation of the execution steps for the Gameday can be completed by one or two people, likely the Gameday coordinator(s), and should take approximately one day. Preparing for following Gamedays should become easier and quicker as experience in the team grows.

The execution of the Gameday should be completed by the whole team and will take at least an hour, likely several. The document can be used as a space to collaboratively document thoughts, questions, and betterments.


## <a name="why-gameday"></a>Why Gameday?

A Gameday is an effective way to validate our knowledge of our systems, that our SLIs and observability are configured appropriately, and that our system handles failures as expected. It is a way to test the following (in order of importance):



1. SLIs should accurately measure the level of service by considering customer usage patterns.
2. Alerts should trigger appropriately.
3. Dashboards should be configured so we can easily answer the question of if our system is healthy or not, and if not, what the SLI violation is that indicates our system isn’t healthy.
4. We should have enough visibility to identify the root cause so we can effectively debug our systems during time of incident.

Gamedays are a way for us to test our systems, runbooks, dashboards, monitors, and incident response process so we can catch misunderstandings, regressions, false assumptions, and resiliency issues before they become incidents that impact our customers.

The outcome of a Gameday should be a list of betterments the team feels empowered to act upon. Following Gamedays should demonstrate the value of those betterments by addressing the concerns that came up the first time.




## <a name="service-context"></a>Service Context

This section should be completed before the execution of the Gameday.


### <a name="what-does-this-system-do"></a>What does this system do? 

Add details here about the purpose of the system from the perspective of the customer or end consumer, as well as some of the high level technical points that are important to know with regards to its end function.


### <a name="who-is-the-customer-and-what-is-their-primary-use-case"></a>Who is the customer and what is their primary use case? 

Identify the customer or end user (also known as the target persona) and the primary use case for them. While there may be multiple personas that utilize the product, as well as multiple use cases, it is best to prioritize them and understand who the primary persona is. Additional personas may be recorded here as well, but make sure to prioritize them.


### <a name="what-is-the-user-flow-for-the-primary-use-case-within-this-system"></a>What is the user flow for the primary use case within this system? 

Document the high level steps a customer goes through to achieve the primary use case. The intent of this is to make sure all parts of the system and user workflow are considered during the Gameday.


### <a name="how-is-the-customer-impacted-when-this-system-is-degraded"></a>How is the customer impacted when this system is degraded?

Document the expected customer impact during an incident when the system is degraded. This is to help make sure the team understands the symptoms that a customer may experience or that may be reported for when the system is degraded.


### <a name="what-service-level-objectives-slos-have-we-set-in-order-to-achieve-the-desired-customer-experience"></a>What Service Level Objectives (SLOs) have we set in order to achieve the desired customer experience?

SLOs for the system should already be created before completing the Gameday. A reminder that SLOs are a threshold applied to a Service Level Indicator (SLI). Document the SLOs here so everyone is working off of the same expectation during the Gameday.


### <a name="what-service-level-indicators-slis-do-we-use-to-measure-the-achieved-experience"></a>What Service Level Indicators (SLIs) do we use to measure the achieved experience? 

Document the SLIs that are monitored for this system. These are the high-level metrics that gauge the customer experience and determine whether or not the system is healthy. These metrics should be what you observe for answering the question, “Is our system healthy?” and based on the thresholds defined in your SLOs, will determine the answer to that question.




## <a name="preparation-checklist"></a>Preparation Checklist 


### <a name="toolbox"></a>Toolbox


<table>
  <tr>
   <td><strong>Name</strong>
   </td>
   <td><strong>URL(s)</strong>
   </td>
  </tr>
  <tr>
   <td>Runbook(s)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>PagerDuty Service(s)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Datadog Dashboard(s)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Rollbar Project(s)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Quantico
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Other Monitoring Tools
   </td>
   <td>
   </td>
  </tr>
</table>



### <a name="before-the-gameday"></a>Before the Gameday



*   Complete the Service Context portion of this document.
*   Verify that the test environment is healthy.
    *   Existing cluster or E2E tests tests are passing.
    *   Hosts are healthy and have the most recent code and configuration running.
*   Metrics are being sent to Datadog.
*   Confirm notifications are sent to Slack as expected.
*   Confirm paging works as expected.
    *   If you are using a non-production environment for your Gameday, you may not receive PagerDuty alerts depending on your configuration.
*   Prepare load generation scripts to simulate customer traffic.
*   Prepare failure injection script if necessary.


### <a name="after-the-gameday"></a>After the Gameday



*   Load generation script(s) stopped.
*   And failure injection is reversed such that the environment is healthy again.
*   All betterments identified are filed in JIRA to be completed by the team.




## <a name="gameday"></a>Gameday 


### <a name="roles-and-responsibilities"></a>Roles and Responsibilities


<table>
  <tr>
   <td><strong>Role</strong>
   </td>
   <td><strong>Responsibilities</strong>
   </td>
  </tr>
  <tr>
   <td>Gameday Coordinator(s)
   </td>
   <td>
<ul>

<li>Prepare for gameday

<li>Executing scenario steps

<li>Identify betterments
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>(Optional) On-Call / Triage Engineer
   </td>
   <td>
<ul>

<li>Respond to PagerDuty alerts

<li>Work through the incident response process as if this were a real incident

<li>Reach out for additional assistance as needed
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Attendees
   </td>
   <td>
<ul>

<li>Observe and respond to scenarios

<li>Identify betterments
</li>
</ul>
   </td>
  </tr>
</table>



### <a name="scenario-1-get-to-know-your-system"></a>Scenario 1 - Get To Know Your System 

**Description:** The first type of Gameday that should be run for each system a team owns. A small amount of load to generate happy path traffic is placed on the system, and the team reviews everything together.

**Purpose: **To demonstrate the functionality, validity, and effectiveness of the dashboards and monitors for a given system, as well as validate the SLIs and SLOs that were created by the team for the system. The team should quickly be able to answer if the system is healthy or not, and a focus on documenting any tribal knowledge should be made. Ideally, someone new to the team should be able to answer the question regarding the system’s health, not just the veteran members of the team.

**Expectations:**



*   We should be able to answer, “How many RPS is the load generator sending?”
*   We should be able to answer, “Are there any SLO violations?”
*   Do we expect to see any alerts?
*   Do we expect to see any errors?
*   Are the metrics reporting sane values?
*   Tribal knowledge is not required to answer questions about the system.

**Execution Steps:**



1. Baseline the system with no additional load generated by evaluating dashboards and monitors.
2. Generate happy path load against the system.
3. Validate the listed expectations as well as any others that the team may have come up with.
4. Stop the load.

**Observations and Findings:**



*   A place for questions, comments, and other notes that may come up during the Gameday.
*   Intended to be a place for collaborative documentation of what is happening, not for solutions.

**Betterments:**



*   Formalized betterments that the team agrees would be helpful. Should address the findings and observations that come up, and is where the solutions to problems that are observed should be documented.
*   Dashboards
    *   What can we improve?
    *   Are the metrics being used and the reported values correct?
    *   Are the SLIs all presented in a clear fashion?
    *   Are SLO thresholds visualized in a clear fashion?
    *   Do we utilize color coding and/or thresholds to illustrate healthy and unhealthy metric values?
    *   Do we provide meaningful titles on graphs that clearly describe the data?
    *   Do we make it easy for the on-call engineer to investigate further when there is an issue? This can be done by utilizing links to runbooks or other dashboards, as well as providing critical and related metrics next to the SLIs.
*   Monitors
    *   What can we improve?
    *   Are the metrics being used and the reported values correct?
    *   Are SLO thresholds backed by monitors that will page the on-call engineer as a breach is approached?
    *   Do monitors auto-resolve when they go back to healthy values?
    *   Have we tested the monitors to validate that they effectively reach PagerDuty and the expected on-call engineer?
    *   Will our monitor be relevant in 1 month? 6 months? 12 months?
    *   Can we utilize more advanced anomaly detection to better detect issues and prevent false positives?
    *   Are any monitors excessively noisy and need to be tuned or removed?
    *   Are there any irrelevant monitors or monitors showing No Data that can be fixed or removed?
    *   Do monitors include links to the relevant runbooks?
*   Runbooks
    *   What can we improve?
    *   Is it easy to find the relevant information?
    *   Would someone without experience with the system be able to effectively take action?
    *   Are documented actions up-to-date and relevant?
    *   Are we linking to our runbook in our monitors?
