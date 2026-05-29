# NexusEdge Hailo Edition — Algorithm Parameters

Accepted parameters for each control algorithm. Set these as keys under
`[equipment.algorithm_params]` (with `algorithm = "<id>"`) in your site config.
Defaults apply when a key is omitted. Generated from the live engine schema.

| # | Algorithm | id | # params |
|---|---|---|---|
| 1 | Always-On Enable (season-gated) | `always_on` | 1 |
| 2 | Cascade | `cascade` | 7 |
| 3 | Cascade Boiler Plant | `cascade_boiler` | 7 |
| 4 | Commercial Lighting & Power | `commercial_lighting` | 8 |
| 5 | Cooling Tower | `cooling_tower` | 8 |
| 6 | DX + CW AHU | `dx_cw_ahu` | 9 |
| 7 | Electrical Load Monitor (120V) | `electrical_monitor` | 8 |
| 8 | Fan Coil Unit (2-Way / 4-Way) | `fan_coil` | 7 |
| 9 | Heat Pump | `heat_pump` | 8 |
| 10 | Lead/Lag Boilers | `lead_lag_boiler` | 7 |
| 11 | Lead/Lag Chillers | `lead_lag_chiller` | 9 |
| 12 | Lead/Lag Pumps | `lead_lag_pump` | 12 |
| 13 | Linear Proportional | `linear` | 6 |
| 14 | Model Predictive Control (Advisory) | `mpc_advisory` | 5 |
| 15 | On/Off (Bang-Bang) | `on_off` | 5 |
| 16 | PID | `pid` | 8 |
| 17 | Pool Controller (Gas Heater) | `pool_gas_heater` | 13 |
| 18 | Pool Controller (Heat Pump) | `pool_heat_pump` | 13 |
| 19 | Pressure Booster Pumps | `pressure_booster` | 29 |
| 20 | Residential Boiler | `resi_boiler` | 7 |
| 21 | Residential Furnace | `resi_furnace` | 8 |
| 22 | Residential Heat Pump | `resi_heat_pump` | 7 |
| 23 | Rooftop Unit | `rtu` | 10 |
| 24 | Smart Garden Controller | `smart_garden` | 9 |
| 25 | Smart Home Controller | `smart_home` | 10 |
| 26 | TMC (Temperature Modulation) | `tmc` | 16 |
| 27 | TMC AHU | `tmc_ahu` | 15 |
| 28 | TMC AHU 4-pipe Lead/Lag | `tmc_ahu_lead_lag` | 26 |
| 29 | TMC Chiller | `tmc_chiller` | 9 |
| 30 | TMC Chiller (simplified) | `tmc_chiller_simple` | 5 |
| 31 | TMC Comfort Boiler | `tmc_comfort_boiler` | 8 |
| 32 | TMC DOAS + DX + Season Relay | `tmc_doas_changeover` | 14 |
| 33 | TMC Direct-Fired DOAS + DX | `tmc_doas_dx` | 11 |
| 34 | TMC Domestic Boiler | `tmc_domestic_boiler` | 5 |
| 35 | TMC Electric Heat | `tmc_electric_heat` | 6 |
| 36 | TMC Greenhouse | `tmc_greenhouse` | 8 |
| 37 | TMC Natatorium | `tmc_natatorium` | 7 |
| 38 | TMC Steambundle | `tmc_steambundle` | 9 |
| 39 | TMC VAV | `tmc_vav` | 6 |
| 40 | TMC VAV + DX | `tmc_vav_dx` | 8 |
| 41 | Zone Reheat | `tmc_zone_reheat` | 13 |
| 42 | VFD Pump Pack | `vfd_pump_pack` | 10 |
| 43 | Water-Cooled Chiller | `water_cooled_chiller` | 6 |
| 44 | Water Monitor (City) | `water_monitor_city` | 9 |
| 45 | Water Monitor (Well) | `water_monitor_well` | 9 |

## Always-On Enable (season-gated) — `always_on`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `season` | Season Gate (0=always 1=winter-only 2=summer-only) | 0.0 | 0.0 | 2.0 | mode |

## Cascade — `cascade`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `space_setpoint` | Space Setpoint | 72.0 | 60.0 | 85.0 | °F |
| `outer_gain` | Outer Gain | 2.0 | 0.1 | 20.0 |  |
| `sat_setpoint_min` | SAT Setpoint Min | 55.0 | 40.0 | 75.0 | °F |
| `sat_setpoint_max` | SAT Setpoint Max | 75.0 | 55.0 | 95.0 | °F |
| `inner_gain` | Inner Gain | 15.0 | 0.1 | 100.0 |  |
| `inner_integral_gain` | Inner Integral | 0.1 | 0.0 | 5.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |

## Cascade Boiler Plant — `cascade_boiler`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `deadband` | Deadband | 3.0 | 0.5 | 10.0 | °F |
| `sp_at_oat_low` | SP at Low OAT | 160.0 | 100.0 | 160.0 | °F |
| `sp_at_oat_high` | SP at High OAT | 130.0 | 100.0 | 160.0 | °F |
| `wwsd_oat` | WWSD OAT | 65.0 | 50.0 | 80.0 | °F |
| `lag_stage_on_delay_secs` | Lag Stage Delay | 300.0 | 60.0 | 1800.0 | s |
| `high_limit_temp` | High Limit | 200.0 | 160.0 | 210.0 | °F |
| `pump_oat_threshold` | Pump OAT Threshold | 35.0 | 0.0 | 65.0 | °F |

## Commercial Lighting & Power — `commercial_lighting`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `occupancy_timeout_secs` | Occ Timeout | 1200.0 | 300.0 | 3600.0 | s |
| `daylight_on_lux` | Daylight On | 300.0 | 50.0 | 800.0 | Lux |
| `daylight_off_lux` | Daylight Off | 500.0 | 100.0 | 1200.0 | Lux |
| `dimmer_min_pct` | Dimmer Min | 10.0 | 5.0 | 30.0 | % |
| `parking_min_pct` | Parking Min | 30.0 | 20.0 | 50.0 | % |
| `building_demand_pct` | Demand Limit | 80.0 | 50.0 | 95.0 | % |
| `phase_imbalance_pct` | Phase Imbalance | 10.0 | 5.0 | 20.0 | % |
| `power_factor_warning` | PF Warning | 0.85 | 0.7 | 0.95 |  |

