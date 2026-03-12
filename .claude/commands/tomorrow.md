Help me prep for tomorrow. Check both calendars for tomorrow's events, scan my inbox for anything I need to handle before the day starts, and pull my Google Tasks due tomorrow. Summarize what's coming, and suggest what to prioritize first thing in the morning.

**Execution order:**
1. Run `TZ=America/Chicago date` first to get the current date/time in CT. Calculate tomorrow's date from this.
2. In a single parallel wave, fetch all of the following simultaneously:
   - Calendar events for tomorrow: CCSD93 (`kinsalk@ccsd93.com`), Social Media, and Family calendars
   - Gmail: unread inbox messages (`in:inbox is:unread`)
   - Tasks from all four lists using known IDs (no tasklists_list call needed):
     - My Tasks: `MDkzMDA2NTY2MTE5NDY2MDE5MTU6MDow`
     - Today's Tasks: `bTVPeWFKR1c4T0NnT0VGVg`
     - Retirement Ceremony: `anJ6Z3NOREFZTmlxOXhsUA`
     - Dept Meeting: `MmViMlh3U2pkQWF2LXczUw`
   - Weather from Open-Meteo for Carol Stream, IL (lat: 41.8886, lon: -88.1348):
     `daily=temperature_2m_max,temperature_2m_min,precipitation_probability_max,weathercode&forecast_days=2&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago`
     Use index `[1]` from the daily arrays to get tomorrow's data.
3. Fetch details on any emails that look actionable.

Summarize tomorrow's calendar, flag anything in the inbox that should be handled tonight, list tasks due tomorrow, and close with a recommended focus for the morning. End with a brief weather note for tomorrow — conditions, high/low, and whether to expect rain.
