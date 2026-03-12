Get the 7-day weather forecast for Kevin's location.

**Execution order:**
1. Use the default location: **Carol Stream, IL** (lat: 41.8886, lon: -88.1348).
2. Fetch 7-day daily forecast from Open-Meteo in a single call:
   - `daily=temperature_2m_max,temperature_2m_min,precipitation_sum,precipitation_probability_max,weathercode`
   - `temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago`
   - `forecast_days=7`

**Display:**
- Location label: "Carol Stream, IL"
- Clean day-by-day table:

| Day | Conditions | High / Low | Rain Chance |
|-----|------------|------------|-------------|
| Tuesday | Partly cloudy | 62° / 44° | 10% |
| Wednesday | Rain | 55° / 41° | 80% |
...

- Flag any days with notable weather in bold or with a note — thunderstorms (code 95, 96, 99), heavy rain (code 65, 67), snow (codes 71–77), or rain chance above 60%.
- Close with a one-line summary of the week's overall pattern (e.g., "Quiet start to the week, rain moves in Wednesday, clears by the weekend.")

Use the WMO weather code table in CLAUDE.md to translate codes to readable conditions.

If the Open-Meteo call fails, say so clearly and do not guess at conditions.
