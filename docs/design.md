**Title:** A/B Test — Revenue & Conversion Impact of Variant B

## Metrics
- **Primary (OEC):** CVR = users with revenue > 0 / users
- **Secondary:** RPU; AOV among converters
- **Guardrails:** N/A
- **Unit:** User-level; one arm per user

## Stats Plan
- α=0.05 (two-sided), power=0.8, fixed-horizon
- **SRM:** chi-square vs 50/50; p < 0.01 → invalid (stop)
- **CVR:** two-proportion z-test; 95% CI for absolute lift
- **RPU:** Welch’s t-test + percentile bootstrap CI; report medians
- **Decision:** Ship if CI>0 and abs lift ≥ +0.3pp; else iterate; negative/no SRM → no-ship
- **CUPED:** Only if pre-period covariate exists

## Power / MDE
MDE default **+0.5pp** absolute. Per-arm n:
n ≈ 2 * p̄ (1−p̄) * (z_{0.975}+z_{0.8})² / δ², with z_{0.975}=1.96, z_{0.8}=0.84.

## Data Quality
- Enforce unique user assignment (first assignment wins; earliest by date if present)
- Document drops/typing fixes