## Cooling Tower — `cooling_tower`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `cw_setpoint` | CW Supply SP | 85.0 | 65.0 | 100.0 | °F |
| `deadband` | Deadband | 3.0 | 1.0 | 10.0 | °F |
| `min_approach` | Min Approach | 7.0 | 3.0 | 15.0 | °F |
| `min_fan_speed` | Min Fan Speed | 20.0 | 10.0 | 40.0 | % |
| `max_fan_speed` | Max Fan Speed | 100.0 | 60.0 | 100.0 | % |
| `stage_delay_secs` | Stage Delay | 300.0 | 60.0 | 900.0 | s |
| `basin_heater_oat` | Basin Heater OAT | 40.0 | 30.0 | 50.0 | °F |
| `freeze_lockout_oat` | Freeze Lockout OAT | 35.0 | 25.0 | 45.0 | °F |

## DX + CW AHU — `dx_cw_ahu`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | SAT Setpoint | 55.0 | 45.0 | 75.0 | °F |
| `deadband` | Deadband | 1.0 | 0.1 | 3.0 | °F |
| `dx_stage1_on_offset` | DX1 ON Offset | 1.0 | 0.1 | 5.0 | °F |
| `dx_stage1_off_offset` | DX1 OFF Offset | 0.5 | 0.1 | 3.0 | °F |
| `dx_stage2_on_delay_secs` | DX2 ON Delay | 600.0 | 30.0 | 1800.0 | s |
| `min_oa_position` | Min OA % | 15.0 | 0.0 | 50.0 | % |
| `max_cw_position` | Max CW % | 100.0 | 50.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |
| `cw_gain` | CW Gain | 20.0 | 1.0 | 100.0 |  |

## Electrical Load Monitor (120V) — `electrical_monitor`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `per_breaker_soft_limit` | Soft Limit | 24.0 | 15.0 | 28.0 | A |
| `per_breaker_hard_limit` | Hard Limit | 28.0 | 20.0 | 30.0 | A |
| `hard_limit_delay_secs` | Hard Limit Delay | 10.0 | 3.0 | 30.0 | s |
| `whole_house_demand_pct` | Demand Limit % | 80.0 | 50.0 | 95.0 | % |
| `main_breaker_amps` | Main Breaker | 200.0 | 60.0 | 400.0 | A |
| `shed_rotation_secs` | Shed Rotation | 900.0 | 300.0 | 3600.0 | s |
| `brownout_threshold` | Brown-Out V | 108.0 | 100.0 | 114.0 | V |
| `overvoltage_threshold` | Over-Voltage V | 132.0 | 126.0 | 140.0 | V |

## Fan Coil Unit (2-Way / 4-Way) — `fan_coil`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `cool_setpoint` | Cool Setpoint | 74.0 | 60.0 | 85.0 | °F |
| `heat_setpoint` | Heat Setpoint | 70.0 | 55.0 | 78.0 | °F |
| `deadband` | Deadband | 1.0 | 0.5 | 5.0 | °F |
| `valve_gain` | Valve Gain | 8.0 | 1.0 | 20.0 |  |
| `valve_integral` | Valve Integral | 0.3 | 0.01 | 2.0 |  |
| `max_valve_step` | Max Valve Step | 5.0 | 1.0 | 20.0 | % |
| `changeover_lockout_min` | Changeover Lockout | 30.0 | 5.0 | 120.0 | min |

## Heat Pump — `heat_pump`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `heat_setpoint` | Heat Setpoint | 68.0 | 55.0 | 85.0 | °F |
| `cool_setpoint` | Cool Setpoint | 74.0 | 60.0 | 90.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 5.0 | °F |
| `balance_point` | Balance Point OAT | 30.0 | 10.0 | 45.0 | °F |
| `aux_lockout_oat` | Aux Lockout OAT | 40.0 | 20.0 | 55.0 | °F |
| `defrost_interval_secs` | Defrost Interval | 3600.0 | 600.0 | 7200.0 | s |
| `defrost_duration_secs` | Defrost Duration | 180.0 | 60.0 | 600.0 | s |
| `stage2_delay_secs` | Stage 2 Delay | 300.0 | 60.0 | 900.0 | s |

## Lead/Lag Boilers — `lead_lag_boiler`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `hw_supply_setpoint` | HWS Setpoint | 160.0 | 100.0 | 200.0 | °F |
| `deadband` | Deadband | 3.0 | 0.5 | 10.0 | °F |
| `stage_on_delay_secs` | Stage ON Delay | 300.0 | 0.0 | 1800.0 | s |
| `stage_off_delay_secs` | Stage OFF Delay | 300.0 | 0.0 | 1800.0 | s |
| `pump_pre_start_secs` | Pump Pre-Start | 60.0 | 10.0 | 600.0 | s |
| `changeover_interval_secs` | Changeover Interval | 604800.0 | 3600.0 | 2592000.0 | s |
| `proof_bypass` | Proof Bypass | 0.0 | 0.0 | 1.0 | bool |

## Lead/Lag Chillers — `lead_lag_chiller`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `cws_setpoint` | CWS Setpoint | 45.0 | 38.0 | 55.0 | °F |
| `deadband` | Deadband | 2.0 | 0.1 | 10.0 | °F |
| `stage_on_delay_secs` | Stage ON Delay | 600.0 | 0.0 | 1800.0 | s |
| `stage_off_delay_secs` | Stage OFF Delay | 900.0 | 0.0 | 1800.0 | s |
| `pump_pre_start_secs` | Pump Pre-Start | 60.0 | 10.0 | 600.0 | s |
| `changeover_interval_secs` | Changeover Interval | 604800.0 | 3600.0 | 2592000.0 | s |
| `condenser_pump_post_run_secs` | Condenser Pump Post-Run | 180.0 | 0.0 | 900.0 | s |
| `loop_temp_max` | 2-Pipe Loop Flush Max (0=disabled) | 0.0 | 0.0 | 120.0 | °F |
| `proof_bypass` | Proof Bypass | 0.0 | 0.0 | 1.0 | bool |

