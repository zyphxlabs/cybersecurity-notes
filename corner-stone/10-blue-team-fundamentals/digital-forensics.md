## What is Digital Forensics
Forensics is basically applying methods and procedures to investigate and solve crimes, and digital forensics is the branch that focuses specifically on cyber crime, which is just any criminal activity done on or through a digital device. Its all about using proper tools and techniques to dig through digital devices after something happens and pull out actual usable evidence for legal action

Digital devices made life way easier but that same convenience opened the door to a whole new category of crime. Take a scenario like law enforcement raiding a suspects place with a proper warrant and finding a laptop phone hard drive and a usb. Once handed to a digital forensics team they collect everything securely and dig through it in a proper lab with the right tools. In a case like this you might find stuff like a digital map used to plan a robbery, a document mapping entrance and escape routes, another one listing out physical security controls and how to bypass them, media files from past robberies and even chat logs or call records tying back to the crime. All of that becomes actual evidence usable in legal proceedings, which is really the whole point of doing this properly

## The Four Phases (NIST Process)
Nist defines a general four phase process for handling digital forensics cases regardless of the specific tools involved

Collection is the first phase, basically identifying every device evidence could come from at a scene, things like computers laptops cameras and usbs. The big thing here is making sure the original data doesnt get tampered with while collecting it, and keeping proper documentation of everything thats gathered

Examination comes next since raw collected data can be massive and overwhelming. This phase is about filtering it down to whats actually relevant, like pulling only media from a specific date off a camera instead of dealing with everything on it, or isolating one specific users data off a system with a bunch of accounts on it

Analysis is where the real digging happens, correlating data across multiple pieces of evidence to actually draw conclusions. What this looks like depends heavily on the case and what data is even available, but the goal is building out a clear chronological picture of whats relevant

Reporting wraps it up with a detailed writeup covering the methodology used and the actual findings, sometimes with recommendations included too. This report goes to law enforcement and execs so it needs an executive summary that makes sense to people without a technical background too

## Types of Digital Forensics
Different categories of evidence need different tools and approaches entirely

- computer forensics — the most common type, focused on investigating computers since theyre the device most tied to criminal activity
- mobile forensics — digging into phones specifically, pulling stuff like call records texts and gps history
- network forensics — looks past individual devices at the whole network, mostly working with network traffic logs
- database forensics — investigating intrusions into databases that led to data being modified or straight up exfiltrated
- cloud forensics — investigating data sitting on cloud infrastructure, this one gets tricky since theres often way less evidence actually available compared to a physical device
- email forensics — looking into emails specifically to figure out if theyre tied to phishing or fraud campaigns

## Evidence Acquisition Best Practices
Collecting evidence properly is a big deal, it has to be done securely without touching or altering the original data in any way

Proper authorization has to be obtained before collecting anything, evidence grabbed without approval can just get thrown out as inadmissible in court. Since this data is often deeply private or sensitive, staying within legal limits matters a lot here

Chain of custody is basically a formal document tracking every detail about a piece of evidence so theres a clear trail of who touched what and when. Without this, if evidence goes missing or gets altered later theres literally no way to hold anyone accountable since theres no record proving who had it. Key stuff a chain of custody doc should include

- description of the evidence including name and type
- who actually collected it
- date and time it was collected
- where its being stored
- a record of every time its accessed and by who

This whole document is what proves the integrity of evidence when it actually gets presented in court

Write blockers are a core tool in the kit too. Say youre pulling evidence off a suspects hard drive by hooking it up to your forensic workstation, without a write blocker some background process on your own machine could end up altering file timestamps on that drive without you even meaning to, which messes up the analysis later. A write blocker physically prevents any write action from touching the original drive so it stays exactly as found the whole time

## Windows Forensic Imaging
Desktop and laptop systems are the most commonly collected evidence since most criminal activity involves a personal machine somewhere. For windows specifically, forensic images are taken as bit by bit copies of the whole system, and there are two main categories

Disk image captures everything on the actual storage device, hdd or ssd, this is non volatile data meaning it survives even after a restart, stuff like files documents and browsing history

Memory image captures whats sitting in ram at that moment, this is volatile so it disappears the second the system gets powered off or restarted. This is why memory should generally be captured first before anything else during an investigation, things like open files running processes and active network connections only live here and get wiped the moment the machine shuts down

## Tools for Disk and Memory Acquisition
A few well known tools come up constantly in windows forensics work

FTK Imager is widely used for taking disk images, comes with a solid gui for creating images in different formats and can also be used to actually analyze a disk image afterward, covers both acquisition and analysis

Autopsy is a popular open source platform you import an acquired disk image into for deeper analysis, gives you stuff like keyword search deleted file recovery metadata inspection and even extension mismatch detection to catch files disguised with the wrong extension

DumpIt is specifically for pulling memory images off a windows system, runs through a simple command line interface and can output the memory dump in a few different formats

Volatility is a powerful open source tool built specifically for analyzing memory images once youve got them, uses a plugin system where each artifact type gets its own dedicated plugin to dig through. Works across windows linux macos and android which makes it pretty versatile across different case types

## Reading File Metadata
Every file carries some level of metadata just from being created or edited. A basic txt file only holds simple stuff like creation and modification dates from the os, but something edited in a heavier program like word carries way more embedded info. Even converting a doc to pdf usually keeps most of that original metadata intact depending on what pdf writer was used

pdfinfo is a solid tool for pulling this straight out of a pdf, showing stuff like

```
pdfinfo document.pdf
```

This can show you the creator and producer software, creation and modification dates, page count, whether its encrypted, and more. In a case i worked through the metadata clearly pointed back to it being created in word for office 365 on a specific date, which is honestly a pretty simple but powerful lead just sitting there in the file properties nobody thinks to check

## Photo EXIF Data
Exif stands for exchangeable image file format, its basically the metadata standard baked into photos. Every time you snap a picture on a phone or digital camera a bunch of info gets embedded automatically, stuff like

- camera or phone model
- exact date and time the photo was taken
- camera settings like focal length aperture shutter speed and iso

Since most phones have gps built in, theres a good chance exif data also includes actual coordinates showing exactly where a photo was taken. Exiftool is the go to command line tool for pulling all this out of an image

```
exiftool image.jpg
```

Running this against a photo can spit out a gps position field with actual latitude and longitude values. Dropping those coordinates into something like google maps or bing maps reveals the literal street the photo was taken on. Worth noting when typing coordinates into a map search you gotta swap deg for the actual ° symbol and clean up extra spacing for it to actually resolve properly, its a small formatting thing but it trips people up if they just copy paste the raw exif output straight in