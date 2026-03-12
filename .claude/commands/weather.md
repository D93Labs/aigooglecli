Get current weather conditions and today's forecast for Kevin's location.

**Execution order:**
1. Run `TZ=America/Chicago date` via Bash to get the current time — needed to filter out past hours from the hourly breakdown.
2. Use the default location: **Carol Stream, IL** (lat: 41.8886, lon: -88.1348).
3. Fetch from Open-Meteo in a single call:
   - `current_weather=true`
   - `daily=temperature_2m_max,temperature_2m_min,precipitation_sum,precipitation_probability_max,weathercode`
   - `hourly=temperature_2m,precipitation_probability,weathercode`
   - `temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago`
   - `forecast_days=1`

**Display:**
- Location label: "Carol Stream, IL"
- Current temp, conditions (from WMO code), wind speed
- Today's high / low
- Chance of precipitation (from daily `precipitation_probability_max`)
- Hourly breakdown for remaining hours of today only — skip any hours already past in CT
  - Format: `2:00 PM — 58°F, 20% rain chance, Partly cloudy`

Use the WMO weather code table in CLAUDE.md to translate codes to readable conditions.

If the Open-Meteo call fails, say so clearly and do not guess at conditions.