## Lead/Lag Pumps — `lead_lag_pump`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `stage_on_threshold` | Stage ON Threshold | 80.0 | 30.0 | 100.0 | % |
| `stage_off_threshold` | Stage OFF Threshold | 25.0 | 0.0 | 80.0 | % |
| `stage_on_delay_secs` | Stage ON Delay | 300.0 | 0.0 | 1800.0 | s |
| `stage_off_delay_secs` | Stage OFF Delay | 300.0 | 0.0 | 1800.0 | s |
| `min_on_delay` | Min ON Delay | 300.0 | 60.0 | 3600.0 | s |
| `min_off_delay` | Min OFF Delay | 300.0 | 60.0 | 3600.0 | s |
| `proof_amps` | Proof Amps | 0.5 | 0.0 | 50.0 | A |
| `proof_fail_delay_secs` | Proof Fail Delay | 30.0 | 5.0 | 300.0 | s |
| `proof_bypass` | Proof Bypass | 0.0 | 0.0 | 1.0 | bool |
| `changeover_enabled` | Weekly Changeover | 1.0 | 0.0 | 1.0 | bool |
| `changeover_interval_secs` | Changeover Interval | 604800.0 | 3600.0 | 2592000.0 | s |
| `post_run_time` | Post-Run Time | 120.0 | 0.0 | 900.0 | s |

## Linear Proportional — `linear`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 68.0 | 30.0 | 120.0 | °F |
| `proportional_gain` | Gain | 10.0 | 0.1 | 100.0 |  |
| `min_output` | Min Output % | 0.0 | 0.0 | 100.0 | % |
| `max_output` | Max Output % | 100.0 | 0.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |
| `reverse_acting` | Reverse Acting | 0.0 | 0.0 | 1.0 | bool |

## Model Predictive Control (Advisory) — `mpc_advisory`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `confidence_threshold` | Confidence Threshold | 0.7 | 0.0 | 1.0 |  |
| `recommendation_interval_sec` | Rec. Interval | 900.0 | 60.0 | 3600.0 | s |
| `setpoint_deadband` | SP Deadband | 0.5 | 0.1 | 5.0 | °F |
| `max_setpoint_adjustment` | Max SP Adj | 2.0 | 0.5 | 5.0 | °F |
| `demand_limit_kw` | Demand Limit | 300.0 | 50.0 | 2000.0 | kW |

## On/Off (Bang-Bang) — `on_off`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 68.0 | 30.0 | 120.0 | °F |
| `deadband` | Deadband | 1.0 | 0.1 | 10.0 | °F |
| `min_on_delay` | Min ON Delay | 60.0 | 0.0 | 3600.0 | s |
| `min_off_delay` | Min OFF Delay | 60.0 | 0.0 | 3600.0 | s |
| `reverse_acting` | Reverse Acting | 0.0 | 0.0 | 1.0 | bool |

## PID — `pid`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 68.0 | 30.0 | 250.0 | °F |
| `kp` | Proportional (Kp) | 4.0 | 0.0 | 50.0 |  |
| `ki` | Integral (Ki) | 0.2 | 0.0 | 5.0 |  |
| `kd` | Derivative (Kd) | 0.0 | 0.0 | 5.0 |  |
| `min_output` | Min Output % | 0.0 | 0.0 | 100.0 | % |
| `max_output` | Max Output % | 100.0 | 0.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |
| `reverse_acting` | Reverse Acting | 0.0 | 0.0 | 1.0 | bool |

## Pool Controller (Gas Heater) — `pool_gas_heater`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `pool_setpoint` | Pool Temp SP | 82.0 | 70.0 | 104.0 | °F |
| `heat_deadband` | Heat Deadband | 2.0 | 0.5 | 5.0 | °F |
| `high_limit` | Heater High Limit | 104.0 | 95.0 | 110.0 | °F |
| `pump_pre_circ_secs` | Pump Pre-Circ | 60.0 | 30.0 | 120.0 | s |
| `pump_post_circ_secs` | Pump Post-Circ | 120.0 | 60.0 | 300.0 | s |
| `ph_setpoint` | pH Setpoint | 7.4 | 7.0 | 7.8 | pH |
| `ph_deadband` | pH Deadband | 0.2 | 0.1 | 0.5 | pH |
| `ph_max_dose_secs` | pH Max Dose | 30.0 | 10.0 | 120.0 | s |
| `ph_lockout_secs` | pH Lockout | 300.0 | 120.0 | 600.0 | s |
| `orp_setpoint` | ORP Setpoint | 700.0 | 600.0 | 800.0 | mV |
| `orp_deadband` | ORP Deadband | 25.0 | 10.0 | 50.0 | mV |
| `orp_max_dose_secs` | ORP Max Dose | 45.0 | 10.0 | 120.0 | s |
| `orp_lockout_secs` | ORP Lockout | 300.0 | 120.0 | 600.0 | s |

## Pool Controller (Heat Pump) — `pool_heat_pump`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `pool_setpoint` | Pool Temp SP | 82.0 | 70.0 | 104.0 | °F |
| `heat_deadband` | Heat Deadband | 2.0 | 0.5 | 5.0 | °F |
| `high_limit_discharge` | Discharge High Limit | 115.0 | 100.0 | 125.0 | °F |
| `low_ambient_lockout` | Low Ambient Lockout | 50.0 | 40.0 | 60.0 | °F |
| `compressor_min_run_secs` | Comp Min Run | 300.0 | 120.0 | 600.0 | s |
| `compressor_min_off_secs` | Comp Min Off | 300.0 | 120.0 | 600.0 | s |
| `defrost_interval_secs` | Defrost Interval | 2700.0 | 1200.0 | 5400.0 | s |
| `defrost_duration_secs` | Defrost Duration | 300.0 | 120.0 | 600.0 | s |
| `defrost_trigger_oat` | Defrost Trigger OAT | 35.0 | 25.0 | 50.0 | °F |
| `ph_setpoint` | pH Setpoint | 7.4 | 7.0 | 7.8 | pH |
| `ph_deadband` | pH Deadband | 0.2 | 0.1 | 0.5 | pH |
| `orp_setpoint` | ORP Setpoint | 700.0 | 600.0 | 800.0 | mV |
| `orp_deadband` | ORP Deadband | 25.0 | 10.0 | 50.0 | mV |

