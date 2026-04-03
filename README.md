# Electricity Anomaly Detection Dataset

## Dataset Overview

This dataset is designed for electricity theft detection, containing normal electricity consumption data and six types of typical anomaly (theft) behaviors. The total sample size is 7,000, with balanced numbers across categories.

- **Normal samples**: 1,000
- **Anomaly samples**: 6,000 in total, 1,000 for each of the six anomaly types

Each sample represents a user's load data over a 24‑hour period. The sampling interval is 15 minutes, so each sample consists of 96 consecutive load values (unit: kW or normalized, depending on the original data).

## Anomaly Type Description

| Anomaly Type         | Label                  | Description |
|----------------------|------------------------|-------------|
| Dynamic Reduction    | Dynamic Reduction      | Load curve is randomly and dynamically reduced with varying amplitude, simulating irregular theft behavior. |
| Peak Clipping        | Peak Clipping          | High peaks in the load curve are clipped below a certain threshold, simulating avoidance of peak consumption records. |
| Random Reduction     | Random Reduction       | Randomly selects multiple time points and reduces the load values by a random proportion. |
| Single‑Point Zeroing | Single‑Point Zeroing   | Sets a single sampling point’s load value to zero. |
| Peak Shifting        | Peak Shifting          | Shifts peak load values within a time window forward or backward, altering the load distribution pattern. |
| Interval Zeroing     | Interval Zeroing       | Sets load values in a continuous interval of sampling points to zero. |

## Data Format

- **Recording period**: 24 hours
- **Sampling interval**: 15 minutes
- **Points per sample**: 24 × (60 / 15) = 96

### Typical Data Structure

| Field       | Type           | Description |
|-------------|----------------|-------------|
| `id`        | int            | Unique sample identifier (optional) |
| `label`     | int / str      | Class label: 0 for normal, 1–6 for the six anomaly types (or using anomaly name strings) |
| `load_curve`| list[float]    | Load sequence of length 96, ordered by time |

> Note: Actual field names may vary slightly depending on file format (CSV/JSON/Excel). Please refer to the actual data files.

## Use Cases

- Binary classification: normal vs. anomaly (theft)
- Multi‑class classification: identify the specific theft technique (6 anomaly types)
- Anomaly detection: train only on normal data to detect any deviation from normal patterns

## Important Notes

1. The load data may have been normalized; please refer to the original data source for absolute units.
2. The anomalies are synthetically injected; real‑world theft behaviors can be more complex, so careful evaluation of model generalization is advised.
3. The dataset is balanced across categories, but in real scenarios anomaly samples are rare. When evaluating, focus on precision, recall, F1‑score, etc.

## Citation & License

Please comply with the usage terms provided by the data distributor. If you use this dataset in academic research, it is recommended to cite the original source (if any).

---

*Last updated: April 2026*
