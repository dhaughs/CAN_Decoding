# CAN_Decoding

Open-source CAN bus DBC files and signal references for reverse-engineered vehicles. Bench-verified bit definitions, not assumptions.

---

## Repository structure

```
vehicles/
  toyota/
    tacoma/
      3rd_gen_2016_2023/
        tacoma_3rdgen_hs_can.dbc          # CANdb++ DBC, cantools strict-compatible
        tacoma_3rdgen_hs_can_signals.xlsx # Human-readable signal reference
        tacoma_3rdgen_service_pids.xlsx   # ScanGauge XGauge OBD/UDS PIDs
```

---

## Signal confidence levels

| Level | Meaning |
|---|---|
| **confirmed** | Bit position and behavior bench-verified against raw captured frames |
| **unverified** | Position inferred but not independently bench-tested |
| **unknown** | Signal observed; purpose not yet identified |

---

## Vehicles

### Toyota Tacoma 3rd Gen (2016-2023) — HS-CAN (DW CAN 01, 500 kbps)

- **131 messages decoded**
- **468 signals** (463 confirmed, 2 unverified, 3 unknown)
- **52 enumeration values** defined
- Capture tool: Vehicle Spy 3 / neoVI Fire 2
- Sessions: April 2026 (drive captures), November 2026 (bench validation)
- Bench vehicle: 2016 Tacoma (3rd gen architecture is consistent across 2016-2023)

Key systems covered: engine, transmission (Aisin AC60), ABS/VSC, body control (doors, locks, lighting stalk, seatbelts), steering, ADAS.

The `tacoma_3rdgen_service_pids.xlsx` file contains ScanGauge XGauge request/response entries for Toyota powertrain sensors (trans temp, oil temp, fuel pressure, etc.). These are diagnostic poll PIDs, separate from the broadcast DBC signals.

---

## Contributing

Signal corrections and additions welcome. If you bench-test a signal:

1. Note the raw byte capture that proves it (hex bytes, which bit changed, what you activated)
2. Update the DBC and xlsx together
3. Change the confidence to `confirmed` and add a note with date and test method

For unidentified messages or signals, open an issue with the message ID and any observed byte patterns.

---

## License

MIT — use freely, attribution appreciated.
