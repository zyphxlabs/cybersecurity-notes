\# Active Directory Basics

\---



\## What is a Windows Domain

A group of users and computers under the administration of a business.

Centralises management through Active Directory (AD).

The server running AD services is called a Domain Controller (DC).



\*\*Two main advantages:\*\*

\- Centralised identity management — configure all users from one place

\- Managing security policies — deploy policies across all computers from AD



\---



\## Active Directory Objects



\### Users

\- Security principals — can be authenticated and assigned privileges

\- Two types: People (employees) and Services (IIS, MSSQL etc)

\- Service users only have privileges needed to run their specific service



\### Machines

\- Every computer joining the domain gets a machine object created

\- Machine accounts are security principals with limited domain rights

\- Machine account name = computer name + $ sign (example: DC01$)

\- Passwords are auto-rotated — 120 random characters



\### Security Groups

Used to assign access rights to resources for entire groups instead of single users.



| Group | Description |

|-------|-------------|

| Domain Admins | Full admin over entire domain including DCs |

| Server Operators | Can administer DCs but cannot change admin group memberships |

| Backup Operators | Can access any file regardless of permissions — for backups |

| Account Operators | Can create or modify accounts in the domain |

| Domain Users | All existing user accounts |

| Domain Computers | All existing computers |

| Domain Controllers | All existing DCs |



\---



\## Organisational Units (OUs)

Container objects used to classify users and machines.

Used to define sets of users with similar policy requirements.

A user can only be in ONE OU at a time.



\*\*Default containers:\*\*

\- Builtin — default groups for any Windows host

\- Computers — machines joining network go here by default

\- Domain Controllers — default OU for DCs

\- Users — default users and groups for domain-wide context

\- Managed Service Accounts — accounts used by services



\*\*OUs vs Security Groups:\*\*

\- OUs — for applying policies to users and computers

\- Security Groups — for granting permissions over resources

\- A user can be in many security groups but only one OU



\---



\## Machine Categories

| Category | Description |

|----------|-------------|

| Workstations | Regular user devices — no privileged users should sign in |

| Servers | Provide services to users or other servers |

| Domain Controllers | Most sensitive — contain hashed passwords for all accounts |



\---



\## Group Policy Objects (GPOs)

Collection of settings applied to OUs.

Managed via Group Policy Management tool.



\*\*How GPOs work:\*\*

\- Create GPO under Group Policy Objects

\- Link it to the OU where you want policies applied

\- GPO applies to linked OU and all sub-OUs under it

\- Synced via SYSVOL network share on DC

\- Takes up to 2 hours to apply — force with `gpupdate /force`



\*\*Example GPOs created in room:\*\*

\- Restrict Control Panel Access — linked to Marketing, Sales, Management OUs

\- Auto Lock Screen (5 min inactivity) — linked to root domain



\---



\## Delegation

Giving specific users control over certain OUs without making them Domain Admin.



Common use case — giving IT support ability to reset passwords for low-privilege users.



\*\*PowerShell command to reset a password:\*\*

```powershell

Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

```



\*\*Force password reset at next login:\*\*

```powershell

Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

```



\---



\## Authentication Protocols



\### Kerberos (Default — Modern Windows)

Ticket-based authentication system.



\*\*Process:\*\*

1\. User sends username + encrypted timestamp to KDC

2\. KDC returns Ticket Granting Ticket (TGT) + Session Key

3\. User sends TGT + SPN to KDC to request Ticket Granting Service (TGS)

4\. KDC returns TGS + Service Session Key

5\. User sends TGS to service — connection established



\*\*Key terms:\*\*

\- KDC — Key Distribution Center — runs on DC — creates tickets

\- TGT — Ticket Granting Ticket — proves you authenticated

\- TGS — Ticket Granting Service — grants access to specific service

\- SPN — Service Principal Name — identifies the service you want



\### NetNTLM (Legacy — kept for compatibility)

Challenge-response mechanism.



\*\*Process:\*\*

1\. Client sends authentication request to server

2\. Server sends random challenge to client

3\. Client combines NTLM hash + challenge and sends response

4\. Server forwards challenge + response to DC

5\. DC recalculates and compares response

6\. Result sent back to client



Password or hash is never transmitted over network.



\---



\## Trees and Forests



\### Trees

Multiple domains sharing the same namespace joined together.

Example: thm.local splits into uk.thm.local and us.thm.local



\### Forests

Union of several trees with different namespaces into one network.

Example: thm.local tree + mht.local tree = one forest



\### Trust Relationships

Allow users from one domain to access resources in another.



\- \*\*One-way trust\*\* — Domain AAA trusts BBB — users on BBB can access AAA

\- \*\*Two-way trust\*\* — both domains mutually authorise each other

\- Joining domains in a tree or forest creates two-way trust by default

\- Trust does not automatically grant access — still must be configured



\---



\## Key Commands

| Command | What it does |

|---------|-------------|

| `gpupdate /force` | Forces immediate GPO sync on a computer |

| `lusrmgr.msc` | Local Users and Groups |

| `Set-ADAccountPassword` | Reset AD user password via PowerShell |

| `Set-ADUser` | Modify AD user properties via PowerShell |

