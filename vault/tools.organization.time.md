---
id: 22drlGfQ0h95jgfzOGSG0
title: Time
desc: ''
updated: 1647770565029
created: 1609702188544
---

Tuesday 03 August 2021

> Most of us use our calendars all wrong: we don't schedule work; we schedule interruptions. Meetings get scheduled. Phone calls get scheduled. Doctor appointments get scheduled. You know what often doesn't get scheduled? Real work. All those other things are distractions. Often, they're other people's work. But they get dedicated blocks of time, and your real work becomes an orphan.

Peek into time blocking.

As Roman Stoic philosopher Seneca once wrote:

> “People are frugal in guarding their personal property; but as soon as it comes to squandering time, they are most wasteful of the one thing in which it is right to be stingy.”

----


Having a look at the MyTime plugin (https://github.com/codicelq/mytime) because I wanted a time tracking solution and that this is currectly lacking from the excellent Todo+ plugin.

Created a snippet to directyl add current time 

```bash
    "now": {
        "prefix": "now",
        "scope": "markdown,yaml",
        "body": "- `$CURRENT_HOUR:$CURRENT_MINUTE` ",
        "description": "now in hour:min"
    }
```


- `20:00` Started work on machine A
- `20:29` // Went to have a piss
- `21:26` Started work on machine A
- `23:26` // Went to have a piss
- `23:45` Started work on machine B



| Time span          | Task                      |
| -----------------: | ------------------------- |
|          `01:00`   | Started work on machine A |
|          `00:15`   | Started work on machine B |
|        **`01:15`** | **Total**                 |

> _Last update 20:29_ / Lines [valid:3, comments:2, invalid:0]


| Time span          | Task                      |
| -----------------: | ------------------------- |
|          `01:00`   | Started work on machine A |
|          `00:15`   | Started work on machine B |
|          `02:30`   | Went to have a piss       |
|        **`03:45`** | **Total**                 |

> _Last update 20:28_ / Lines [valid:5, comments:0, invalid:0]

---

Let's see if this work with intricated sentences or objects 



- `20:00` Started work on machine A

And this is the code I used for this time machine 

```bash
    "now": {
        "prefix": "now",
        "scope": "markdown,yaml",
        "body": "- `$CURRENT_HOUR:$CURRENT_MINUTE` ",
        "description": "now in hour:min"
    }
```
- `20:29` // Went to have a piss

In my amazing bathroom

- `21:26` Started work on machine A

Blah

- `23:26` // Went to have a piss

Outside 

- `23:45` Started work on machine B



| Time span          | Task                      |
| -----------------: | ------------------------- |
|          `01:00`   | Started work on machine A |
|          `00:15`   | Started work on machine B |
|        **`01:15`** | **Total**                 |

> _Last update 20:34_ / Lines [valid:3, comments:2, invalid:12]


Working !!! That looks like a very nice option 
Its not working in the todo+ files

  Luis_Molina seeds metabo:
    ✔ grab back latest Mzmine project @started(21-01-03 13:40) @done(21-01-03 13:42) @lasted(2m26s)
    - make MN:
      ✔ make MN metadata file @started(21-01-03 13:42) @done(21-01-03 13:47) @lasted(5m16s)
      ✔ upload stuff to GNPS @started(21-01-03 13:47) @done(21-01-03 15:06) @lasted(1h19m56s)
      ✔ briefly check MN in cytoscape @15m @started(21-01-03 15:56) @done(21-01-03 16:06) @lasted(10m11s)
      ✔ Run ISDB @1h @done(21-01-03 18:05)
        ✔ upload mgf and attributes to x2go @15m @started(21-01-03 16:06) @done(21-01-03 16:37) @lasted(31m29s)
        ssh allardp@x2go.epgl-geneve.org
        cd Desktop/FARMAnetwork/RECHERCHE/COMMON\ FASIE-FATHO/PMA/Ubuntu_VM_img/ISDB_DNP/results/
        ✔ run isdb via command line (x2go not working)  @30m @started(21-01-03 16:37) @done(21-01-03 16:42) @lasted(5m50s)
        ✔ get back top 50 locally @10m @started(21-01-03 16:42) @done(21-01-03 16:46) @lasted(4m31s)
    ✔ run taxo reponderation using Arabidopsis @1h @1h @started(21-01-03 17:47) @done(21-01-03 18:05) @lasted(18m24s)
        ✔ download latest version @started(21-01-03 14:30) @done(21-01-03 15:06) @lasted(36m54s)
      ☐ script a metadata formatter that take a sample metadata and feature table and generates a sample metadat grouped feature table (for cytoscape display) @4h
      stope here  /Users/pma/Dropbox/Research_UNIGE/git_repos/pf_project/src/peaklist_formatter.py
    ☐ make report @1h
    ☐ send it @10m

----

What if it runned over various days ?? 
Doesn't seem to take days shifts into account.


## Sunday 03 January

- `20:38` //_Good morning_
- `20:39` Bricole_2
- `22:00` Bricole_1
## Monday 04 January

- `07:45` //_Let's start_
- `08:39` Bricole_2
- `09:43` Bricole_3
- `21:39` Bricole_1


- `21:03` Mail

## Timeis

https://time.is/fr/