## Pressure Booster Pumps — `pressure_booster`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `target_pressure` | Target Pressure | 84.0 | 40.0 | 150.0 | PSI |
| `wakeup_pressure` | ESS Wakeup Pressure | 78.0 | 30.0 | 140.0 | PSI |
| `ess_charge_pressure` | ESS Charge Pressure | 89.0 | 50.0 | 160.0 | PSI |
| `high_trip_pressure` | High Trip Pressure | 110.0 | 80.0 | 200.0 | PSI |
| `lag_stage_pressure` | Lag Stage Pressure | 74.0 | 30.0 | 140.0 | PSI |
| `lag_stage_delay_secs` | Lag Stage Delay | 15.0 | 0.0 | 120.0 | s |
| `lag_destage_pct` | Lag Destage % | 50.0 | 10.0 | 90.0 | % |
| `lag_destage_delay_secs` | Lag Destage Delay | 30.0 | 5.0 | 300.0 | s |
| `min_speed_hz` | Min Speed | 30.0 | 15.0 | 45.0 | Hz |
| `max_speed_hz` | Max Speed | 60.0 | 45.0 | 60.0 | Hz |
| `ess_min_speed_secs` | ESS Min Speed Timer | 60.0 | 10.0 | 600.0 | s |
| `ess_charge_secs` | ESS Charge Duration | 30.0 | 5.0 | 120.0 | s |
| `ess_bladder_fail_secs` | ESS Bladder Fail Threshold | 45.0 | 5.0 | 300.0 | s |
| `pid_kp` | PID Kp | 4.0 | 0.0 | 50.0 |  |
| `pid_ki` | PID Ki | 0.3 | 0.0 | 5.0 |  |
| `pid_kd` | PID Kd | 0.0 | 0.0 | 5.0 |  |
| `alternation_hours` | Alternation Hours | 100.0 | 1.0 | 1000.0 | hr |
| `suction_low_psi` | Suction Low Trip | 12.0 | 0.0 | 50.0 | PSI |
| `suction_low_delay_secs` | Suction Low Delay | 2.0 | 0.5 | 30.0 | s |
| `overload_amps` | Overload Amps | 20.1 | 5.0 | 50.0 | A |
| `overload_delay_secs` | Overload Delay | 3.0 | 0.5 | 30.0 | s |
| `high_amp_warning` | High Amp Warning | 17.5 | 5.0 | 50.0 | A |
| `high_amp_delay_secs` | High Amp Warning Delay | 30.0 | 5.0 | 120.0 | s |
| `dry_run_hz` | Dry Run Hz Threshold | 54.0 | 30.0 | 60.0 | Hz |
| `dry_run_amps` | Dry Run Amps Threshold | 4.5 | 0.5 | 15.0 | A |
| `dry_run_delay_secs` | Dry Run Delay | 5.0 | 1.0 | 30.0 | s |
| `accel_rate` | Accel Rate | 2.5 | 0.5 | 10.0 | Hz/s |
| `decel_rate` | Decel Rate | 2.5 | 0.5 | 10.0 | Hz/s |
| `ema_alpha` | EMA Filter Alpha | 0.3 | 0.01 | 1.0 |  |

## Residential Boiler — `resi_boiler`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Supply Setpoint | 140.0 | 100.0 | 160.0 | °F |
| `deadband` | Deadband | 5.0 | 1.0 | 15.0 | °F |
| `high_limit` | High Limit | 160.0 | 140.0 | 200.0 | °F |
| `outdoor_lockout` | Outdoor Lockout | 65.0 | 50.0 | 80.0 | °F |
| `min_run_secs` | Min Run Time | 180.0 | 60.0 | 600.0 | s |
| `min_off_secs` | Min Off Time | 180.0 | 60.0 | 600.0 | s |
| `post_purge_secs` | Post-Purge | 60.0 | 0.0 | 300.0 | s |

## Residential Furnace — `resi_furnace`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `heat_setpoint` | Heat Setpoint | 68.0 | 55.0 | 85.0 | °F |
| `cool_setpoint` | Cool Setpoint | 74.0 | 60.0 | 90.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 5.0 | °F |
| `cool_stage2_offset` | Cool Stage 2 Offset | 3.0 | 1.0 | 10.0 | °F |
| `cool_stage2_delay_secs` | Stage 2 Delay | 300.0 | 60.0 | 900.0 | s |
| `min_run_secs` | Min Run Time | 120.0 | 30.0 | 600.0 | s |
| `min_off_secs` | Min Off Time | 120.0 | 30.0 | 600.0 | s |
| `post_purge_secs` | Post-Purge | 90.0 | 0.0 | 300.0 | s |

## Residential Heat Pump — `resi_heat_pump`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `heat_setpoint` | Heat Setpoint | 68.0 | 55.0 | 85.0 | °F |
| `cool_setpoint` | Cool Setpoint | 74.0 | 60.0 | 90.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 5.0 | °F |
| `balance_point` | Balance Point OAT | 25.0 | 5.0 | 40.0 | °F |
| `emergency_lockout_oat` | Emergency Lockout | 35.0 | 15.0 | 50.0 | °F |
| `defrost_interval_secs` | Defrost Interval | 2700.0 | 600.0 | 7200.0 | s |
| `defrost_duration_secs` | Defrost Duration | 120.0 | 30.0 | 300.0 | s |

