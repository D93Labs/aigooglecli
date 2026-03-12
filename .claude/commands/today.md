Give me a check-in on where things stand right now. Look at what's happened today so far — emails received, calendar events that have passed — and what's still ahead for the rest of the day. Pull any Google Tasks due today and note which are done and which are still open. Help me figure out what to focus on next.

**Execution order:**
1. Run `TZ=America/Chicago date` first to get the current time in CT. Use this to correctly determine what events have already passed vs. what's still ahead.
2. In a single parallel wave, fetch all of the following simultaneously:
   - Calendar events for today: CCSD93 (`kinsalk@ccsd93.com`), Social Media, and Family calendars
   - Gmail: inbox messages from today (use `in:inbox after:YYYY/MM/DD before:YYYY/MM/DD+1`)
   - Tasks from all four lists using known IDs (no tasklists_list call needed):
     - My Tasks: `MDkzMDA2NTY2MTE5NDY2MDE5MTU6MDow`
     - Today's Tasks: `bTVPeWFKR1c4T0NnT0VGVg`
     - Retirement Ceremony: `anJ6Z3NOREFZTmlxOXhsUA`
     - Dept Meeting: `MmViMlh3U2pkQWF2LXczUw`
   - Weather from Open-Meteo for Carol Stream, IL (lat: 41.8886, lon: -88.1348):
     `current_weather=true&daily=temperature_2m_max,temperature_2m_min,precipitation_probability_max,weathercode&forecast_days=1&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago`
3. Fetch email details for the most relevant messages in a second parallel wave.

Present the check-in in three parts: what's already happened, what's still ahead, and what to focus on next. Include a brief current weather snapshot (temp, conditions, high/low) in the "what's still ahead" section.
