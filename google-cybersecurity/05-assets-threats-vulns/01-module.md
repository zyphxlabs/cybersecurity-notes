## Assets threats and vulnerabilities

Security plans are basically built around three things assets threats and vulnerabilities they represent what why and how of security asset is anything that has value to a company like buildings equipment data and even people threat is any event or circumstance that can hurt those assets and vulnerability is the weakness that a threat can use to actually cause damage like a weak lock is vulnerability and burglar trying to get in is the threat

Risk is calculated as likelihood x impact so its not just about something bad happening but how likely it is and how bad it would be if it did happen that helps companies decide where to actually spend their time and resources because they cant protect everything at once

Threats come in two types

- intentional like a hacker targeting a misconfigured app on purpose
- unintentional like an employee accidentally holding door open for a stranger

vulnerabilities also come in two types

- technical like misconfigured software
- human like someone losing their access card

## Asset management and classification

Asset management is just tracking what you have and the risk around it you cant protect something if you dont even know it exists so companies keep an asset inventory which is basically a catalog of everything worth protecting

Once they know what they have they classify it based on how sensitive or important it is the common levels are public internal-only confidential and restricted restricted being the most sensitive stuff like health or payment info that only need to know people can access

government orgs are a bit different they call their most sensitive level confidential instead of restricted so the naming isnt always same everywhere

classifying assets isnt always simple specially with info like figuring out who actually owns something say a company gives you a laptop for work but you also keep personal photos on it now its not fully clear who owns what and one piece of info can have multiple classification levels at once like your name being public but your address being more confidential

## States of data

Data lives in three states and protecting it depends on which state its in

- data in use is when someone is actively accessing it like checking email
- data in transit is when its moving from one place to another like sending a message
- data at rest is when its just sitting somewhere not being touched like a closed laptop

worth noting now with cloud stuff data isnt really at rest just because your phone is sitting on a table since its probably still synced somewhere

## Cloud computing and cloud security

Cloud computing basically changed how businesses operate online now you dont need to build your own infra from scratch you can just use cloud based services to scale faster and cheaper

there are three main types of cloud services

- SaaS which is front end apps you use through browser like gmail slack zoom company handles all backend stuff
- PaaS which gives developers tools to build their own apps while provider manages the backend hardware and software examples are google app engine heroku vmware cloud foundry
- IaaS where you get remote access to backend systems like servers storage networking and you pay for what you use instead of buying your own hardware

cloud security is its own subfield now focused on protecting data apps and infra thats hosted in cloud instead of on premises

the big concept here is shared responsibility model basically who is responsible for what depends on the service type client usually handles identity and access management resource configuration and data handling while provider handles the underlying infra security

challenges with cloud security

- misconfiguration is the biggest one since clients often just use default settings that dont match their actual needs
- cloud native breaches happen more due to this misconfig issue
- monitoring access can get tricky depending on service level
- meeting regulations like HIPAA PCI DSS GDPR also becomes harder since data isnt sitting in your own building anymore

## Security culture policies standards and procedures

Security isnt just IT departments job its a shared culture that includes employees vendors and customers everyone has some role to play in protecting assets

security plans usually get broken down by risk categories like damage disclosure or loss of information and the causes behind these can be physical damage device malfunction attacks or just human error like sending sensitive info from personal email

plans are communicated through three elements

- policy which is the set of rules explaining what we are protecting and why example is acceptable use policy AUP that new employees sign
- standard which is more tactical its like a reference point for setting policies example is NIST SP 800-63B saying passwords need to be atleast 8 characters
- procedure which is the actual step by step instructions for doing a task like how to reset your password securely

these three together basically turn abstract security goals into actual actionable stuff for everyone in the company

## Compliance and NIST CSF

Compliance is just following internal standards and external regulations companies care about this a lot because being out of compliance can lead to fines lawsuits and damage to reputation especially in industries like health care energy and finance

regulations are different from frameworks regulations are mandatory rules set by government while frameworks like CSF are optional resources companies can choose to use

NIST CSF was originally released in 2014 to protect critical infra in US later on it got adapted for public and private businesses too so more companies specially smaller ones could use it without building their own plan from zero

NIST CSF is a voluntary framework that helps companies manage cybersecurity risk it has three main parts

- core which is basically a checklist of functions identify protect detect respond recover and govern govern got added later in 2024 to stress leadership role in managing risk
- tiers which measure how mature a companys security program is on a scale of 1 to 4 tier 1 being bare minimum passive and tier 4 being adaptive and well developed
- profiles which are like a snapshot of where the security plan stands at a certain point in time so you can compare it to another point later kind of like comparing old photos to see how something changed over time

CISA gives a rough guide on how to actually implement CSF

- create a current profile outlining your specific business needs
- do a risk assessment to see whats meeting regulatory and business standards
- find and prioritize the gaps that put your assets at risk
- make an action plan to actually hit your goals

CSF isnt always easy to implement tho since its pretty detailed and companies at different stages find different parts useful some already have a plan and just use CSF to check gaps others use it as a starting point from scratch