# Zabbix WISP Infrastructure Templates

Production-tested Zabbix templates for monitoring Wireless ISP (WISP) infrastructure — PtMP base stations, PtP backhaul links, core/POP routing gear, and site environmental sensors.

Built and refined through real deployment work for a live regional WISP, not written from documentation alone. Each template ships with the items, low-level discovery (LLD) rules, triggers, and macros needed to actually run in production — not just a bare metric list.

   **[Read the full case study here](https://docs.google.com/document/d/1XUM5_YdoFCgTL2L8tD67BemfjKhf6VGDwnSYDy72Y6A/edit?usp=sharing)** — full context on the design decisions, alerting logic, and dashboard structure.

## What's Here

| Category | Vendors Covered | Status |
|---|---|---|
| PtMP Base Stations | MikroTik, Cambium, Ubiquiti (UBNT) | ✅ Available |
| PtP Backhaul | [insert vendors] | 🔜 Coming soon |
| Core & POP Routers/Switches | [insert vendors] | 🔜 Coming soon |
| Voltage & Environmental | [insert vendors] | 🔜 Coming soon |

## Repo Structure

```
zabbix-wisp-templates/
├── ptmp/
│   ├── mikrotik/
│   ├── cambium/
│   └── ubnt/
├── ptp-backhaul/
├── core-pop-routers/
├── voltage-environmental/
└── docs/
```

## What's in a Template

Each PtMP template monitors:
- **Network latency** — ICMP ping, ping loss, response time
- **RF & wireless state** — channel width, frequency, SSID, AP population
- **Inventory & asset control** — firmware version, serial number, device name
- **System health** — uptime, SNMP service availability

Triggers use hysteresis to avoid alert flapping on unstable links, and core/POP routers are mapped as parent hosts so a single upstream outage doesn't spam a NOC with hundreds of downstream subscriber alerts.

## Using These Templates

1. Download the `.xml` file for your vendor/category.
2. In Zabbix: **Data collection → Templates → Import**.
3. Review macros and item keys — you'll likely need to adjust these to match your own device naming, SNMP community strings, or firmware version quirks before it runs cleanly.

These are a strong starting point, not drop-in-and-forget. Every WISP's environment differs enough that some tuning is expected.

## About

I build custom Zabbix monitoring for WISPs and network operators — templates, LLD discovery, alerting logic, and NOC/Support dashboards tailored to how your team actually works.

Currently taking on a small number of free builds for network operators in exchange for a testimonial. If you want a template adapted to your specific hardware and environment, or a full monitoring setup built out, reach out: **[insert your contact — email or a way to DM you]**
