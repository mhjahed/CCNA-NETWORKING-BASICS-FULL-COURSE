```
███╗   ██╗███████╗████████╗██████╗  █████╗ ███████╗██╗ ██████╗███████╗
████╗  ██║██╔════╝╚══██╔══╝██╔══██╗██╔══██╗██╔════╝██║██╔════╝██╔════╝
██╔██╗ ██║█████╗     ██║   ██████╔╝███████║███████╗██║██║     ███████╗
██║╚██╗██║██╔══╝     ██║   ██╔══██╗██╔══██║╚════██║██║██║     ╚════██║
██║ ╚████║███████╗   ██║   ██████╔╝██║  ██║███████║██║╚██████╗███████║
╚═╝  ╚═══╝╚══════╝   ╚═╝   ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝ ╚═════╝╚══════╝
              ░░▄▄▄░░  P R A C T I C E   S T U D I O  ░░▄▄▄░░
```

```bash
jahed@netbasics:~$ fastfetch
────────────────────────────────────────────────────────────────
  course       NetCad Academy — Networking Basics
  knowledge    91 · MASTERED   (official knowledge check, 02 Aug 2026)
  weak ifaces  m13 (Address Resolution) · m5 (Communication Principles)
  stack        HTML + CSS + vanilla JS  →  deps: none · build: none · backend: none
  runs on      file://, http://, literally anything that serves bytes
────────────────────────────────────────────────────────────────
```

A front-end-only practice studio that turns a **completed** Networking Basics course into hands-on reps.
Built from the learner's own downloaded course files, so every IP, MAC, password and lab objective on
the site matches the material already studied — no generic textbook filler.

The loop is simple: **Read → Do → Verify.**
Read a condensed study guide, redo the Packet Tracer labs *in the browser*, then re-test yourself with
a quiz scored on the same bands as the official knowledge check. The dashboard tracks the real result
(91 · Mastered) and routes practice time toward the two non-Mastered modules first.

---

```bash
jahed@netbasics:~$ whoami --verbose
```

| field     | value |
|---|---|
| operator  | **Jahed SA** |
| origin    | NetCad Academy — Networking Basics, completed |
| result    | 91 · **Mastered** (02 Aug 2026) |
| motive    | a finished course fades; a practised one doesn't |
| interface | any modern browser, light theme |

---

```bash
jahed@netbasics:~$ ping -c2 studio.local        # quick start — nothing to install, nothing to build
```

**Option A — open directly (0% packet loss):**

Double-click `index.html`. The site uses **no `fetch()` and no JS modules**, so it runs straight off the
file system.

**Option B — serve it (recommended):**

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Any static server works: `npx serve`, `php -S localhost:8000`, …

> Poppins is loaded from Google Fonts. Offline, the site silently falls back to the system
> sans-serif and stays 100% functional.

---

```bash
jahed@netbasics:~$ ip route show table pages
```

| route | deep links | purpose |
|---|---|---|
| `index.html` | *(default gateway)* | **Dashboard** — knowledge-check ring (91 · Mastered), per-module score table, focus-area plan, uplinks to everything |
| `learn.html` | `#m1` … `#m17` | **Study Guide** — all 17 modules condensed into key ideas + key terms, each with a *practice it* jump link |
| `sims.html` | `#ascii` `#journey` `#router` `#nat` `#tools` | **Simulators** — five interactive stations (captured below) |
| `labs.html` | — | **Lab Guides** — the four Packet Tracer activities rewritten as tickable checklists (saved per browser) + model answers + reflection-question solutions |
| `quiz.html` | — | **Practice Quiz** — 34 questions (2 per module) with explanations; mixed / per-module / weak-module sets; end-of-run review; personal-best tracking |

---

```bash
jahed@netbasics:~$ tcpdump -i sims0 -nn -c5
listening on sims0, link-type EN10MB … 5 stations captured
```

### 01 · Bits & ASCII — `sims.html#ascii`
The Module 1 activity. Type up to 5 characters → see decimal, hex and 8-bit binary → watch the signal
rendered as on/off cells travelling down the wire.

### 02 · Packet Journey — `sims.html#journey`
Lab 13.1.3 as an animation. Ping **local** (`172.16.31.2`) or **remote** (`10.10.10.2`) and step through
every hop. A PDU table records Src/Dst MAC + Src/Dst IPv4 at each device — highlighting the router's MAC
rewrite while the IPs stay end-to-end. Uses the lab's real addresses (`0060.7036.2849`, `00D0.BA8E.741A`, …).

