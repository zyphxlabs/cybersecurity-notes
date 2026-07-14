## Stakeholders and their roles

Stakeholder is basically any individual or group that has interest in the decisions or activities of an organization so in security context these are the people who care about how well the company is protected. There is a whole hierarchy that goes from analyst to management all the way up to executives and each level has different concern about security

There are five main stakeholders we focus on

- risk managers
- CEO
- CFO
- CISO
- operations managers

Risk managers identify risks and manage response to security incidents they also notify legal department for regulatory issues and inform PR team if public communication is needed

CEO is highest ranking person in the org responsible for financial and managerial decisions and reports to shareholders so security becomes top priority for them naturally

CFO manages financial operations of company and cares about security mainly from cost angle like how much an incident would cost the business and also cost of tools and strategies used to fight security issues

CISO is highest level security stakeholder responsible for developing organization's security architecture doing risk analysis system audits and creating security and business continuity plans

Operations managers oversee security professionals and are usually first line of defense working directly with analysts they handle daily maintenance of security operations

As entry level analyst i probably wont talk directly to risk manager CEO CFO or CISO most of my communication will go through operations manager who then passes things up if needed

## Communicating with stakeholders

Since the info being communicated is sensitive like a breach report i need to be careful about what im sending and who im sending it to different stakeholders need different info so it has to stay clear concise and focused

Before sending anything i should ask my manager what the stakeholders actually need to know having a security mindset means asking questions like whats the most important data to protect daily or what tool has been most useful for protecting our assets

Some questions to ask myself before sending any communication

- what do i want this person to know
- why is it important for them to know it
- when do they need to take action
- how do i explain this without technical jargon

Lower level stakeholders like ops managers and risk managers care more about day to day stuff like log anomalies while senior stakeholders like CFO and CISO care about bigger picture stuff like financial burden of an incident so i need to match my message to who im talking to

## Telling a security story

Creating a security communication is basically like telling a story with beginning middle and end theres a conflict which is the security issue and then a resolution which is the proposed solution

Steps to build the story

- detail the issue like what was found in the logs
- refer to incident response playbook and mention its guidance
- provide a possible solution even if im not the final decision maker

This can be shared through email document ticketing system or visuals depending on situation many orgs already have incident management systems that follow their playbook steps

## Choosing communication method

The method depends on how complex and how sensitive the info is

- instant messaging or phone call for straightforward stuff
- email or in person meeting for complex multi layered situations
- spreadsheet or graph when its mostly data and numbers

Emails can have long wait times since stakeholders are busy so sometimes a quick call or message moves things forward faster than waiting days for a reply following up shows initiative and can prevent small issues from becoming big ones

## Visual dashboards

A visual dashboard is a way of displaying different types of data quickly in one place its useful specially when the story involves numbers a dashboard can be as simple as one chart or as complex as multiple charts graphs and tables depending on what im trying to show

Tools like Google Sheets and Apache OpenOffice are free options to build these dashboards

## Building a bar chart in Google Sheets

Scenario was ops manager needs to tell CISO which departments click phishing emails the most turns out the five departments were HR customer service global security media relations and professional development

Steps to build it

- open google sheets and start blank spreadsheet
- A1 type Department B1 type # of clicked phishing emails
- A2 Human Resources B2 30
- A3 Customer Service B3 18
- A4 Global Security B4 10
- A5 Media Relations B5 40
- A6 Professional Development B6 27
- select all the data including headers
- click Insert then Chart
- in chart editor pick bar chart type first option
- go to customize then chart and axis titles and rename it something like Clicked phishing emails by department
- close the chart editor

This basically turns raw numbers into something stakeholders can understand in seconds instead of reading a paragraph explaining the same thing

## Julianas story example

Juliana had two incidents to communicate after escalating them one was an employee locked out from failed logins across five departments since this was mostly numbers she built a visual dashboard for the senior executives to review and decide next steps

Second