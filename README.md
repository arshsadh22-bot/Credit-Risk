
Hazard_rate_model


Overview:
A Python-based hazard rate model that constructs cumulative default probability (PD) term structures across 17 rating grades (AAA to CCC) using the standard survival function:
PD(t) = 1 − e^(−λt)
The model introduces a portfolio-level adjustment factor that rescales the global S&P intensity curve to reflect a specific portfolio's observed default experience illustrating how PD term structures shift when your portfolio deviates from the global rating scale.


Key Features:
Computes cumulative PD for up to t years across all 17 rating grades
Three-panel visualisation: original PDs, adjusted PDs, and the divergence between them
Demonstrates convergence behaviour showing how adjusted and original curves reconverge faster for lower-rated obligors (CCC) than investment-grade ones (AAA)


Methodology:
Base λ values are derived from S&P historical default rates per rating grade. The adjustment factor is computed as:
adj_factor = portfolio observed default rate / long-run global default rate
Applying this scalar to λ shifts the entire intensity curve proportionally — a factor below 1 compresses PDs downward (portfolio safer than global scale implies), a factor above 1 shifts them upward (portfolio riskier). This is a simplified illustration of portfolio-level anchoring before grade-level IRB calibration.


Regulatory Context:
Conceptually aligned with Basel IRB through-the-cycle to point-in-time PD adjustment
Relevant to IFRS-9 lifetime PD estimation for ECL staging
Convergence behaviour reflects the mathematical property that all positive-hazard-rate survival curves must eventually reach certainty of default


Tools and Libraries:
Python 3.x
Pandas
NumPy
Matplotlib


How to Run:
Clone the repository or download the .ipynb file
Open in Jupyter Notebook or JupyterLab
Run all cells


Limitations:
The adjustment factor is a portfolio-level scalar. In production IRB environments, calibration is performed at the rating grade level
Base λ values reflect S&P global default experience and may not represent any specific sector, jurisdiction, or credit cycle
Model is intended as a pedagogical and analytical tool, not a production calibration methodology


