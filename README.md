# Real-Time Classroom Monitoring (Midterm Project)

A simulated classroom sensor sends a reading every minute (temperature, humidity, CO₂).
The program processes each reading as it arrives. It calculates live statistics, detects
problems, shows a live table, and saves the results.

## Files
- `midterm.ipynb`: the project (code and explanations)
- `requirements.txt`: required libraries

Running the notebook creates:
- `results.csv`: all readings with indicators
- `alerts.csv`: only the readings that triggered an alert
- `results.png`: the chart

## Installation
```bash
python -m venv .venv
.venv\Scripts\activate          # Windows  (macOS/Linux: source .venv/bin/activate)
pip install -r requirements.txt
```

## How to run
1. Open `midterm.ipynb` in VS Code or Jupyter.
2. Select the `.venv` kernel.
3. Click **Run All**. The stream takes about 10 seconds. Change `DELAY` in the settings cell to make it faster or slower.

## What it does
- **Data generator:** `sensor_stream()` yields one reading at a time. It includes missing values and spikes, and uses a fixed seed so every run gives the same data.
- **Indicators:** moving average, rolling standard deviation, rolling min/max, and the alert count.
- **Alerts:** `HIGH_TEMP` (above 27 °C), `HIGH_CO2` (above 1000 ppm), `SPIKE` (more than 3 °C away from the moving average), `MISSING_VALUE`.
