# 🔍 OSINT Resources & Methodology

> A curated reference for Open Source Intelligence (OSINT) gathering — organised by category for red team assessments, penetration testing, and investigations.

---

## Table of Contents

- [Methodology Overview](#methodology-overview)
- [Anonymity & Operational Security](#anonymity--operational-security)
- [Sock Puppets & Personas](#sock-puppets--personas)
- [Search Engines & Dorking](#search-engines--dorking)
- [People & Identity](#people--identity)
- [Email Enumeration](#email-enumeration)
- [Username & Account Discovery](#username--account-discovery)
- [Phone Numbers](#phone-numbers)
- [Social Media](#social-media)
- [Image & Facial Recognition](#image--facial-recognition)
- [Geolocation & Maps](#geolocation--maps)
- [Company & Business Intelligence](#company--business-intelligence)
- [Domain, IP & Network Intelligence](#domain-ip--network-intelligence)
- [IoT & Cameras](#iot--cameras)
- [Physical Reconnaissance](#physical-reconnaissance)
- [Vehicle & Transport](#vehicle--transport)
- [Dark Web & Breach Data](#dark-web--breach-data)
- [Radio & Wireless](#radio--wireless)
- [Passwords & Wordlists](#passwords--wordlists)
- [OSINT Platforms & Case Management](#osint-platforms--case-management)
- [Training & Practice](#training--practice)
- [Reporting](#reporting)

---

## Methodology Overview

A structured OSINT engagement typically covers two core target surfaces:

**Target Location Intelligence**
Gather physical and structural information about a location. Sources include satellite imagery, drone footage, building plans, Airbnb listings, and street-level photography. Look for: access control points, perimeter fencing, guard positions, smoking/break areas (tailgating vectors), signage, badge designs, and uniform styles.

**Target People / Employee Intelligence**
Gather details about personnel: names, roles, email patterns, phone numbers, managers, and social media presence. Look for photos of access badges, desks, screens, and internal information inadvertently posted online.

---

## Anonymity & Operational Security

Before conducting any investigation, protect your identity and attribution.

| Tool | Description |
|------|-------------|
| [Tor Project](https://www.torproject.org/) | Anonymise browsing via onion routing |
| [Mullvad VPN](https://mullvad.net/) | Privacy-first VPN with no-log policy |
| [Private Internet Access](https://www.privateinternetaccess.com/) | VPN with restriction-free browsing |
| [Startpage](https://www.startpage.com/) | Private search engine (Google results, no tracking) |
| [DuckDuckGo](https://duckduckgo.com/) | Private search engine |
| [Cover Your Tracks (EFF)](https://coveryourtracks.eff.org/) | Test your browser fingerprint |
| [Tails OS](https://tails.boum.org/) | Amnesic OS for anonymous investigation |
| [Whonix](https://www.whonix.org/) | Privacy-hardened OS for advanced opsec |

**Kali Linux OSINT modules:** `/opt/ptf/modules/intelligence-gathering/`

---

## Sock Puppets & Personas

A sock puppet is a fake online identity used to gather intelligence without attribution to the investigator. It must not be linked to your real phone number, IP address, or identity.

| Resource | Description |
|----------|-------------|
| [This Person Does Not Exist](https://www.thispersondoesnotexist.com/) | AI-generated face for persona photo |
| [Fake Name Generator](https://www.fakenamegenerator.com/) | Full synthetic identity details |
| [Ultimate Guide to Sockpuppets (OSINT Team)](https://osintteam.blog/the-ultimate-guide-to-sockpuppets-in-osint-how-to-create-and-utilize-them-effectively-d088c2ed6e36) | Methodology guide |
| [How to Create a Sock Puppet (Medium)](https://medium.com/@lochana8723/how-to-create-a-perfect-sock-puppet-for-osint-investigations-739c5a13e5cf) | Step-by-step walkthrough |
| [Proton Mail](https://proton.me/) | Anonymous email for persona registration |
| [MySudo](https://mysudo.com/) | Compartmentalised phone/email personas |

---

## Search Engines & Dorking

### General Search Engines

| Engine | URL |
|--------|-----|
| Google | [google.com/advanced_search](https://www.google.com/advanced_search) |
| Bing | [bing.com](https://www.bing.com/) |
| Yandex | [yandex.com](https://yandex.com/) |
| DuckDuckGo | [duckduckgo.com](https://duckduckgo.com/) |
| Baidu | [baidu.com](http://www.baidu.com/) |
| Startpage | [startpage.com](https://www.startpage.com/) |

### Google Dorking / Search Operators

| Resource | Description |
|----------|-------------|
| [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database) | Exploit-DB's collection of Google dorks |
| [Ahrefs Advanced Search Operators](https://ahrefs.com/blog/google-advanced-search-operators/) | Comprehensive operator reference |
| [Google Advanced Search Guide (PDF)](http://www.googleguide.com/print/adv_op_ref.pdf) | Printable reference |
| [Bing & Google Operators (Bruce Clay)](https://www.bruceclay.com/blog/bing-google-advanced-search-operators/) | Cross-engine comparison |
| [DuckDuckGo Syntax](https://help.duckduckgo.com/duckduckgo-help-pages/results/syntax/) | DDG-specific operators |
| [OSINTcurious Dorks Page](https://osintcurio.us/2019/12/20/google-dorks/) | Curated dork examples |

**Common dork patterns:**
```
filetype:pdf site:target.com
intitle:"index of" "password"
inurl:login site:target.com
"@target.com" filetype:xls
site:linkedin.com/in "target company"
```

### Specialist Search Engines

| Tool | Description |
|------|-------------|
| [Censys](https://search.censys.io/) | Internet-wide host and certificate scanning |
| [Shodan](https://www.shodan.io/) | Search engine for internet-connected devices |
| [GreyNoise](https://www.greynoise.io/) | Distinguish targeted attacks from internet noise |
| [ZoomEye](https://www.zoomeye.org/) | Chinese equivalent of Shodan |
| [PublicWWW](https://publicwww.com/) | Search inside website source code |
| [CRDF Threat Center](https://threatcenter.crdf.fr/) | IoC lookup — IP and domain correlation over time |
| [Cobwebs](https://cobwebs.com/) | WEBINT platform |
| [DarkOwl](https://www.darkowl.com/) | Dark web search engine |

---

## People & Identity

### People Search Engines

| Tool | Free/Paid | Notes |
|------|-----------|-------|
| [TruePeopleSearch](https://www.truepeoplesearch.com/) | Free | US-focused |
| [FastPeopleSearch](https://www.fastpeoplesearch.com/) | Free | US-focused |
| [ThatsThem](https://thatsthem.com/) | Free | Phone, email, address lookup |
| [PeekYou](https://peekyou.com/) | Free | Social media cross-reference |
| [WebMii](https://webmii.com/) | Free | Aggregated web presence |
| [411.com](https://www.411.com/) | Free | US phone/address directory |
| [TruthFinder](https://www.truthfinder.com/) | Paid | Background reports |
| [WhitePages](https://www.whitepages.com/) | Paid | US directory |
| [FastBackgroundCheck](https://www.fastbackgroundcheck.com/) | Paid | Background records |

### Family & Relationships

| Tool | Description |
|------|-------------|
| [FamilyTreeNow](https://familytreenow.com/) | Public family tree records |
| [Ancestry](https://www.ancestry.com/) | Genealogy and historical records |
| [MyHeritage](https://www.myheritage.com/) | Family tree + facial recognition |

### Voter Records

| Tool | Description |
|------|-------------|
| [VoterRecords.com](https://www.voterrecords.com/) | US voter registration lookup |
| [Electoral Commission of South Africa](https://www.elections.org.za/pw/Voter/Voter-Information) | SA voter information |

---

## Email Enumeration

### Discovering Email Addresses

| Tool | Description |
|------|-------------|
| [Hunter.io](https://hunter.io/) | Find and verify email addresses by domain |
| [Phonebook.cz](https://phonebook.cz/) | Lists domains, emails, and URLs for a given domain |
| [Voila Norbert](https://www.voilanorbert.com/) | Email finder |
| [Clearbit Connect](https://clearbit.com/resources/tools/connect) | Gmail plugin for email discovery |
| [theHarvester](https://github.com/laramies/theHarvester) | CLI tool: names, emails, IPs, subdomains, URLs |
| [Bluto](https://github.com/darryllane/Bluto) | DNS recon, email/staff enumeration, metadata harvesting |
| [GatherContacts](https://github.com/clr2of8/GatherContacts) | LinkedIn contact harvesting |

```bash
# theHarvester example
theHarvester -d target.com -b all
```

### Validating Email Addresses

| Tool | Description |
|------|-------------|
| [EmailHippo](https://www.emailhippo.com/) | Real-time email verification |
| [Email-Checker.net](https://email-checker.net/) | Simple validity check |
| [Valid Email Scanner](https://github.com/0xhav0c/valid-email-scanner) | CLI bulk validation |
| [HaveIBeenPwned](https://haveibeenpwned.com/) | Check if address appears in data breaches |
| [DeHashed](https://dehashed.com/) | Search breached credentials by email/username |

**Tips:**
- Identify the company's email format pattern (e.g. `firstname.lastname@company.com`)
- Use the "Forgot Password" function to confirm if an email exists on a platform
- Check MX records and SMTP responses for validation clues

---

## Username & Account Discovery

| Tool | Description |
|------|-------------|
| [Sherlock](https://sherlock-project.github.io/) | Search 300+ platforms by username (Python CLI) |
| [WhatsMyName](https://whatsmyname.app/) | Username enumeration across platforms |
| [Namechk](https://namechk.com/) | Check username availability across platforms |
| [NameCheckup](https://namecheckup.com/) | Cross-platform username search |
| [IntelX](https://intelx.io/) | Search leaked data, paste sites, dark web |
| [Maltego](https://www.maltego.com/) | Graph-based OSINT link analysis |

```bash
# Sherlock CLI
python3 sherlock username
```

---

## Phone Numbers

| Tool | Description |
|------|-------------|
| [PhoneInfoga](https://github.com/sundowndev/phoneinfoga) | Advanced phone number OSINT framework |
| [Truecaller](https://www.truecaller.com/) | Caller ID and number lookup |
| [NumVerify](https://numverify.com/) | International number validation API |
| [CallerIDTest](https://calleridtest.com/) | Caller ID testing |
| [Infobel](https://www.infobel.com/) | Global telephone directory |
| [Broadcastify](https://www.broadcastify.com/) | Live radio streams for public safety comms |

```bash
# PhoneInfoga
phoneinfoga scan -n +27821234567
phoneinfoga serve -p 8080
```

---

## Social Media

### Platform-Specific Tools

**Twitter / X**
- [Advanced Search](https://twitter.com/search-advanced) — filter by user, geo, date
- Operators: `from:user`, `to:user`, `geocode:lat,lng,radius`
- [OSINT Twitter Tools](https://github.com/rmdir-rp/OSINT-twitter-tools)
- [WhoTwi](https://en.whotwi.com/) — graphical Twitter profile analysis

**Facebook**
- [IntelX Facebook Tools](https://intelx.io/tools?tab=facebook)
- [SowSearch](https://sowsearch.info/) — Facebook search
- Search for photos *of* the target (not just *by* the target)

**Instagram**
- [Imginn](https://imginn.com/) — anonymous Instagram viewer
- [InstaDP](https://instadp.io/) — full-size profile picture downloader
- [Osintgram](https://github.com/Datalux/Osintgram) — Instagram OSINT CLI tool
- Tip: right-click → "View page source" → search `profilePage_` for the persistent profile ID

**LinkedIn**
- [Signal Hire](https://www.signalhire.com/) — extract emails, phones, and social profiles
- Job listings reveal: tech stack, office locations, team structures, key contacts

**Snapchat**
- [Snap Map](https://map.snapchat.com/) — public location heatmap

**Cross-Platform**
| Tool | Description |
|------|-------------|
| [Sherlock](https://sherlock-project.github.io/) | Username search across 300+ platforms |
| [WhatsMyName](https://whatsmyname.app/) | Username enumeration |
| [Social Searcher](https://www.social-searcher.com/) | Real-time social media monitoring |
| [Echosec](https://www.echosec.net/) | Real-time geo-tagged social media intelligence |
| [Skopenow](https://www.skopenow.com/) | Automated social media investigation |

---

## Image & Facial Recognition

### Reverse Image Search

| Tool | Description |
|------|-------------|
| [Google Images](https://images.google.com/) | Standard reverse image search |
| [Yandex Images](https://yandex.com/images/) | Often superior for face matching |
| [TinEye](https://tineye.com/) | Exact image match tracking |
| [Bing Visual Search](https://www.bing.com/visualsearch) | Microsoft reverse image |
| [RevEye](https://chrome.google.com/webstore/detail/reveye-reverse-image-sear/keaaclcjhehbbapnphnmpiklalfhelgf) | Browser extension: searches all engines at once |
| [Karma Decay](https://karmadecay.com/) | Reddit-specific reverse image search |

### Facial Recognition

| Tool | Description |
|------|-------------|
| [PimEyes](https://pimeyes.com/) | Advanced face recognition across public web |
| [Search4Faces](https://search4faces.com/) | Face search across VKontakte and Odnoklassniki |
| [FaceCheck.ID](https://facecheck.id/) | Face-to-profile reverse search |

**Tips:**
- Try multiple engines — Yandex consistently outperforms others for face matching
- Right-click → "View image source" to reveal the original URL and metadata

### EXIF Data

EXIF metadata in images can reveal: camera model, GPS coordinates, date/time, and device info.

| Tool | Description |
|------|-------------|
| [Jimpl](https://jimpl.com/) | Web-based EXIF viewer |
| [Jeffrey's Exif Viewer](http://exif.regex.info/exif.cgi) | Detailed EXIF parsing |
| ExifTool (CLI) | Industry-standard local tool |

```bash
exiftool image.jpg
exiftool -gps:all image.jpg   # GPS data only
exiftool -r /directory/       # Recursive scan
```

---

## Geolocation & Maps

### Mapping Tools

| Tool | Description |
|------|-------------|
| [Google Earth](https://earth.google.com/) | Satellite and 3D terrain |
| [Snap Map](https://map.snapchat.com/) | Social media activity heatmap |
| [Wigle.net](https://wigle.net/) | Global Wi-Fi network mapping |
| [Descartes Labs](https://search.descarteslabs.com/) | Satellite imagery search |
| [HERE Maps](https://wego.here.com/) | Alternative mapping platform |
| [Fatmap](https://fatmap.com/) | 3D terrain and outdoor maps |
| [OpenStreetMap](https://www.openstreetmap.org/) | Open-source mapping data |

### Geolocation Analysis

| Tool | Description |
|------|-------------|
| [GeoGuessr](https://www.geoguessr.com/) | Train location identification skills |
| [GeoGuessr Tips & Techniques](https://somerandomstuff1.wordpress.com/2019/02/08/geoguessr-the-top-tips-tricks-and-techniques/) | Methodology guide |
| [SunCalc](https://www.suncalc.org/) | Calculate shadow direction/sun position from a photo |
| [Overpass Turbo](https://overpass-turbo.eu/) | Query OpenStreetMap data |

**Visual geolocation checklist:** parking layouts, door/window styles, signage fonts, vegetation, road markings, utility infrastructure, licence plates, building materials.

---

## Company & Business Intelligence

| Tool | Description |
|------|-------------|
| [OpenCorporates](https://opencorporates.com/) | World's largest open company database |
| [Companies House (UK)](https://find-and-update.company-information.service.gov.uk/) | UK company registrations and filings |
| [CIPC (South Africa)](https://www.cipc.co.za/) | SA company registration lookup |
| [AIHitData](https://www.aihitdata.com/) | Company data aggregator |
| [LinkedIn](https://www.linkedin.com/) | Employees, org structure, job postings |
| [Wayback Machine](https://web.archive.org/) | Historical snapshots of company websites |
| [BuiltWith](https://builtwith.com/) | Identify a site's tech stack |
| [Crunchbase](https://www.crunchbase.com/) | Startup funding and leadership data |

**Key intelligence from job postings:** office addresses, tech stack, security software in use, team structure, key hiring managers.

**Target information to collect:** address, key personnel, website infrastructure, imagery, dress code, badge design, entry/exit points.

---

## Domain, IP & Network Intelligence

| Tool | Description |
|------|-------------|
| [theHarvester](https://github.com/laramies/theHarvester) | Email, subdomain, IP, URL harvesting |
| [Shodan](https://www.shodan.io/) | Internet-connected device search |
| [Censys](https://search.censys.io/) | Certificate and host scanning |
| [GreyNoise](https://www.greynoise.io/) | IP classification and threat context |
| [Phonebook.cz](https://phonebook.cz/) | Domain → email/URL enumeration |
| [DNSDumpster](https://dnsdumpster.com/) | DNS recon and visualisation |
| [SecurityTrails](https://securitytrails.com/) | DNS history, subdomain enumeration |
| [Whois Lookup](https://whois.domaintools.com/) | Domain registration details |
| [ViewDNS](https://viewdns.info/) | Reverse IP, DNS records, WHOIS |
| [crt.sh](https://crt.sh/) | Certificate transparency log search |
| [Netcraft](https://sitereport.netcraft.com/) | Site report including hosting and tech stack |
| [SiteCheck (Sucuri)](https://sitecheck.sucuri.net/) | Malware and security check |
| [SEO Site Checkup](https://seositecheckup.com/tools) | Website analysis tools |
| [Bluto](https://github.com/darryllane/Bluto) | DNS recon, zone transfer, email enumeration |

```bash
# theHarvester
theHarvester -d target.com -b google,linkedin,shodan

# Nmap basic recon
nmap -sV -sC -A target.com
```

---

## IoT & Cameras

| Tool | Description |
|------|-------------|
| [Shodan](https://www.shodan.io/) | Find exposed cameras, routers, ICS |
| [IPVM](https://ipvm.com/) | Video surveillance intelligence |
| [Insecam](http://www.insecam.org/) | Index of open IP cameras |
| [Censys](https://search.censys.io/) | Internet-wide device scanning |

**Shodan camera dorks:**
```
product:"webcam" country:"ZA"
title:"Network Camera" has_screenshot:true
port:554 has_screenshot:true
```

---

## Physical Reconnaissance

**Sources for physical target intelligence:**
- Satellite imagery (Google Earth, Bing Maps)
- Drone footage and aerial photography
- Local government building plans / council archives
- Airbnb listings (interior photos of target area or adjacent buildings)
- Street View (Google, Apple Maps)
- Real estate listings (Zillow, Property24, Private Property)

**What to look for:**
- Access control systems (keypads, card readers, turnstiles)
- Perimeter fencing types and height
- Guard positions and patrol patterns
- Smoking/break areas (tailgating entry points)
- Badge and uniform designs on employee social media
- Desk setups, screens, and whiteboards visible in photos

---

## Vehicle & Transport

| Tool | Description |
|------|-------------|
| [FirstCheck ZA](https://www.firstcheck.co.za/) | SA vehicle registration check |
| [VehicleCheck ZA](https://www.vehiclecheck.co.za/) | SA vehicle history and registration |
| [FlightRadar24](https://www.flightradar24.com/) | Live aircraft tracking |
| [ADS-B Exchange](https://www.adsbexchange.com/) | Unfiltered aircraft tracking (no government filtering) |
| [MarineTraffic](https://www.marinetraffic.com/) | Real-time vessel tracking |
| [OpenSky Network](https://opensky-network.org/) | Free aircraft position data |

---

## Dark Web & Breach Data

| Tool | Description |
|------|-------------|
| [HaveIBeenPwned](https://haveibeenpwned.com/) | Email breach check |
| [DeHashed](https://dehashed.com/) | Breach data search (credentials, usernames, IPs) |
| [IntelX](https://intelx.io/) | Dark web, paste, and breach search |
| [Leak-Lookup](https://leak-lookup.com/) | Credential leak search |
| [BreachDirectory](https://breachdirectory.org/) | Free breach lookup |
| [Tor Browser](https://www.torproject.org/) | Dark web access |
| [DarkOwl](https://www.darkowl.com/) | Dark web monitoring platform |
| [Ahmia](https://ahmia.fi/) | Tor hidden service search engine |

---

## Radio & Wireless

| Tool | Description |
|------|-------------|
| [Wigle.net](https://wigle.net/) | Global Wi-Fi and cellular network map |
| [Broadcastify](https://www.broadcastify.com/) | Live public safety radio streams |
| [RTL-SDR](https://www.rtl-sdr.com/) | Software-defined radio for signal interception |
| [RadioReference](https://www.radioreference.com/) | Frequency database and scanner tools |

---

## Passwords & Wordlists

| Resource | Description |
|----------|-------------|
| [RockYou2021](https://github.com/ohmybahgosh/RockYou2021.txt) | Massive combined password wordlist |
| [SecLists](https://github.com/danielmiessler/SecLists) | The definitive collection of wordlists for security testing |
| [Password Cracking Rules](https://github.com/NotSoSecure/password_cracking_rules) | Hashcat/John rule sets |
| [CrackStation](https://crackstation.net/) | Online hash cracking and lookup |
| [Weakpass](https://weakpass.com/) | Wordlist aggregator and generator |

**Techniques:** Password spraying with Burp Suite, credential stuffing, rule-based mutation.

---

## OSINT Platforms & Case Management

| Tool | Description |
|------|-------------|
| [Maltego](https://www.maltego.com/) | Graph-based link analysis and automation |
| [Hunchly](https://hunch.ly/) | Automated web capture and case management |
| [SpiderFoot](https://www.spiderfoot.net/) | Automated OSINT collection framework |
| [Recon-ng](https://github.com/lanmaster53/recon-ng) | Modular web reconnaissance framework |
| [OSINT Framework](https://osintframework.com/) | Categorised tool navigator |
| [NexusXplore](https://www.nexusxplore.com/) | Enterprise OSINT platform |
| [Shadowdragon](https://shadowdragon.io/) | OSINT data discovery and monitoring |
| [OSINT Combine](https://www.osintcombine.com/) | OSINT training and tools |
| [OpenProject](https://www.openproject.org/) | Open-source project/case management |
| [Awesome OSINT (GitHub)](https://github.com/Astrosp/Awesome-OSINT-For-Everything) | Curated mega-list of OSINT tools |

---

## Training & Practice

| Resource | Description |
|----------|-------------|
| [OSINT Dojo](https://www.osintdojo.com/) | Structured OSINT skill challenges |
| [Investigator (CyberSoc Wales)](https://investigator.cybersoc.wales/) | OSINT CTF challenges |
| [TraceLabs](https://www.tracelabs.org/) | Crowd-sourced OSINT for missing persons |
| [Bellingcat Online Investigation Toolkit](https://docs.google.com/spreadsheets/d/18rtqh8EG2q1xBo2cLNyhIDuK9jrPGwYr9DI2UncoqJQ) | Bellingcat's curated OSINT toolkit |
| [GeoGuessr Daily Challenges](https://www.geoguessr.com/daily-challenges) | Geolocation skill building |
| [A Google a Day](http://www.agoogleaday.com/) | Search skill building |
| [Quiztime (Twitter)](https://twitter.com/quiztime) | Geolocation puzzle community |
| [r/whatisthisthing](https://www.reddit.com/r/whatisthisthing/) | Crowd-sourced identification |
| [TCM Security OSINT Course](https://academy.tcm-sec.com/) | Practical OSINT training |
| [OSINT Curious](https://osintcurio.us/) | Blog, tools, and podcast |

---

## Reporting

A good OSINT report should include:

1. **Executive Summary** — key findings in plain language
2. **Scope & Methodology** — what was investigated and how
3. **Target Profile** — compiled identity/entity intelligence
4. **Findings by Category** — organised evidence with screenshots and source citations
5. **Risk Assessment** — what an adversary could do with this information
6. **Recommendations** — how the target can reduce their OSINT exposure

**Tools for documentation:**
- [Hunchly](https://hunch.ly/) — automated capture with timestamped evidence
- [CherryTree](https://www.giuspen.com/cherrytree/) — hierarchical note-taking for investigations
- [Obsidian](https://obsidian.md/) — linked markdown notes for case building
- Screenshots with metadata stripped before submission

---

*Maintained for red team and penetration testing use. Always operate within legal and ethical boundaries, with written authorisation from the target organisation.*
