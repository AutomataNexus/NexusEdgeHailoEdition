# NexusEdge Configuration Examples

Self-contained, ready-to-adapt site configurations for NexusEdge Hailo Edition.
Each example is a directory containing a `site.toml` (equipment, I/O map, control
algorithm, setpoints) and a matching `hardware-daemon.toml` (which Sequent
Microsystems HATs are present and at which stack addresses).

## Using an example

Copy the example directory, edit the channel map / setpoints / scaling to match
your wiring, then point the installer at it:

```bash
curl -fsSL https://nexusedgehailo.automatanexus.com/install.sh | sudo bash \
    -s -- --email you@example.com --password 'yourpass' --config ./ahu-single-zone/
```

The installer copies both `.toml` files into `/etc/nexusedge/config/` and starts
the controller; the app and the embedded control engine both read from there.

## Examples

| Directory | Equipment | Algorithm | Demonstrates |
|---|---|---|---|
| [`ahu-single-zone/`](ahu-single-zone/) | Air handling unit | `tmc_ahu` | One MegaBAS HAT; NTC temps; a current-transformer input scaled to amps; modulating heating/cooling valves + economizer damper; seasonal SAT setpoints. |

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

See [`docs/ALGORITHM_PARAMS.md`](../docs/ALGORITHM_PARAMS.md) for the full list of
control algorithms and their tunable parameters.
