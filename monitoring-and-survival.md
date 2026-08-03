# Reforestation Manual: Monitoring & Survival Tracking

*Detailed operational companion to [../REFORESTATION.md](../REFORESTATION.md#impact-measurement). **Status:** describes the monitoring model designed for the Phase 2 pilot (see [../ROADMAP.md](../ROADMAP.md#phase-2--validation-2026-q4--2027-q1)) — the first verified batch of tracked trees is a Phase 2 success metric, not a result already in hand.*

## Why Monitoring Matters More Than Planting Counts

A planted tree that dies within a year isn't impact — it's a data point about what didn't work. CeloHT's public reporting (see [../METRICS.md](../METRICS.md#core-metrics)) always pairs "trees planted" with a verified survival rate, which means monitoring has to be built into the program from day one, not added later as an afterthought.

## Logging Standard

Every planting event (see [planting-methodology.md](./planting-methodology.md#data-logged-per-event)) is logged with a unique event ID, GPS coordinates (point for sparse plantings, boundary polygon for dense clusters), species, quantity, and date. This log is the baseline every future monitoring check compares against.

## Monitoring Checkpoints

| Checkpoint | Timing | What's Assessed |
|---|---|---|
| Initial establishment check | 30 days post-planting | Basic survival, watering adequacy, pest/damage signs |
| 6-month check | 6 months post-planting | Survival count, growth signs, site condition |
| 18-month check (primary reporting checkpoint) | 18 months post-planting | Confirmed survival rate — this is the figure reported publicly per [../METRICS.md](../METRICS.md#core-metrics) |

## Who Conducts Monitoring

Community members trained alongside nursery leads (see [nursery-operations.md](./nursery-operations.md#nursery-lead-training)) conduct routine checks; a Reforestation Working Group coordinator conducts periodic independent spot-verification against community-reported figures, consistent with the verification principle in [../REFORESTATION.md](../REFORESTATION.md#methodology).

## Data Recorded Per Checkpoint

- Event ID (linking back to the original planting log)
- Count surviving vs. originally planted
- Cause of loss where identifiable (drought, pest, livestock damage, human disturbance) — loss causes are logged honestly, since they directly inform site and species selection improvements for future plantings
- Photo documentation
- Assessor name/role

## Independent Spot-Verification

To guard against overreporting, a coordinator not involved in the routine monitoring for a given site conducts an independent count on a sample of sites each cycle. Discrepancies between community-reported and independently-verified figures are documented and published, not smoothed over — consistent with the honesty principle in [../METRICS.md](../METRICS.md#corrections-policy).

## GIS Integration

Planting and monitoring locations feed a shared map, allowing anyone to see where activity has actually occurred rather than relying on aggregate counts alone. See [../REFORESTATION.md](../REFORESTATION.md#gis-integration).

## Satellite Monitoring (Future)

For larger planting areas as the program scales past the pilot phase, satellite-based vegetation monitoring (e.g. NDVI analysis) is planned as a supplement to ground-based checks — see [../REFORESTATION.md](../REFORESTATION.md#satellite-monitoring-concepts) and [../ROADMAP.md](../ROADMAP.md). This is not yet in use during the pilot phase.

## Reporting

Confirmed 18-month survival data feeds directly into [../METRICS.md](../METRICS.md#core-metrics) and CeloHT's quarterly/annual impact reporting. Cumulative reforestation impact (total trees, verified survival rate) is a named success metric for [Phase 4 of the roadmap](../ROADMAP.md#phase-4--maturity-2028).

## References

- [../REFORESTATION.md](../REFORESTATION.md)
- [planting-methodology.md](./planting-methodology.md)
- [../METRICS.md](../METRICS.md)