### 03 · Home Router Lab — `sims.html#router`
A working home-router GUI — login `admin/admin`, tabs for **Setup / Administration / Wireless / Wireless
Security / Status**, real Save-Settings semantics (session drops on IP/password change), wired PCs, and a
wireless laptop with full scan → connect → passphrase flow. Every device has its own command prompt.
Two scenarios, auto-checked objectives:

```
SCENARIO A — Natsumi's home        (lab: Configure a Wireless Router and Clients)
  max users ........ 10
  router password .. MyPassword1!
  SSID ............. MyHome
  security ......... WPA2 Personal · MyPassPhrase1!
  clients .......... DHCP
  verify ........... browse http://skillsforall.srv

SCENARIO B — DHCP range change     (lab 11.2.3)
  router IP ........ 192.168.5.1
  pool start ....... 192.168.5.126
  max users ........ 75
  expected leases .. .126 → .127 → .128
  verify ........... ping from each leased client
```

### 04 · NAT Explorer — `sims.html#nat`
Lab *Examine NAT*. Four private hosts (`192.168.0.100–103`) send HTTP through the router; header cards
show the source **before/after** translation while a live NAT table maps inside-local → inside-global ports.

### 05 · Testing Toolbox — `sims.html#tools`
A simulated console (Module 17) with realistic timing and outputs:

```
ipconfig [/all] · ping · tracert · nslookup · arp -a · help · clear
```

The same console engine powers the PCs inside the Router Lab.

---

```bash
jahed@netbasics:~$ ls -la /var/lib/localStorage/      # progress & storage — 100% client-side
```

| key | content | surfaced as |
|---|---|---|
| `nb_lab_checks` | checked steps per lab guide | "Labs started x/4" |
| `nb_quiz_best` | best quiz percentage + date | "Quiz best" in the top bar |

Nothing leaves the browser. Clearing site data is the factory reset for progress.

---

```bash
jahed@netbasics:~$ tree /opt/netbasics-studio
```

```
├── index.html          dashboard
├── learn.html          study guide (17 modules)
├── sims.html           simulators
├── labs.html           lab guides & checklists
├── quiz.html           practice quiz
├── css/
│   └── style.css       design system (Poppins, light-only theme)
├── js/
│   ├── data.js         knowledge-check scores + quiz bank
│   ├── shared.js       storage/toast helpers + simulated terminal engine
│   ├── sims.js         the five simulators
│   └── quiz.js         quiz engine
├── assets/             photography used on the pages
├── uploads/            the original course resources this site was built from
└── extracted/          text extracted from the PDFs (working notes)
```

---

```bash
jahed@netbasics:~$ dig +short TXT course.sources
```

Compiled from the learner's own files — values on the site trace back to these:

- *Network Basics (NetCad Academy).pdf* — course notes, modules 1–4 in depth
- *Knowledge Results.pdf* — official knowledge-check result (91 · Mastered, per-module scores)
- *Configure a Wireless Router and Client.html* — Packet Tracer activity, wireless router & clients
- *11_2_3_Packet_Tracer_Configure_DHCP_on_a_Wireless_Router.pdf*
- *13_1_3_Packet_Tracer_Identify_MAC_and_IP_Addresses.pdf*
- *Packet Tracker Examine NAT on a Wireless Router.pdf*

---

```bash
jahed@netbasics:~$ cat /etc/studio/design.conf
```

```ini
theme        = light                # one theme, done right — no dark toggle debt
font         = "Poppins"            # graceful fallback: system sans-serif
borders      = 1px                  # thin, everywhere
shadows      = subtle
accents      = 1                    # a single controlled accent color
icons        = line-svg             # zero emoji
glass        = sticky-topbar-only   # restrained soft-glass, nowhere else
photography  = illustrative-only    # ethernet/switch hero, home router, fiber macro
layout_rule  = "real hierarchy + real data tables > decorative card grids"
```

---

```bash
jahed@netbasics:~$ man 1 practice        # scoring bands mirror the official knowledge check
```

```
score ≥ 90   →  MASTERED
80 – 89      →  ADVANCED
```

**The rep cycle:**

1. **READ** the module in the Study Guide.
2. **PLAY** with the matching simulator until the behaviour is predictable.
3. **REHEARSE** the lab checklist, then run the real activity in Packet Tracer.
4. **LOCK IT IN** with the module quiz — watch `m13` and `m5` climb to Mastered.

---

```bash
jahed@netbasics:~$ fortune
"A network you can rebuild from memory is a network you actually understand."
0 packets dropped during the making of this site.

jahed@netbasics:~$ logout
Connection to studio.local closed.
```
