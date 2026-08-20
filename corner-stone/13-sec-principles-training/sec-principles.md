## CIA Triad
Before even getting into security principles you need to know who your adversary actually is, protecting a laptop from a curious toddler is a completely different problem than protecting one holding designs worth millions from industrial espionage. Perfect security doesnt exist, all we can really do is make it harder for the adversary to get in

Confidentiality is about making sure information only reaches the people its meant for, like your credit card number only going to the payment processor during online shopping, if you doubt that itll stay private youd probably back out of the purchase entirely. In healthcare its even more serious since providers are legally required to keep medical records confidential and can be held accountable if they leak

Integrity is about the data not getting tampered with, if someone alters your shipping address after you place an order it goes to the wrong person, or worse if a patient record gets altered it could lead to the wrong treatment being given which could genuinely be life threatening

Availability just means the system actually being up and usable when you need it, if an online store is constantly down youll eventually give up and shop somewhere else, and if a clinics system is down a doctor cant pull up your medical history which makes diagnosis harder and more error prone

These three dont all need equal weight all the time, like a university announcement doesnt need to be confidential but its integrity matters a lot since you dont want it tampered with

## Beyond CIA
Authenticity is about confirming that something actually came from who it claims to be from, not fraudulent or faked. Nonrepudiation means the source cant later deny that they were the ones who sent or created something. These two go hand in hand, you need to know an order is genuinely from the customer and that they cant turn around and deny placing it, a business can maybe tolerate a fake order for a t shirt but definitely not for something like 1000 cars

## Parkerian Hexad
Back in 1998 donn parker proposed six security elements instead of just three, on top of availability integrity authenticity and confidentiality he added two more

Utility is about whether the information is actually usable in its current form, like if you lose the decryption key to an encrypted drive the data is technically still there and available but its useless to you without the key

Possession is about controlling who physically holds or controls the data, if someone steals your backup drive you've lost possession of that data even if you still technically own it, same idea applies with ransomware where an attacker encrypts your data and you lose control over it even though its still sitting on your disk

## DAD Triad
Dad is basically the opposite of cia, disclosure alteration and destruction or denial

Disclosure is the opposite of confidentiality, like an attacker leaking medical records publicly. Alteration is the opposite of integrity, like an attacker modifying patient records which could lead to wrong treatment. Destruction or denial is the opposite of availability, like an attacker taking down a paperless medical facilitys database so records become completely inaccessible

Pushing confidentiality and integrity too hard can hurt availability and vice versa, so good security is really about finding a balance between all three rather than maximizing one at the cost of the others

## Security Models
Bell-lapadula model is focused on achieving confidentiality through three rules. Simple security property is no read up, meaning someone at a lower clearance cant read something at a higher clearance. Star security property is no write down, meaning someone at a higher clearance cant write down to a lower level, which would leak sensitive info to someone below their clearance. Discretionary security property uses an access matrix to define specific read and write permissions on top of the first two rules. All of this summarizes to write up read down, you can share info with people above you but only receive from people below you. Its limitation is it wasnt built with file sharing in mind

Biba model flips that idea around and focuses on integrity instead. Simple integrity property is no read down, a higher integrity subject shouldnt read from something lower integrity. Star integrity property is no write up, a lower integrity subject shouldnt write to something higher integrity. This summarizes to read up write down which is basically the opposite of bell lapadula, makes sense since one cares about confidentiality and the other about integrity. Its weak spot is it doesnt really handle insider threats well

Clark-wilson model also targets integrity but uses a different approach. It defines constrained data items which are the data you actually want to protect the integrity of, unconstrained data items which is everything else like raw user input, transformation procedures which are the operations like read and write that maintain integrity of the constrained data, and integrity verification procedures which check that the constrained data is actually still valid

## Defence in Depth
This is basically building security in layers instead of relying on one single barrier, also called multi level security. Think of it like a locked drawer inside a locked room inside a locked apartment inside a locked building with cameras watching too, no single layer stops everyone but stacking them together blocks most threats and slows down the rest

## Trust but Verify vs Zero Trust
Trust but verify means you still verify even when you trust something or someone, this usually means solid logging and periodically checking those logs since manually reviewing everything just isnt realistic, thats why automated tools like proxies and intrusion detection systems exist to help with this

Zero trust flips the whole idea and treats trust itself as a vulnerability, so instead of trusting something because its on the internal network or company owned, everything has to authenticate and get authorized before accessing any resource, basically never trust always verify. This limits the blast radius if a breach does happen. Microsegmentation is one way this gets implemented, where a network segment can literally be as small as a single host with strict controls on communication between segments

## Vulnerability, Threat, Risk
These three terms often get mixed up so its worth separating them clearly. Vulnerability is a weakness, like glass doors on a showroom being inherently fragile. Threat is the potential danger tied to that weakness, like the possibility of someone breaking the glass. Risk is about the likelihood of that threat actually being exploited and what impact it would have on the business, so if a hospitals database software turns out to have a known vulnerability with a working exploit already published, thats the point where you seriously have to weigh the risk and decide what to do next

## ISO/IEC 19249
This standard lists five architectural principles for building secure systems

- Domain separation — grouping related components together under their own domain with shared security attributes, like how os kernels run in a more privileged ring than regular user applications
- Layering — structuring a system into abstract layers so security policies can be applied and validated at each level individually, like how the osi model breaks networking into distinct layers each handling its own job
- Encapsulation — hiding low level implementation details and only exposing specific methods to interact with data, similar to oop where you provide a method instead of letting someone directly touch a variable
- Redundancy — building in backups so the system stays available and keeps its integrity even if one part fails, like a server with dual power supplies or a raid setup that survives a drive failure
- Virtualization — sharing one set of hardware across multiple systems, which also gives you sandboxing for safely observing or detonating potentially malicious programs

And five design principles

- Least privilege — giving someone only the exact permissions they need for their task and nothing extra
- Attack surface minimisation — reducing the number of exposed vulnerabilities by turning off anything not actually needed, like disabling unused services during hardening
- Centralized parameter validation — validating all input in one centralized place instead of scattering validation logic everywhere, since bad input is a common way systems get exploited
- Centralized general security services — keeping things like authentication centralized rather than scattered, while still being careful not to create a single point of failure
- Preparing for error and exception handling — designing systems to fail safely, like a firewall that blocks all traffic if it crashes instead of letting everything through, and making sure error messages dont accidentally leak sensitive info

## Shared Responsibility Model
With cloud services becoming so common, security responsibility gets split between the provider and the customer depending on the service type. An iaas user has full control and responsibility over their operating system, while a saas user has basically no access to the underlying os at all. This split means proper cloud security only works if both the provider and the customer handle their end of the responsibility