## Rooftop Unit — `rtu`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `heat_setpoint` | Heat Setpoint | 68.0 | 55.0 | 85.0 | °F |
| `cool_setpoint` | Cool Setpoint | 74.0 | 60.0 | 90.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 5.0 | °F |
| `econ_high_limit` | Econ High Limit | 65.0 | 50.0 | 75.0 | °F |
| `econ_low_limit` | Econ Low Limit | 40.0 | 20.0 | 55.0 | °F |
| `econ_min_pct` | Econ Min % | 15.0 | 0.0 | 30.0 | % |
| `stage2_offset` | Stage 2 Offset | 3.0 | 1.0 | 10.0 | °F |
| `stage2_delay_secs` | Stage 2 Delay | 300.0 | 60.0 | 900.0 | s |
| `min_run_secs` | Min Run Time | 120.0 | 30.0 | 600.0 | s |
| `min_off_secs` | Min Off Time | 120.0 | 30.0 | 600.0 | s |

## Smart Garden Controller — `smart_garden`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `moisture_setpoint` | Soil Moisture SP | 45.0 | 20.0 | 80.0 | %VWC |
| `moisture_deadband` | Moisture DB | 5.0 | 2.0 | 15.0 | %VWC |
| `max_irrigation_secs` | Max Irrigation | 1800.0 | 300.0 | 7200.0 | s |
| `daily_zone_budget_gal` | Zone Budget | 50.0 | 10.0 | 200.0 | gal |
| `daily_total_budget_gal` | Total Budget | 200.0 | 50.0 | 1000.0 | gal |
| `ph_setpoint` | pH Setpoint | 6.2 | 5.5 | 7.0 | pH |
| `ec_setpoint` | EC Setpoint | 1200.0 | 400.0 | 3000.0 | µS/cm |
| `dli_target` | DLI Target | 20.0 | 10.0 | 50.0 | mol/m²/d |
| `frost_heater_on_temp` | Frost On | 38.0 | 32.0 | 45.0 | °F |

## Smart Home Controller — `smart_home`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `cool_sp_occupied` | Cool SP (Occ) | 74.0 | 68.0 | 80.0 | °F |
| `cool_sp_away` | Cool SP (Away) | 78.0 | 72.0 | 85.0 | °F |
| `heat_sp_occupied` | Heat SP (Occ) | 70.0 | 62.0 | 76.0 | °F |
| `heat_sp_away` | Heat SP (Away) | 62.0 | 55.0 | 68.0 | °F |
| `hvac_deadband` | HVAC Deadband | 2.0 | 0.5 | 5.0 | °F |
| `stage2_delay_secs` | Stage 2 Delay | 900.0 | 300.0 | 1800.0 | s |
| `compressor_min_off_secs` | Comp Min Off | 300.0 | 120.0 | 600.0 | s |
| `humidity_high_limit` | Humidity Limit | 65.0 | 55.0 | 75.0 | %RH |
| `interior_occ_timeout_secs` | Occ Timeout | 900.0 | 60.0 | 3600.0 | s |
| `garage_auto_close_secs` | Garage Auto-Close | 900.0 | 300.0 | 3600.0 | s |

## TMC (Temperature Modulation) — `tmc`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 68.0 | 30.0 | 120.0 | °F |
| `thermal_mass` | Thermal Mass | 2.0 | 0.5 | 10.0 |  |
| `brake_factor` | Brake Factor (β) | 3.0 | 1.0 | 10.0 |  |
| `error_gain` | Error Gain (Kp) | 15.0 | 1.0 | 50.0 |  |
| `momentum_gain` | Momentum Gain (Km) | 5.0 | 0.0 | 20.0 |  |
| `sensitivity` | Sensitivity (S) | 0.7 | 0.1 | 3.0 |  |
| `max_decel` | Max Deceleration | 0.8 | 0.1 | 5.0 |  |
| `deadband` | Deadband | 1.0 | 0.1 | 5.0 | °F |
| `max_step` | Max Step/Cycle | 2.0 | 0.5 | 5.0 | % |
| `freeze_limit` | Freeze Limit | 38.0 | 30.0 | 45.0 | °F |
| `high_temp_limit` | High Temp Limit | 120.0 | 100.0 | 140.0 | °F |
| `max_hw_position` | Max HW % | 85.0 | 50.0 | 100.0 | % |
| `max_cw_position` | Max CW % | 100.0 | 50.0 | 100.0 | % |
| `min_oa_position` | Min OA % | 15.0 | 0.0 | 50.0 | % |
| `econ_enable_temp` | Econ Enable OAT | 55.0 | 40.0 | 70.0 | °F |
| `econ_disable_temp` | Econ Disable OAT | 75.0 | 60.0 | 90.0 | °F |

## TMC AHU — `tmc_ahu`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `summer_setpoint` | Summer SAT Setpoint | 55.0 | 45.0 | 65.0 | °F |
| `winter_setpoint` | Winter SAT Setpoint | 68.0 | 55.0 | 80.0 | °F |
| `summer_oat_threshold` | Summer OAT Threshold | 65.0 | 55.0 | 85.0 | °F |
| `winter_oat_threshold` | Winter OAT Threshold | 45.0 | 25.0 | 55.0 | °F |
| `economizer_low_oat` | Economizer Low OAT | 40.0 | 30.0 | 60.0 | °F |
| `economizer_high_oat` | Economizer High OAT | 65.0 | 50.0 | 80.0 | °F |
| `thermal_mass` | Thermal Mass | 2.0 | 0.5 | 10.0 |  |
| `error_gain` | Error Gain (Kp) | 12.0 | 1.0 | 50.0 |  |
| `deadband` | Deadband | 1.5 | 0.1 | 5.0 | °F |
| `integral_gain` | Integral Gain | 0.2 | 0.0 | 5.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.5 | 5.0 | % |
| `min_oa_position` | Min OA % | 15.0 | 0.0 | 50.0 | % |
| `freeze_limit` | Freeze Limit | 35.0 | 30.0 | 45.0 | °F |
| `high_temp_limit` | High Temp Limit | 110.0 | 90.0 | 120.0 | °F |
| `log_interval` | Log Interval | 30.0 | 5.0 | 300.0 | s |

