# NIT Calicut Campus Shuttle Optimization

A small operations-analysis portfolio project exploring how NIT Calicut could improve campus-shuttle reliability on the Mega Boys Hostel (MBH) → Main Campus route without adding buses.

## Executive summary

The project combines field observations, timetable review, descriptive analysis, and a proposed 12:00–14:00 service pattern.

- **Morning:** standardize dispatch behaviour after normal boarding rather than allowing unplanned additional wait-to-fill time.
- **12:00–14:00:** pilot an interleaved sequence — AC → Regular Bus 1 → Regular Bus 2 — at 10-minute intervals.
- **Trade-off:** the timetable comparison estimates 632 theoretical passenger-spaces in the current schedule versus 568 in the proposal (64 fewer, about 10.1% lower). This is scheduled capacity, not a measured passenger count; monitor crowding during any pilot.
- **Evidence limits:** observations are small and unevenly distributed across time periods. There are no observations for 09:00–12:00 or after 14:00 in the diagnostic summary, and the project does not establish causation.

## Repository structure

```text
NIT_Calicut_Shuttle_Optimization_GitHub/
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
├── data/
│   ├── README.md
│   └── shuttle_observations_and_analysis.xlsx
├── src/
│   └── shuttle_analysis.py
├── docs/
│   └── data_dictionary.md
├── outputs/
│   └── .gitkeep
└── deliverables/
    ├── consulting_presentation.pptx
    └── project_report.pdf
```

## Run the analysis

Requires Python 3.9+.

### Windows (Command Prompt)

```bat
cd /d "C:\path\to\NIT_Calicut_Shuttle_Optimization_GitHub"
py -m pip install -r requirements.txt
py src\shuttle_analysis.py
```

### macOS / Linux

```bash
cd /path/to/NIT_Calicut_Shuttle_Optimization_GitHub
python3 -m pip install -r requirements.txt
python3 src/shuttle_analysis.py
```

By default, the script reads `data/shuttle_observations_and_analysis.xlsx`, prints a summary, and writes CSV outputs to `outputs/`. To use another workbook:

```bash
python src/shuttle_analysis.py --workbook path/to/workbook.xlsx --output-dir outputs
```

## What the script does

1. Checks that the workbook contains the expected observation and timetable sheets.
2. Reads the raw observation block from `Sheet1` and computes descriptive metrics where source values are present: arrival deviation, departure deviation, dwell time, passenger count, occupancy, and over-capacity observations.
3. Computes the current/proposed 12:00–14:00 scheduled passenger-space comparison using the documented fleet capacities and trip counts.
4. Exports `observation_summary.csv`, `occupancy_observations.csv`, and `capacity_comparison.csv`.

The workbook contains manually assembled analysis and source observations. The script deliberately reports missing values as missing rather than zero and does not infer missing timestamps or claim causal relationships.

## Main recommendation

Pilot the morning dispatch standard and the proposed 12:00–14:00 interleaved pattern. Compare schedule adherence, 10-minute headway adherence, occupancy, and frequency of crowding against the baseline before making the timetable permanent.

## Suggested GitHub description

**Operations-analysis project using Excel and Python to diagnose campus shuttle reliability and evaluate a fleet-neutral timetable proposal at NIT Calicut.**

## Before publishing publicly

Review the workbook and any observation notes for information you do not want public. This repository includes the project workbook and summary deliverables; publish only if you have permission to share the underlying data. The analysis is an academic portfolio project, not an official NIT Calicut operational recommendation.
