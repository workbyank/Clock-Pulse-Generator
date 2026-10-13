# Circuit notes

## 1. Astable 555 clock

The NE555P runs in astable mode:

- Pin 8 → +5 V, pin 1 → GND
- Pin 4 (reset) → +5 V, so the timer is never held in reset
- R1 (1 kΩ) from +5 V to pin 7 (discharge)
- R2 (100 kΩ) from pin 7 to pins 2 (trigger) and 6 (threshold), which are tied together
- C (1 µF) from pins 2/6 to GND
- Pin 3 (output) → select logic input

Charge path: +5 V → R1 → R2 → C. Discharge path: C → R2 → pin 7. The output is high while the capacitor charges to about 2/3 Vcc and low while it discharges to about 1/3 Vcc.

Typical value: C = 1 µF gives a slow clock (about 7 Hz with the values in the README). For faster clocks, reduce C or R2. Keep C at 0.1 µF or higher for stable timing.

## 2. Select logic

| Select | Manual pulse | Astable pulse | OR output |
|:------:|:------------:|:-------------:|:---------:|
| 1 (auto)   | X | passes | follows astable |
| 0 (manual) | passes | blocked | follows manual |

- AND gate A: astable AND select
- NOT gate: invert select
- AND gate C: manual AND (NOT select)
- OR gate: A OR C

The NOT gate is required so that both paths can never be active at the same time.

## 3. Halt

The HLT signal is inverted (NOT gate) and ANDed with the OR output:

| HLT | Clock output |
|:---:|:------------:|
| 0 | Clock runs |
| 1 | Output held low (clock stopped) |

## 4. Power and decoupling

- Place a 0.1 µF ceramic capacitor across VCC and GND near each IC.
- Add a bulk electrolytic capacitor (10 µF or more) across the rails where the supply enters the board. The large electrolytic on the breadboard is doing this job.
- Use short, neat wires for the clock line. Long wires add capacitance and noise.

## 5. Debugging checklist

1. Measure VCC at every IC. It should read close to 5 V.
2. Check that no unused gate input is floating.
3. Probe the 555 output. You should see a square wave at the expected frequency. If it is flat, check pin 4 (reset), pin 8 (VCC), and the RC network.
4. Check that the manual push button is not bouncing. If the count is wrong when stepping manually, add a debounce circuit.
5. Confirm that HLT high stops the output.

## 6. Monostable reference

The original notes also include a 555 monostable (one-shot) configuration with 1 MΩ and 0.1 µF. It is not used in the final clock generator, but it is kept here as a reference for pulse-shaping experiments.
