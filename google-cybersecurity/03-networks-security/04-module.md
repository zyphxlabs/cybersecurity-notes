## Security Hardening

Security hardening is basically the process of making a system stronger by reducing how many ways an attacker can get in which is called the attack surface. Think of it like a house where every door and window is a way a robber could enter so hardening means putting locks on all of them and reducing the number of entry points entirely. It can be done on hardware operating systems applications networks databases and even physical spaces using cameras and guards. Common hardening tasks include patch updates configuration changes removing unused apps and services disabling unused ports and reducing access permissions. The fewer things connected and open on a network the less there is to monitor and attack. Penetration testing is also part of hardening where a simulated attack is run against the system to find vulnerabilities before a real attacker does and the results are documented so teams can fix what was found

## OS Hardening

The OS is what sits between the hardware and the user and it is the first thing that loads when a computer turns on so if it is compromised the whole network can be compromised. Patch updates are one of the most important regular tasks because as soon as a vendor releases a patch for a vulnerability malicious actors already know exactly where that vulnerability is in any system still running the old version so the patch needs to go out fast. After patching the updated system gets added to the baseline configuration which is the documented set of specifications used as a reference for future builds so if anything looks off later you can compare it to the baseline. Hardware and software disposal is also part of hardening because old hardware needs to be properly wiped and unused software should be deleted since some programming languages have known vulnerabilities sitting there doing nothing. Password policies are another regular task requiring things like a minimum of eight characters a capital letter a number and a symbol and usually locking the account after a certain number of wrong attempts. MFA which stands for multi-factor authentication adds another layer by requiring the user to verify in two or more ways using

- Something you know — like a password
- Something you have — like an ID card
- Something unique about you — like a fingerprint

## Brute Force Attacks and Prevention

A brute force attack is basically when an attacker just keeps guessing passwords until they get in. Simple brute force is just randomly trying combinations while dictionary attacks use a list of commonly used passwords and credentials stolen from previous breaches. To test for these kinds of vulnerabilities before they get exploited organizations use virtual machines and sandboxes. A VM is a software version of a physical computer that runs code in isolation so if malware runs in it the rest of the system stays safe and the VM can be deleted and replaced with a clean image after. A sandbox is a testing environment completely separate from the network used to test suspicious files patches or simulate attacks. The tricky thing is some malware is smart enough to detect it is running inside a VM or sandbox and behave like harmless software until it is in a real environment. Prevention methods include

- Hashing and salting  hashing converts a password into a unique value that cannot be reversed and salting adds random characters to the hash making it longer and harder to crack
- MFA and 2FA  requiring more than just a password to get in
- CAPTCHA and reCAPTCHA  Google's free service that makes users prove they are human to stop bots from running brute force attempts
- Password policies  rules about complexity how often to update whether passwords can be reused and limits on login attempts

## Network Hardening

Network hardening focuses on securing network-related things like port filtering access privileges and encryption. Some tasks happen regularly like firewall rules maintenance network log analysis patch updates and server backups. Network log analysis is when security teams go through logs to find events of interest and they use a SIEM tool to do this which collects and analyzes log data from across the network and shows everything in one dashboard called a single pane of glass. The SIEM also gives a prioritized list of vulnerabilities from high to low where high priority ones have a much shorter deadline to fix. Other tasks are done once and updated as needed like port filtering which means only keeping open the ports that are actually needed and blocking everything else because any unused open port is a vulnerability waiting to be exploited. Networks should always run the most up-to-date wireless protocols and older ones should be disabled. Network segmentation is used to create isolated subnets for different departments like one for marketing and one for finance so if one subnet has an issue it does not spread to the whole company and users only get access to the part of the network they actually need for their job. All network communication should be encrypted using the latest encryption standards and data in restricted zones needs even higher encryption standards

## Network Security Tools

These are the layers of defense that security teams use and each one adds more protection on top of the last

- Firewall — allows or blocks traffic based on rules and inspects packet headers. NGFWs can also inspect packet payloads. Every system should have its own firewall not just the network one
- IDS (Intrusion Detection System) — sits behind the firewall and monitors traffic for known attack signatures and anomalies then alerts the admin. It does not stop anything it just detects and reports so the admin has to act. New sophisticated attacks might slip through
- IPS (Intrusion Prevention System) — like an IDS but it actually stops the suspicious traffic by blocking the sender or dropping packets. The downside is it sits inline so if it breaks the whole connection between the private network and the internet breaks and it can also block legitimate traffic if it gets a false positive
- Full packet capture devices — record and analyze all data transmitted over the network and help investigate IDS alerts
- SIEM — collects and analyzes log data from firewalls IDSs IPSs VPNs proxies and DNS logs all into one dashboard. Does not stop anything on its own but gives analysts everything in one place to make decisions. Security analysts work in a SOC to monitor this dashboard and escalate events when needed

## Cloud Security

Cloud infrastructure needs to be secured just like regular networks but it has some unique challenges. IAM or Identity Access Management is a big one because misconfigured user roles in the cloud can let unauthorized people access critical operations. Configuration is also tricky because every cloud service needs to be precisely configured and during migrations if something is misconfigured it exposes the network to vulnerabilities. The attack surface also grows with every new cloud service added because each one is a potential entry point. Zero-day attacks are important to consider too but CSPs actually handle these better than traditional IT because they can patch hypervisors and migrate workloads to other VMs before customers are even impacted. One limitation with cloud is visibility because while admins can see all packets on a traditional network CSPs do not let you monitor traffic on their servers directly but they do offer flow logs and packet mirroring tools and also pay for third-party audits

The shared responsibility model is the key principle here which basically says the CSP is responsible for securing the physical data centers hypervisors and host OS and the organization using the cloud is responsible for securing whatever they put in it. A problem happens when companies assume the CSP is handling security they actually have not taken responsibility for like configuring their own cloud services properly

Cloud hardening techniques include

- IAM — managing who gets access to what cloud resources
- Hypervisors — type one runs on hardware like VMware ESXi and type two runs on software like VirtualBox. CSPs use type one and manage it themselves but misconfigurations can cause VM escapes where an attacker gets access to the primary hypervisor and potentially other VMs
- Baselining — setting a fixed reference point for how the cloud environment is configured so any changes can be compared against it
- Cryptography — encrypting data stored and processed in the cloud using encryption keys so unauthorized actors cannot read it
- Cryptographic erasure — instead of traditional data deletion you destroy the encryption keys which makes the data completely unreadable. All copies of the key must be destroyed
- Key management tools — TPM is a chip that securely stores passwords and encryption keys and CloudHSM is a device that provides secure storage for cryptographic keys and handles encryption and decryption operations