Run a WiFi access point scan on Kevin's MacBook and display a full diagnostic report.

Run all four of these Bash commands:

1. `system_profiler SPAirPortDataType 2>/dev/null`
2. `ifconfig en0 | grep inet`
3. `ping -c 4 8.8.8.8 | tail -2`
4. `route -n get default 2>/dev/null | grep gateway`

Parse and present the results as a clean report with three sections:

## Current Connection

Show the following in a two-column table:

- **Network** — redacted by macOS privacy settings (note this if so)
- **IP Address** — from ifconfig
- **Gateway** — from route command
- **Protocol** — PHY Mode (e.g., 802.11ax / WiFi 6)
- **Band / Channel** — e.g., 5 GHz — Ch. 149
- **Channel Width** — e.g., 20MHz, 40MHz, 80MHz (pull from the channel line in system_profiler)
- **MCS Index** — from system_profiler output
- **Signal** — dBm
- **Noise** — dBm
- **SNR** — calculated (signal minus noise), with quality rating: Excellent (>40), Good (25–40), Fair (10–25), Poor (<10)
- **Transmit Rate** — Mbps
- **Security** — e.g., WPA2 Personal
- **Latency** — avg ms to 8.8.8.8 and packet loss % from ping results. Rate as: Great (<20ms), Acceptable (20–50ms), or Slow (>50ms)

## Nearby Access Points

Show all other visible networks in a markdown table with columns: Network, Band, Channel, Protocol, Security, Signal.

- Sort by signal strength descending when signal data is available
- Label SSIDs as "Network 1", "Network 2", etc. (macOS redacts them for privacy)
- Signal data is often unavailable for non-connected networks — show "n/a" for those
- Flag any unsecured networks (no security) with ⚠ in the Security column

Add a one-line footnote: *Signal data for nearby networks is not always available — macOS only exposes full details for your connected AP.*

## Summary

2–3 sentences covering:
- Total APs visible and any channel congestion (multiple APs on the same channel)
- Channel width note if on 20MHz — WiFi 6 performs best at 80MHz, worth flagging to IT if persistent
- Latency quality based on ping results
- Any unsecured networks nearby flagged as a heads-up

Keep the tone calm, clear, and practical — consistent with Kevin's assistant persona.
