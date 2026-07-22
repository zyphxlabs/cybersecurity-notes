## What is a Windows Domain

A windows domain is basically when a business groups all their users and computers together and manages everything from one place through something called Active Directory. The server that runs all of this is called a Domain Controller and it's basically the brain of the whole setup. The two big reasons companies do this is so they can manage all users from one place and push security policies across every single computer without touching them one by one.

## Active Directory Objects

### Users

Users are security principals which means they can be authenticated and given privileges. There are two types really people like employees and services like IIS or MSSQL and service users only get the privileges they need to run their specific service nothing more.

### Machines

Every computer that joins the domain gets its own machine object created for it. Machine accounts are also security principals but with limited rights and the account name is always the computer name with a dollar sign at the end like DC01$. Passwords for these are auto rotated and are 120 random characters so nobody is manually managing them.

### Security Groups

Security groups are used to give access rights to a bunch of people at once instead of doing it one by one. Some important ones:

- Domain Admins — full admin over the entire domain including DCs
- Server Operators — can administer DCs but cannot change admin group memberships
- Backup Operators — can access any file regardless of permissions for backup purposes
- Account Operators — can create or modify accounts in the domain
- Domain Users — all existing user accounts
- Domain Computers — all existing computers
- Domain Controllers — all existing DCs

## Organisational Units

OUs are basically containers used to group users and machines that need similar policies applied to them. One important thing is a user can only be in one OU at a time which is different from security groups. The difference between OUs and security groups is that OUs are for applying policies while security groups are for granting permissions over resources.

Default containers that come with any domain:

- Builtin — default groups for any Windows host
- Computers — machines joining network go here by default
- Domain Controllers — default OU for DCs
- Users — default users and groups for domain wide context
- Managed Service Accounts — accounts used by services

## Machine Categories

Three types of machines exist in a domain:

- Workstations — regular user devices and no privileged users should ever sign into these
- Servers — provide services to users or other servers
- Domain Controllers — most sensitive ones because they contain hashed passwords for every account in the domain

## Group Policy Objects

GPOs are basically collections of settings you apply to OUs to control how computers and users behave. You create a GPO then link it to whatever OU you want and it applies to that OU and everything underneath it. The settings sync through a network share on the DC called SYSVOL and it can take up to 2 hours to apply but you can force it immediately with `gpupdate /force`.

## Delegation

Delegation is when you give a specific person control over certain OUs without making them a full Domain Admin. A common example is giving IT support the ability to reset passwords for regular users without touching anything else. The PowerShell commands for this are:

- `Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose` — resets the password
- `Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose` — forces password reset at next login

## Authentication Protocols

### Kerberos

Kerberos is the default authentication system in modern Windows and it works on tickets. User sends their username and an encrypted timestamp to the KDC which gives back a Ticket Granting Ticket and a Session Key. Then when the user wants to access a service they send that TGT along with the SPN to get a Ticket Granting Service ticket and that TGS is what actually gets them into the service.

Key terms to know:

- KDC — Key Distribution Center — runs on DC and creates the tickets
- TGT — Ticket Granting Ticket — proves you already authenticated
- TGS — Ticket Granting Service — grants access to a specific service
- SPN — Service Principal Name — identifies which service you want

### NetNTLM

NetNTLM is the older one kept around for compatibility and it works on a challenge response system. Server sends a random challenge to the client and the client combines their NTLM hash with that challenge and sends it back. The DC then recalculates it and checks if it matches. The good thing is the actual password or hash never travels over the network.

## Trees and Forests

A tree is when multiple domains share the same namespace joined together so thm.local could split into uk.thm.local and us.thm.local. A forest is when you take multiple trees with completely different namespaces and combine them into one network like thm.local and mht.local becoming one forest.

Trust relationships let users from one domain access resources in another. One way trust means domain AAA trusts BBB so BBB users can access AAA. Two way trust means both domains mutually authorise each other and this is created by default when joining a tree or forest. But trust does not automatically give access you still have to configure permissions separately.