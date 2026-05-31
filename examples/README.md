# NexusEdge Configuration Examples

Self-contained, ready-to-adapt site configurations for NexusEdge Hailo Edition.
Each example is a directory with a `site.toml` (equipment, I/O map, control
algorithm, setpoints) and a matching `hardware-daemon.toml` (which Sequent
Microsystems HATs are present and at which stack addresses).

NexusEdge **Community Edition** includes **three control algorithms** —
`tmc`, `pid`, and `on_off`. The examples below cover all three. (The full
library of 40+ equipment-specific algorithms — AHU, RTU, chiller, cooling
tower, DOAS, VAV, natatorium, lead/lag plants, and more — unlocks with a Pro
subscription; they appear in the algorithm selector but are locked in
Community Edition.)

## Using an example

Copy the example directory, edit the channel map / setpoints / scaling to match
your wiring, then point the installer at it:

```bash
curl -fsSL https://nexusedgehailo.automatanexus.com/install.sh | sudo bash \
    -s -- --email you@example.com --password 'yourpass' --config ./tmc-ahu/
```

The installer copies both `.toml` files into `/etc/nexusedge/config/` and starts
the controller; the app and the embedded control engine both read from there.

## Community-tier examples

| Directory | Algorithm | Equipment | Demonstrates |
|---|---|---|---|
| [`ahu-single-zone/`](ahu-single-zone/) | `tmc` | Single-zone AHU | Temperature-modulation control of heating/cooling valves + economizer damper; a current-transformer input scaled to amps; freeze/high-limit safeties. |
| [`pid-loop/`](pid-loop/) | `pid` | Hot-water reheat loop | Classic PID modulating one valve to a zone-temperature setpoint; reverse-acting (heating) sense. |
| [`on-off-boiler/`](on-off-boiler/) | `on_off` | Hot-water boiler | Hysteresis/bang-bang burner + circulator control with minimum on/off timers (anti-short-cycle). |

## Config notes

- **`name` is required** on every `[[equipment.inputs]]` and `[[equipment.outputs]]`.
- **Analog inputs are raw 0-10V.** NTC channels (`ntc10k`/`ntc1k`) auto-convert to
  °F. For 0-10V transmitters, transducers, and current transformers, add an
  `[equipment.inputs.scaling]` block to map volts to engineering units:

  ```toml
  [equipment.inputs.scaling]
  input_min = 0.0      # volts at the low end
  input_max = 10.0     # volts at the high end
  output_min = 0.0     # engineering unit at input_min
  output_max = 250.0   # engineering unit at input_max  (e.g. PSIG, %RH, A)
  ```

  Live-zero sensors work too (e.g. a 2-10V transmitter → `input_min = 2.0`).
- **Modulating outputs** use `heating_valve` / `cooling_valve` / `damper` (0-100%
  → 0-10V). Set `inverted = true` for reverse-acting or normally-closed actuators.
- **Discrete outputs** use `triac` (MegaBAS) or `relay` (relay/SSR HATs).
- **Board types**: `megabas`, `megaind`, `univin16`, `uout16`, `relind16`,
  `relind8`. Each `[boards.<type>]` takes `enabled` and `stacks = [..]`.

See [`docs/ALGORITHM_PARAMS.md`](../docs/ALGORITHM_PARAMS.md) for every algorithm
and its tunable parameters.
