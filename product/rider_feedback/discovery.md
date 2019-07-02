### Overview

An important component of the SMARTA and Ataper projects is the eventual incorporation of user-generated feedback as an organic, discrete source of system events, behaviors, alerts, and foibles. This data source would service the needs of ostensibly ephemeral impact events for the system and ultimately feed a data warehouse for BI analysis. 

The conceit of the story is that primary sources of truth are fundamentally invalidated or otherwise eroded by one-off events that are unaccounted for in the existing API.

### Goals

Our exaxmple for the first iteration is a riff on the Waze-style user feedback system with the key characteristics:

* Pre-defined event categories.
* A confirm/deny system for each event to invalidate out-of-date/resolved incidents.
* Pre-emptive visual representation at impacted stations/lines.
* Traceability to individual rides and riders. 

Some stretch and open-ended goals and consequences of this initiative: 

* Rider login system (OpenID?)
* Tracked user preferences.
* Cached seaerches/previous trips.


<img src="https://i.imgur.com/l3VooIs.png" width="250" />

<img src="https://i.imgur.com/TmHonoS.png" width="250" />


### Scenarios

Scenario: Inclement weather has impacted the system as follows: 
  * A fallen tree forces Brookhaven station to single-track trains with all scheduled Gold line trains incurring a +3 minute delay to their overall trips. 
  * The bus bay capacity is reduced and bus departure/arrivals are shuffled from the posted locations.
  * The parking lot availability is reduced by 50% 
  * Adjacent traffic and crosswalk lights are non-functioning leading to considerable backed up traffic
  
|Actor|Goal(s)| 
|---|---|
|Rider (Reporter)| |
|Rider (Viewer)|   |
|SMARTA (API)|   |
|Ataper (UI)| |
|Analysis (Data science)| |

### Key Questions

To launch an MVP for this feature experiment we need answers to a handful of key questions:

* How do we determine consensus of the existence/non-existence for a given reported event? 
* What categories of events should we track by default?
* How should the events be represented in the UI?
* What's the lifespan of a reported event?


### Mock Ups

### Persistence and Identity

### MVP