## TMC AHU 4-pipe Lead/Lag — `tmc_ahu_lead_lag`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `summer_setpoint` | Summer SAT Setpoint | 55.0 | 45.0 | 65.0 | °F |
| `winter_setpoint` | Winter SAT Setpoint | 68.0 | 55.0 | 80.0 | °F |
| `summer_oat_threshold` | Summer OAT Threshold | 65.0 | 55.0 | 85.0 | °F |
| `winter_oat_threshold` | Winter OAT Threshold | 45.0 | 25.0 | 55.0 | °F |
| `economizer_low_oat` | Economizer Low OAT | 40.0 | 30.0 | 60.0 | °F |
| `economizer_high_oat` | Economizer High OAT | 65.0 | 50.0 | 80.0 | °F |
| `thermal_mass` | Thermal Mass | 2.0 | 0.5 | 10.0 |  |
| `error_gain` | Error Gain (Kp) | 12.0 | 1.0 | 50.0 |  |
| `deadband` | Deadband | 1.5 | 0.1 | 5.0 | °F |
| `integral_gain` | Integral Gain | 0.2 | 0.0 | 5.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.5 | 5.0 | % |
| `min_oa_position` | Min OA % | 15.0 | 0.0 | 50.0 | % |
| `freeze_limit` | Freeze Limit | 35.0 | 30.0 | 45.0 | °F |
| `high_temp_limit` | High Temp Limit | 110.0 | 90.0 | 120.0 | °F |
| `oat_aux_threshold` | OAT Aux Threshold | 50.0 | 30.0 | 75.0 | °F |
| `cw_pump_demand_on_pct` | CW Pump Demand ON % | 10.0 | 0.0 | 50.0 | % |
| `cw_pump_stage_on_pct` | Stage ON Threshold | 80.0 | 30.0 | 100.0 | % |
| `cw_pump_stage_off_pct` | Stage OFF Threshold | 25.0 | 0.0 | 80.0 | % |
| `cw_pump_stage_on_delay_secs` | Stage ON Delay | 300.0 | 0.0 | 1800.0 | s |
| `cw_pump_stage_off_delay_secs` | Stage OFF Delay | 300.0 | 0.0 | 1800.0 | s |
| `cw_pump_min_run_secs` | CW Pump Min Run | 300.0 | 0.0 | 3600.0 | s |
| `cw_pump_min_off_secs` | CW Pump Min Off | 300.0 | 0.0 | 3600.0 | s |
| `cw_pump_proof_amps` | CW Pump Proof Amps | 0.5 | 0.0 | 50.0 | A |
| `cw_pump_proof_fail_delay_secs` | Proof Fail Delay | 30.0 | 5.0 | 300.0 | s |
| `cw_pump_changeover_enabled` | Weekly Changeover | 1.0 | 0.0 | 1.0 | bool |
| `cw_pump_changeover_interval_secs` | Changeover Interval | 604800.0 | 3600.0 | 2592000.0 | s |

## TMC Chiller — `tmc_chiller`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `cws_setpoint` | CWS Setpoint | 45.0 | 38.0 | 55.0 | °F |
| `deadband` | Deadband | 1.5 | 0.1 | 5.0 | °F |
| `freeze_limit` | Low CW Temp Limit | 36.0 | 30.0 | 45.0 | °F |
| `loop_temp_max` | 2-Pipe Loop Flush Max (0=disabled) | 0.0 | 0.0 | 120.0 | °F |
| `oat_enable_threshold` | OAT Enable Threshold (0=disabled) | 0.0 | 0.0 | 75.0 | °F |
| `min_on_delay` | Min ON Delay | 600.0 | 60.0 | 1800.0 | s |
| `min_off_delay` | Min OFF Delay | 900.0 | 60.0 | 1800.0 | s |
| `condenser_pump_post_run_secs` | Condenser Pump Post-Run | 180.0 | 0.0 | 900.0 | s |
| `mode_lockout` | Mode Lockout (1.0 = winter, plant idle) | 0.0 | 0.0 | 1.0 | bool |

## TMC Chiller (simplified) — `tmc_chiller_simple`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `mode_lockout` | Mode Lockout (1.0 = winter, plant idle) | 0.0 | 0.0 | 1.0 |  |
| `oat_enable_threshold` | OAT Enable Threshold | 50.0 | 0.0 | 80.0 | °F |
| `low_cw_limit` | Freeze Protect (Low CW) | 36.0 | 30.0 | 42.0 | °F |
| `valve_open_delay_secs` | Flow Valve Open → Chiller Delay | 10.0 | 0.0 | 120.0 | s |
| `setpoint` | CWS Setpoint | 45.0 | 35.0 | 60.0 | °F |

## TMC Comfort Boiler — `tmc_comfort_boiler`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `max_hws_setpoint` | Max HWS Setpoint | 180.0 | 120.0 | 220.0 | °F |
| `min_hws_setpoint` | Min HWS Setpoint | 140.0 | 100.0 | 180.0 | °F |
| `oat_low` | OAT Low | 0.0 | -30.0 | 40.0 | °F |
| `oat_high` | OAT High | 65.0 | 40.0 | 80.0 | °F |
| `deadband` | Deadband | 3.0 | 0.5 | 10.0 | °F |
| `mode_lockout` | Mode Lockout (1.0 = summer, plant idle) | 0.0 | 0.0 | 1.0 | bool |
| `error_gain` | Error Gain | 8.0 | 0.1 | 50.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |

