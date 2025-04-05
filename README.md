# assignment5_statistical_seismology

## Assignment Write-up: Zaliapin–Zion Earthquake Declustering

The **Zaliapin–Zion declustering algorithm** is a physics-based method designed to distinguish between background seismicity and clustered aftershocks in earthquake catalogs. The method assumes that aftershocks tend to be closer in space and time to their triggering mainshock, whereas background events are more randomly distributed. This distinction is quantified using a distance metric **η (eta)**, which incorporates spatial, temporal, and magnitude-dependent factors.

In this assignment, we implement the Zaliapin–Zion declustering algorithm using a dataset of seismic events in Greece. Each seismic event is described by its timestamp, geographic coordinates (latitude and longitude), and magnitude. The η value for each event is computed with respect to all prior events using the formula:

$$
\eta = \frac{r}{10^{-bM}} \cdot t^q
$$

Where:
- \( r \) is the spatial distance between events (computed using the Haversine formula),
- \( M \) is the magnitude of the event,
- \( t \) is the time difference between events (in days),
- \( b \) and \( q \) are empirical constants, commonly set as \( b = 1.0 \) and \( q = 0.5 \).

The **minimum η** value is extracted for each event. By taking the logarithm of η, we separate the seismic events into two populations: events with **log₁₀(η) < 4.0** are categorized as **aftershocks**, while those with **log₁₀(η) ≥ 4.0** are considered **background events**.

The results include a histogram showing the distribution of log₁₀(η) values and a clear distinction between clustered and background seismicity. Additionally, the aftershocks are plotted on an interactive map of Greece to visually analyze their spatial distribution. This implementation validates the effectiveness of the Zaliapin–Zion method in earthquake declustering and provides valuable insights into regional seismic patterns.

