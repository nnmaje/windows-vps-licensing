# Cheap VPS Windows: Is $3.99 a Month Real, What Does the Licence Add, and How Much RAM Do You Actually Need? (Full Plan Table, RDP Session Limits and Server End-of-Support Dates)

A Windows VPS that can run a real workload on a real licence costs roughly **$33 to $55 a month**. Anything advertised below $5 is either a 1 GB box that Windows cannot comfortably hold, or a 180-day evaluation licence with a shutdown date attached. Above that band you are paying for cores and memory, and that is where SpinServers sits: their KVM line starts at **$39 a month for 6 vCPU and 8 GB of RAM**, six times the memory of a typical $13 Windows plan for about three times the money.

The numbers below explain why the same phrase, Windows VPS, produces quotes that differ by a factor of ten. Three providers price the Windows licence in three different ways, one of them expires, and the cheapest advertised figure usually excludes it.

> **Quick pick:** one Windows application and one or two RDP users needs 4 GB of RAM and a licence, which lands near $33 to $55 all in. If you would rather have 8 GB and six cores for $39 a month and manage the OS yourself, SpinServers' entry KVM plan is the one worth pricing out. 👉 [Check the SpinServers KVM VPS plans and current pricing](https://bit.ly/Spinservers)

## SpinServers KVM VPS plans