## TMC DOAS + DX + Season Relay — `tmc_doas_changeover`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `summer_setpoint` | Summer SAT Setpoint | 55.0 | 45.0 | 70.0 | °F |
| `winter_setpoint` | Winter SAT Setpoint | 65.0 | 55.0 | 80.0 | °F |
| `summer_oat_threshold` | Summer OAT Threshold | 65.0 | 55.0 | 85.0 | °F |
| `winter_oat_threshold` | Winter OAT Threshold | 45.0 | 25.0 | 55.0 | °F |
| `deadband` | Heat Deadband | 1.5 | 0.1 | 5.0 | °F |
| `stage1_deadband` | DX1 Deadband | 2.0 | 0.5 | 6.0 | °F |
| `dx1_oat_lockout` | DX1 OAT Lockout | 60.0 | 40.0 | 75.0 | °F |
| `min_runtime_secs` | DX Min Runtime | 420.0 | 60.0 | 1800.0 | s |
| `min_offtime_secs` | DX Min Offtime | 420.0 | 60.0 | 1800.0 | s |
| `freeze_limit` | Freeze Protect SAT | 38.0 | 30.0 | 45.0 | °F |
| `sat_high_limit` | High SAT Limit | 100.0 | 80.0 | 120.0 | °F |
| `suction_low_limit` | Suction Low Temp | 34.0 | 20.0 | 45.0 | °F |
| `suction_fault_delay` | Suction Fault Delay | 180.0 | 60.0 | 600.0 | s |
| `suction_lockout_secs` | Suction Lockout Duration | 600.0 | 120.0 | 1800.0 | s |

## TMC Direct-Fired DOAS + DX — `tmc_doas_dx`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `summer_setpoint` | Summer Setpoint | 55.0 | 45.0 | 65.0 | °F |
| `winter_setpoint` | Winter Setpoint | 65.0 | 55.0 | 80.0 | °F |
| `summer_oat_threshold` | Summer OAT | 65.0 | 55.0 | 85.0 | °F |
| `winter_oat_threshold` | Winter OAT | 45.0 | 25.0 | 55.0 | °F |
| `deadband` | Deadband | 1.0 | 0.1 | 5.0 | °F |
| `dx_stage1_on_offset` | DX1 ON Offset | 1.0 | 0.1 | 5.0 | °F |
| `dx_stage2_on_delay_secs` | DX2 ON Delay | 600.0 | 30.0 | 1800.0 | s |
| `freeze_limit` | Freeze Limit | 40.0 | 30.0 | 45.0 | °F |
| `max_hw_position` | Max HW % | 100.0 | 50.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |
| `hw_error_gain` | HW Error Gain | 15.0 | 1.0 | 50.0 |  |

## TMC Domestic Boiler — `tmc_domestic_boiler`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `dhw_setpoint` | DHW Setpoint | 140.0 | 110.0 | 160.0 | °F |
| `deadband` | Deadband | 5.0 | 0.5 | 15.0 | °F |
| `dhw_high_limit` | DHW High Limit | 160.0 | 140.0 | 180.0 | °F |
| `min_on_delay` | Min ON Delay | 120.0 | 30.0 | 1800.0 | s |
| `min_off_delay` | Min OFF Delay | 120.0 | 30.0 | 1800.0 | s |

## TMC Electric Heat — `tmc_electric_heat`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 70.0 | 55.0 | 85.0 | °F |
| `deadband` | Deadband | 1.0 | 0.1 | 3.0 | °F |
| `stage_1_on_offset` | Stage 1 ON Offset | 1.0 | 0.1 | 5.0 | °F |
| `stage_2_on_delay_secs` | Stage 2 ON Delay | 300.0 | 30.0 | 1800.0 | s |
| `stage_3_on_delay_secs` | Stage 3 ON Delay | 600.0 | 30.0 | 1800.0 | s |
| `min_on_delay` | Min ON Delay | 120.0 | 30.0 | 1800.0 | s |

## TMC Greenhouse — `tmc_greenhouse`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `day_setpoint` | Day Setpoint | 72.0 | 55.0 | 85.0 | °F |
| `night_setpoint` | Night Setpoint | 60.0 | 40.0 | 75.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 10.0 | °F |
| `max_hw_position` | Max HW % | 100.0 | 50.0 | 100.0 | % |
| `max_cw_position` | Max CW % | 100.0 | 50.0 | 100.0 | % |
| `vent_open_threshold` | Vent Open Threshold | 78.0 | 65.0 | 95.0 | °F |
| `error_gain` | Error Gain | 15.0 | 1.0 | 50.0 |  |
| `max_step` | Max Step/Cycle | 3.0 | 0.5 | 10.0 | % |

## TMC Natatorium — `tmc_natatorium`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `space_setpoint` | Space Setpoint | 84.0 | 75.0 | 92.0 | °F |
| `rh_setpoint` | RH Setpoint | 55.0 | 35.0 | 70.0 | % |
| `rh_deadband` | RH Deadband | 5.0 | 1.0 | 15.0 | % |
| `deadband` | Deadband | 1.0 | 0.5 | 5.0 | °F |
| `space_above_pool_offset` | Space Above Pool Offset | 2.0 | 0.0 | 5.0 | °F |
| `error_gain` | Error Gain | 15.0 | 1.0 | 50.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.5 | 10.0 | % |

## TMC Steambundle — `tmc_steambundle`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `max_hws_setpoint` | Max HWS Setpoint | 180.0 | 120.0 | 220.0 | °F |
| `min_hws_setpoint` | Min HWS Setpoint | 140.0 | 100.0 | 180.0 | °F |
| `oat_low` | OAT Low | 0.0 | -30.0 | 40.0 | °F |
| `oat_high` | OAT High | 65.0 | 40.0 | 80.0 | °F |
| `deadband` | Deadband | 3.0 | 0.5 | 10.0 | °F |
| `mode_lockout` | Mode Lockout (1.0 = summer, plant idle) | 0.0 | 0.0 | 1.0 | bool |
| `error_gain` | Error Gain | 12.0 | 0.1 | 50.0 |  |
| `max_step` | Max Step/Cycle | 2.0 | 0.1 | 10.0 | % |
| `max_valve_position` | Max Valve % | 100.0 | 50.0 | 100.0 | % |

## TMC VAV — `tmc_vav`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 72.0 | 60.0 | 85.0 | °F |
| `deadband` | Deadband | 0.5 | 0.1 | 3.0 | °F |
| `error_gain` | Error Gain | 15.0 | 1.0 | 50.0 |  |
| `damper_min_pct` | Damper Min % | 10.0 | 0.0 | 50.0 | % |
| `damper_max_pct` | Damper Max % | 100.0 | 20.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 3.0 | 0.5 | 10.0 | % |

