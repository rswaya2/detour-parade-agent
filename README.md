# Detour: a parade-day navigation agent

Detour gets New Yorkers where they need to go during Macy's 100th Thanksgiving Day Parade (Nov 26, 2026). It reroutes Users in real time around street closures and spreads everyone across crossings, so the detour doesn't become the next jam.

Built in a 25-minute team challenge at **Build for the Agent Era**, a Big Red Product Club workshop at Cornell Tech led by Alman Shibli (Product Manager, Google).

## The problem
The parade closes a long stretch of the Upper West Side and Midtown and ends at Herald Square, near Penn Station, on one of the busiest travel days of the year. Map apps route each person alone, so they send everyone to the same open streets and crossings.

## How it maps to the workshop framework
| Question | Detour's answer |
|---|---|
| **Customer journey** | One step in the User's day: their agent reads the plan (e.g. a 12:30 train from Penn), and Detour handles when to leave, where to cross, and rerouting as streets reopen. |
| **Distribution** | An MCP connector with parade-specific tools general maps don't have: live closures, crossing points, entrance crowding, "arrive by" planning. Official parade-data partner status makes it the trusted source. |
| **Value** | Paid when the job gets done: the city and MTA for crowd distribution, rideshare referral fees, labeled sponsored stops. Free for Users. |
| **Control** | A separate MCP with only a few tools, never the full API. Booking or paying needs the User's confirmation. Closures are hard blocks, and every crossing has a capacity cap. |

## The herding problem (Networks & Markets)
If every agent sends its User down the fastest street, that street jams: the selfish (Nash) equilibrium. Because Detour sees everyone's trips, it routes toward the social optimum and never sends more people across the parade than the crossings can carry (the min-cut). In the modeled demo with 1,000 agents, the average trip is 42 min when everyone gets the same route, 24 min with selfish agents, and 22.2 min with Detour coordinating them.

## Run the demo
1. Get a Google Maps Platform demo key.
2. Open `detour.html` in Chrome and paste the key into the box (it's stored only in your browser, never in the file).
3. Pick a scenario, press **Plan my trip**, move the clock, and try the disruption, herding and permission buttons.

Uses the Maps JavaScript API, Routes API, and Weather API.

**Note:** The parade route, closure times, crossing capacities and crowd numbers are approximate or modeled for the demo, not official NYPD or Macy's data.

## Team
- **Suhani**: built the demo's routing engine, parade closures, disruptions and weather check
- **Riya**: built the demo's herding simulation (selfish vs. coordinated routing) and permissions panels; distribution and control strategy
