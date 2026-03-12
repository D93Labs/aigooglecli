Give me a morning briefing. What does today look like? Check my calendars, unread emails, and pull any Google Tasks due today.

**Execution order:**
1. Run `TZ=America/Chicago date` first to get the current time in CT.
2. In a single parallel wave, fetch all of the following simultaneously:
   - Calendar events for today: CCSD93 (`kinsalk@ccsd93.com`), Social Media, and Family calendars
   - Gmail: unread inbox messages from today (`in:inbox is:unread`)
   - Tasks from all four lists using known IDs (no tasklists_list call needed):
     - My Tasks: `MDkzMDA2NTY2MTE5NDY2MDE5MTU6MDow`
     - Today's Tasks: `bTVPeWFKR1c4T0NnT0VGVg`
     - Retirement Ceremony: `anJ6Z3NOREFZTmlxOXhsUA`
     - Dept Meeting: `MmViMlh3U2pkQWF2LXczUw`
   - Weather from Open-Meteo for Carol Stream, IL (lat: 41.8886, lon: -88.1348):
     `current_weather=true&daily=temperature_2m_max,temperature_2m_min,precipitation_probability_max,weathercode&forecast_days=1&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago`
3. Fetch email details (metadata) for the top unread messages in a second parallel wave.

Present a clean briefing. Lead with a one-line weather snapshot (current temp, conditions, today's high/low, precip chance). Then: calendar events for the day, unread emails flagged for action, and open tasks. End with a brief note on what to focus on first.