## TMC VAV + DX — `tmc_vav_dx`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | Setpoint | 72.0 | 60.0 | 85.0 | °F |
| `deadband` | Deadband | 0.5 | 0.1 | 3.0 | °F |
| `error_gain` | Error Gain | 15.0 | 1.0 | 50.0 |  |
| `damper_min_pct` | Damper Min % | 10.0 | 0.0 | 50.0 | % |
| `damper_max_pct` | Damper Max % | 100.0 | 20.0 | 100.0 | % |
| `max_step` | Max Step/Cycle | 3.0 | 0.5 | 10.0 | % |
| `dx_stage1_on_offset` | DX1 ON Offset | 1.5 | 0.1 | 5.0 | °F |
| `dx_stage1_off_offset` | DX1 OFF Offset | 0.5 | 0.1 | 3.0 | °F |

## Zone Reheat — `tmc_zone_reheat`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `default_setpoint` | Setpoint | 72.0 | 60.0 | 85.0 | °F |
| `heat_on_threshold` | Heat ON | 1.5 | 0.1 | 5.0 | °F |
| `heat_off_threshold` | Heat OFF | 0.5 | 0.1 | 3.0 | °F |
| `cool_on_threshold` | Cool ON | 1.0 | 0.1 | 5.0 | °F |
| `cool_off_threshold` | Cool OFF | 0.5 | 0.1 | 3.0 | °F |
| `cool_air_threshold` | Cool-Air Available Threshold | 68.0 | 40.0 | 80.0 | °F |
| `damper_min_pct` | Damper Min % | 3.0 | 0.0 | 50.0 | % |
| `damper_max_pct` | Damper Max % | 100.0 | 20.0 | 100.0 | % |
| `damper_band` | Damper Band | 5.0 | 0.5 | 20.0 | °F |
| `damper_max_voltage` | Damper Max Voltage | 10.0 | 1.0 | 10.0 | V |
| `max_step` | Max Step/Cycle | 3.0 | 0.5 | 10.0 | % |
| `log_interval` | Log Interval | 30.0 | 5.0 | 300.0 | s |
| `use_incoming_as_supply` | Use Incoming as Supply (UI hint) | 0.0 | 0.0 | 1.0 | bool |

## VFD Pump Pack — `vfd_pump_pack`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `pressure_setpoint` | Pressure SP | 45.0 | 10.0 | 100.0 | PSI |
| `deadband` | Deadband | 2.0 | 0.5 | 10.0 | PSI |
| `kp` | Proportional Gain | 4.0 | 0.5 | 20.0 |  |
| `ki` | Integral Gain | 0.3 | 0.01 | 2.0 |  |
| `min_speed_pct` | Min Speed | 20.0 | 0.0 | 50.0 | % |
| `max_speed_pct` | Max Speed | 100.0 | 50.0 | 100.0 | % |
| `lag_on_speed_pct` | Lag ON Speed | 85.0 | 50.0 | 100.0 | % |
| `lag_off_speed_pct` | Lag OFF Speed | 40.0 | 10.0 | 70.0 | % |
| `lag_on_delay_secs` | Lag ON Delay | 120.0 | 30.0 | 600.0 | s |
| `deadhead_pressure` | Dead-head PSI | 80.0 | 50.0 | 150.0 | PSI |

## Water-Cooled Chiller — `water_cooled_chiller`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `setpoint` | CHW Supply SP | 44.0 | 38.0 | 55.0 | °F |
| `deadband` | Deadband | 2.0 | 0.5 | 5.0 | °F |
| `stage_on_delay_secs` | Stage ON Delay | 300.0 | 60.0 | 1800.0 | s |
| `stage_off_delay_secs` | Stage OFF Delay | 300.0 | 60.0 | 1800.0 | s |
| `freeze_lockout_temp` | Freeze Lockout | 38.5 | 30.0 | 45.0 | °F |
| `pump_oat_threshold` | Pump OAT Threshold | 55.0 | 40.0 | 80.0 | °F |

## Water Monitor (City) — `water_monitor_city`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `max_shower_duration_secs` | Max Shower Time | 900.0 | 300.0 | 1800.0 | s |
| `max_shower_volume_gal` | Max Shower Vol | 30.0 | 10.0 | 60.0 | gal |
| `fixture_lockout_secs` | Fixture Lockout | 600.0 | 300.0 | 3600.0 | s |
| `daily_budget_gal` | Daily Budget | 150.0 | 50.0 | 500.0 | gal |
| `daily_fixture_budget_gal` | Fixture Budget | 50.0 | 20.0 | 150.0 | gal |
| `scald_limit` | Scald Limit | 120.0 | 105.0 | 130.0 | °F |
| `low_pressure_threshold` | Low Pressure | 20.0 | 10.0 | 30.0 | PSI |
| `leak_detection_flow` | Leak Flow | 0.5 | 0.1 | 1.0 | GPM |
| `leak_detection_secs` | Leak Duration | 300.0 | 60.0 | 900.0 | s |

## Water Monitor (Well) — `water_monitor_well`

| Param | Label | Default | Min | Max | Unit |
|---|---|---|---|---|---|
| `max_shower_duration_secs` | Max Shower Time | 900.0 | 300.0 | 1800.0 | s |
| `max_shower_volume_gal` | Max Shower Vol | 30.0 | 10.0 | 60.0 | gal |
| `daily_budget_gal` | Daily Budget | 150.0 | 50.0 | 500.0 | gal |
| `scald_limit` | Scald Limit | 120.0 | 105.0 | 130.0 | °F |
| `well_cut_in_pressure` | Well Cut-In | 30.0 | 20.0 | 40.0 | PSI |
| `well_cut_out_pressure` | Well Cut-Out | 50.0 | 40.0 | 60.0 | PSI |
| `well_max_runtime_secs` | Well Max Run | 1800.0 | 600.0 | 3600.0 | s |
| `well_min_off_secs` | Well Min Off | 60.0 | 30.0 | 180.0 | s |
| `daily_well_draw_limit_gal` | Well Daily Limit | 200.0 | 50.0 | 1000.0 | gal |

