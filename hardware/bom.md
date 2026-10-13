# Bill of materials

| Qty | Part | Value / Part number | Purpose |
|:---:|------|---------------------|---------|
| 1 | Timer IC | NE555P | Astable clock source |
| 1 | Quad 2-input AND gate | 74LS08 (SN74LS08N) | AND gates A and C in the select logic |
| 1 | Quad 2-input OR gate | 74LS32 (SN74LS32N) | Combines auto and manual pulses |
| 1 | Hex inverter | 74LS04 (SN74LS04N) | NOT gates for select and HLT |
| 1 | Resistor | 1 kΩ | R1 of the 555 |
| 1 | Resistor | 100 kΩ | R2 of the 555 (fixed or trimmer) |
| 1 | Trimmer potentiometer | ~100 kΩ | Frequency adjustment (optional) |
| 1 | Capacitor | 1 µF electrolytic | Timing capacitor C of the 555 |
| 2+ | Capacitor | 0.1 µF ceramic | Decoupling, one per IC |
| 1 | Capacitor | 10 µF electrolytic | Bulk supply filter |
| 1 | Pushbutton | Momentary, 4-pin | Manual pulse |
| 1 | Toggle / slide switch | SPDT | Select (auto / manual) |
| 1 | Switch | SPST | HLT (halt) |
| 3–4 | LED | 5 mm, yellow | Indicators |
| 3–4 | Resistor | 220 Ω | LED current limiting |
| — | Breadboard | Full-size | Prototyping |
| — | Jumper wires | Assorted | Connections |
| — | Power supply | Regulated 5 V | VCC |

Part numbers are as printed on the chips in the photos. Confirm the exact package and pinout against the datasheet before wiring.