| Plan | vCPU / RAM / Storage | Bandwidth and port | Price | Order |
| --- | --- | --- | --- | --- |
| KVM 6 vCPU 8 GB | 6 cores / 8 GB DDR4 / 120 GB RAID-10 SSD | 8 TB, 1 Gbps | **From $39.00/mo** | [View this plan](https://bit.ly/Spinservers) |
| KVM 8 vCPU 8 GB | 8 cores / 8 GB DDR4 / 160 GB RAID-10 SSD | 10 TB, 1 Gbps | Priced on the order page | [View this plan](https://bit.ly/Spinservers) |
| KVM 12 vCPU 12 GB | 12 cores / 12 GB DDR4 / 160 GB RAID-10 SSD | 10 TB, 1 Gbps | Priced on the order page | [View this plan](https://bit.ly/Spinservers) |
| KVM 16 vCPU 16 GB | 16 cores / 16 GB DDR4 / 320 GB RAID-10 SSD | 15 TB, 1 Gbps | Priced on the order page | [View this plan](https://bit.ly/Spinservers) |
| KVM 32 vCPU 32 GB | 32 cores / 32 GB RAM / 500 GB SSD | 20 TB, 1 Gbps | Priced on the order page | [View this plan](https://bit.ly/Spinservers) |

Every plan includes one IPv4 and one IPv6 address, full root access and a 1 Gbps port. Outbound port 25 is closed by default on all of their virtual servers; opening it requires a ticket and can be refused, which matters if you plan to send mail from the box rather than through a relay.

Only the 6 vCPU plan carries a published monthly figure on the plan listing. The larger configurations show specifications without a headline price, so treat the order page as the source of truth rather than any number you see quoted elsewhere.

One thing to confirm before paying: Windows licensing on the KVM VPS line is not stated on the plan listing. Their dedicated servers are documented with Linux, Windows and ESXi installs, so Windows is not foreign to the platform, but the VPS order form is where you check which Server version is offered and whether the licence is included in the monthly figure or added to it. That one line item can move the real cost by $20 a month.

## Why "from $3.99" is not the number that leaves your account

Three providers, three completely different ways of charging for the same Microsoft licence.

| Provider | Advertised entry price | What the Windows licence adds | Realistic all-in |
| --- | --- | --- | --- |
| MassiveGRID | $3.99/mo for a 1 GB Windows Server Starter | Free 180-day evaluation, or **$6.31 per vCPU** | $3.99 during the evaluation, then add per-core licensing |
| GigeNET | $35/mo for 2 cores, 4 GB, 90 GB SSD | **Flat $20.28/mo** Windows Server Standard on any plan | **$55.28/mo** |
| HostFinch | $12.99/mo for 1 vCPU, 2 GB, 40 GB SSD | **$19.99/mo** for Server 2019 or 2016 Standard at checkout | **$32.98/mo** |

Per-core, flat per server, and per-edition add-on are not interchangeable. A per-vCPU charge punishes big machines, because a flat fee that stays at $20.28 whether you buy 4 GB or 16 GB rewards them. Averaging the three into a single "typical licence cost" would give you a number that is wrong for every provider on the list.

GigeNET's own framing is the clearest example: they advertise $55.28 as the all-in price and show the arithmetic, $35 plan plus $20.28 licence, plus $0.0302 an hour for the licence if you bill hourly. HostFinch advertises $12.99 and lists the licence separately in the add-ons at checkout, so the $12.99 headline is a Linux-shaped number. Neither is dishonest. Both require you to read the second number.

SpinServers' $39 entry sits in a different bracket on purpose. Six cores and 8 GB is not a competitor to a $13 two-gigabyte box; it competes with GigeNET's 8-core, 8 GB Professional plan, which is **$90 plus $20.28, or $110.28 all in**. If the Windows licence on the SpinServers plan turns out to be included, the gap is large. If it is billed separately, do the addition before you decide. 👉 [See what the 6 vCPU, 8 GB plan costs today](https://bit.ly/Spinservers)

## What actually happens on day 181 of an evaluation licence

An evaluation licence is genuinely free, and it genuinely ends.

MassiveGRID spells out the mechanics. Every Windows Server template (2016, 2019, 2022, 2025) installs as a Microsoft evaluation edition with no licence cost, and you must activate it online within the first 10 days. It then runs at full functionality for 180 days with a counter on the desktop. After that the server keeps your data and installed software, but it shuts down once an hour and only accepts security updates until a licence is added. Adding the licence converts the installation in place, without a reinstall.

Read that shutdown behaviour against your workload. A trading terminal that needs to hold positions overnight, a scheduled bot, or an IIS site taking customer traffic cannot tolerate an hourly shutdown, and the fix is not a reboot. It is a purchase. The evaluation edition is a good fit for a migration window, a build agent, or a test box you will rebuild anyway. It is a bad fit for anything you would have to explain to a customer.

## 2 GB or 4 GB? Where Windows stops being theoretical

GigeNET enforces a 2 GB RAM and 20 GB disk minimum on the Windows order form and does not offer Windows on their 1 GB plan at all. Their recommendation is 4 GB or more, because updates, a browser and one real application together exceed 2 GB. For SQL Server or several concurrent RDP users, they point at 8 GB.

That lines up with what the rest of the market does. MassiveGRID's smallest Windows 11 Pro configuration is 1 vCPU, 2 GB and 32 GB of NVMe at $4.79, and they note that 2 GB is the floor the desktop edition needs to install. A 1 GB plan in a Windows VPS list is a Linux plan with a Windows logo attached to the marketing page.

Practical sizing:

- **One application, one or two people connecting over RDP:** 4 GB. Below that, Windows Update alone will make the desktop feel broken.
- **SQL Server Express, a busier IIS site, or three or more concurrent users:** 8 GB, and consider reserved cores rather than shared ones.
- **SQL Server Standard, ERP, or anything running at sustained CPU:** 16 GB and dedicated cores. Shared vCPU on a busy database produces the kind of latency that gets blamed on the host.

## The second and third RDP user cost money

Windows Server includes two administrative sessions at no extra charge. That covers a solo operator and a pair of colleagues. The third concurrent user is a licensing event.

MassiveGRID charges **$8.90 per extra user per month**. GigeNET charges **$7.50 a month per CAL, or $35 a month for a five-pack**. HostFinch asks you to contact them, which usually means a quote rather than a list price.

Do the arithmetic on a five-person team before you pick a plan, because it can double the bill. Five users on GigeNET's $35 plan means two free admin sessions plus three CALs: $35 + $20.28 + $22.50 = **$77.78 a month**. The same five people on a plan with 8 GB instead of 4 GB, once you add the CALs, starts to make the bigger plan look reasonable.

Desktop editions do not solve this. Windows 11 Pro allows a single interactive session, and Microsoft does not let hosting providers rent desktop Windows licences at all, so those templates install unactivated and run on a key you already own. Multi-user access means Windows Server plus CALs, full stop.

## Cheap old versions have a date stamped on them

Windows Server 2016 leaves security updates on **13 January 2027**. Windows Server 2019 follows on **10 January 2029**. Windows 10 Pro already stopped receiving security updates on 14 October 2025.

Version availability also varies by provider, which affects what "cheap" means. GigeNET offers only Server 2019 and 2016 Standard on its VPS line and steers you to 2019, with 2022 and 2025 available only on dedicated hardware. MassiveGRID makes Server 2025 the default for new servers and keeps 2016 through 2022 for software that has not been certified on newer releases. Contabo offers 2025, 2022, 2019 and 2016 images. A provider that only stocks 2016 is not offering you a discount; it is selling you a migration scheduled for the next few weeks.

## Choosing Windows is sometimes a one-way door

IONOS states plainly that if you order a Windows virtual server you cannot switch it to another operating system later. To run Linux you place a new order; the flexible-OS option is their Cloud Server line instead. GigeNET lets you switch between Windows and Linux from the client panel without a ticket, but the reinstall wipes the disk.

So the decision order matters. Check whether your stack actually needs Windows first. Classic ASP.NET and .NET Framework applications need IIS. Modern .NET runs on Linux as well, and if that is what you are deploying, paying a Windows licence is optional money. If you might want to move between the two, pick a provider where the operating system is a setting rather than an order.

## Contract length is the other hidden price

Contabo illustrates this better than anyone. Their Windows Server Cloud VPS 16 is listed at $120.10, with a figure of $111.20 shown "for the first 24 months", and Cloud VPS 18 at $151.20 with $139.44 on the same terms. Those are long-term contract prices, not first-month promotions. The saving is real, and so is the commitment: if you might move the workload in six months, an eighteen-month remainder is not a discount.

Ask two questions of any provider before paying: what does this cost in month thirteen, and what is the minimum term? A 24-month price quoted as a monthly price is the single most common way a cheap VPS turns out not to be cheap.

## Where SpinServers fits, and who should not buy it

SpinServers is a Texas-based infrastructure provider whose main business is bare-metal dedicated servers, starting at $79 a month with Linux, Windows and ESXi installs and provisioning in Dallas or San Jose. Their KVM VPS line carries that same hardware-first attitude: RAID-10 SSD storage, a 1 Gbps port, generous monthly bandwidth (8 TB on the entry plan, 20 TB at the top), full root access, and month-to-month billing with no setup fee. Third-party reviews note that month-to-month services there generally carry no refund policy, so a short trial before a long commitment is worth the planning.

The plans are sized for people who know what to do with eight cores: multiple RDP users on one box, a busy IIS or .NET deployment, build agents, automation that runs continuously, or a database that outgrew a shared plan. Self-managed means self-managed, so patching, firewall rules and RDP hardening are yours.

Two groups should look elsewhere. If you want the absolute lowest monthly figure for a single Windows desktop, a $12.99 plan plus a $19.99 licence is cheaper than $39. And if you want someone else to handle Windows updates and monitoring, a managed offering or a dedicated server with a support contract is the honest answer.

## How to decide

- **One Windows app, one or two RDP users, lowest total:** 4 GB RAM with a licence included. HostFinch at $32.98 all in, or GigeNET at $55.28 with hourly billing and US-based support.
- **Several apps or a small team, and you want memory for the money:** SpinServers' 6 vCPU, 8 GB plan at $39, after confirming the Windows licence line. 👉 [Start with the 6 vCPU, 8 GB configuration](https://bit.ly/Spinservers)
- **SQL Server, ERP, or five or more concurrent users:** 8–16 GB, reserved cores, Server 2019 or 2025, and budget the CALs into the total before you compare anything.
- **A migration, a build box, or a test rig:** the 180-day evaluation edition is legitimate and costs nothing. Just diarise day 170.

Before you enter card details, confirm two things: whether the Windows licence is inside the price you were shown or added at checkout, and what the price becomes after any introductory term ends. Everything else on this page is arithmetic; those two are the numbers that decide whether the cheap VPS was cheap.
