## Logs and Log Sources

So logs are basically just records of everything that happens inside a system or network, and as a security analyst you're gonna be going through a lot of them. There are three main types — firewall logs which track incoming and outgoing internet traffic, network logs which record every device entering or leaving the network and connections between them, and server logs which capture stuff like login attempts, username and password requests tied to services like websites or emails. The whole point of monitoring these is to catch vulnerabilities and potential breaches before they get out of hand.

## SIEM Tools

SIEM stands for security information and event management and its basically an application that pulls in all that log data from different sources, analyzes it, and monitors critical activity in real time. The good thing about SIEM is it centralizes everything so instead of a analyst manually going through thousands of logs it does the heavy lifting and throws alerts when something looks off. But it's not a set it and forget it thing, organizations have to keep configuring and updating their SIEM as new threats show up.

## SIEM Dashboards

SIEM tools also come with dashboards which is just a visual way to see all your security data, think of it like a weather app but for threats. Like if someone gets an alert about a suspicious login they can pull up the dashboard and immediately see that there were 500 login attempts on Ymara's account in five minutes, from weird locations, outside her normal hours — that's all right there visually instead of digging through raw logs. Dashboards also show metrics like response time, availability, and failure rate so you can actually measure how things are performing.

## Types of SIEM Deployments

There are three ways organizations can run their SIEM:
- Self-hosted — organization installs and runs everything on their own physical infrastructure, ideal when they need full control over confidential data
- Cloud-hosted — vendor handles everything, you just access it through the internet, good for orgs that don't wanna deal with their own infrastructure
- Hybrid — mix of both, lets you get cloud benefits while still keeping physical control over sensitive stuff

## Splunk and Chronicle

Splunk is a data analysis platform and it has two SIEM products. Splunk Enterprise is the self-hosted version used to retain, analyze and search log data and gives real-time alerts. Splunk Cloud is the cloud-hosted version that does the same but for organizations running hybrid or cloud-only environments. Then theres Chronicle which is Google's cloud-native SIEM tool, cloud-native meaning it's built from the ground up to take advantage of cloud capabilities like flexibility, scalability and availability — not just hosted on cloud but actually designed for it. Chronicle handles log monitoring, data analysis and collection.

## Splunk Dashboards

Splunk has a few different dashboards depending on what you need:
- Security posture dashboard — shows last 24 hours of notable security events, mostly used by SOC teams to monitor threats in real time
- Executive summary dashboard — gives a high level health overview of the org over time, useful for reporting to stakeholders
- Incident review dashboard — highlights high risk items and shows a visual timeline of events leading up to an incident
- Risk analysis dashboard — tracks risk per object like a specific user, computer or IP, and flags unusual behavior like logins outside normal hours

## Chronicle Dashboards

Chronicle has its own set of dashboards too:
- Enterprise insights dashboard — shows recent alerts and suspicious domains flagged as indicators of compromise, each with a confidence score and severity level
- Data ingestion and health dashboard — shows how many logs are coming in and if they're being processed correctly
- IOC matches dashboard — displays top threats and lets analysts track domains, IPs and devices over time to spot trends
- Main dashboard — high level summary of ingestion, alerts and event activity, good for spotting spikes like a surge in failed logins
- Rule detections dashboard — shows which detection rules are firing the most and how severe they are
- User sign in overview dashboard — tracks user login behavior across the org, catches things like someone signing in from multiple locations at the same time

## Open-Source vs Proprietary Tools

Open-source tools are free, built collaboratively, and the source code is public which actually makes them harder to exploit because the community catches issues fast. Proprietary tools like Splunk and Chronicle are owned by companies, users pay for access and training, and only the vendor can touch the source code so you're dependent on them for updates. Common misconception is that open-source equals less safe but that's not really true, a lot of open-source tools are straight up industry standards at this point.

## Linux and Suricata

Linux is an open-source operating system that lets you interact with hardware through a command-line interface and you can customize it heavily for security work. Suricata is an open-source network analysis and threat detection tool made by the Open Information Security Foundation, it inspects network traffic, spots suspicious behavior, generates network logs, and integrates with a lot of SIEM tools including the ones above.

## Future of SIEM

SIEM tools are evolving to work better in cloud environments and the next big thing is automation through something called SOAR — security orchestration automation and response — which is basically a collection of tools and workflows that handle common security incidents automatically without waiting on a human. This frees analysts up to deal with the complex stuff that can't be automated. On top of that AI and ML are being worked into SIEM to improve threat detection, dashboard visuals and data storage. With IoT devices multiplying the attack surface is only getting bigger so SIEM tools are gonna have to keep up.