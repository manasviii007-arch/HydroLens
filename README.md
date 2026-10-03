🌾 HydroLens

Satellite-Powered Agricultural Water & Climate Intelligence

<p align="center">
  <b>“See the Risk. Plan Before the Loss.”</b>
</p><p align="center">
  <img src="https://img.shields.io/badge/Hackathon-Schneider%20Electric%20Yuva%20Yodha-00D2FF?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Challenge-01%20%7C%20Sustainable%20Agriculture-00E5C0?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Geospatial-Satellite%20Analytics-2E7D32?style=for-the-badge" />
</p><p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-problem">Problem</a> •
  <a href="#-solution">Solution</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-quick-start">Quick Start</a>
</p>---

🚀 Overview

HydroLens is a satellite-powered agricultural water and climate intelligence platform designed for Farmer Producer Organizations (FPOs), water cooperatives, and agricultural decision-makers.

Instead of relying primarily on expensive field-level sensor deployment, HydroLens combines:

- 🛰️ Multispectral satellite observations
- 🌦️ Weather and forecast signals
- 🌱 Crop-stage intelligence
- 💧 Water availability
- ☀️ Solar pumping capacity
- 🤖 Predictive analytics
- 🔀 Constraint-based optimization

to transform raw environmental data into community-scale risk maps, water-allocation recommendations, scenario simulations, and actionable farmer alerts.

The core idea

«Detect water stress → predict what happens next → simulate constraints → prioritize scarce resources → coordinate irrigation before crop damage becomes critical.»

---

🎯 The Problem

Agricultural water decisions are often made with incomplete visibility.

A farmer may understand their own field, but an FPO or regional water manager may need to coordinate resources across hundreds of fields simultaneously.

During:

- prolonged dry spells,
- heatwaves,
- irregular rainfall,
- groundwater stress, or
- limited irrigation availability,

the key question becomes:

«“Which fields need limited water first, and what happens if the available water is not enough?”»

Traditional field monitoring can become difficult and expensive across fragmented smallholder farms.

HydroLens addresses this community-level visibility and prioritization gap using satellite-derived indicators and predictive decision support.

---

💡 Our Solution

HydroLens converts satellite and environmental signals into a decision-support layer for agricultural water management.

4 interconnected intelligence pillars

Module| What it does
🌊 Community Water Risk| Maps vegetation and water-stress indicators across contiguous agricultural blocks
🔮 Scenario Engine| Simulates drought/heatwave conditions and limited-water scenarios
☀️ Resource Prioritization| Prioritizes vulnerable fields while considering available water and solar pumping windows
🌾 Harvest & Residue Intelligence| Forecasts harvest windows and helps anticipate storage, transport and residue-management bottlenecks

---

🌊 01 — Community Water Risk

HydroLens processes multispectral satellite imagery to derive vegetation and water-related indicators such as:

NDVI — Vegetation Vigor

NDVI = (NIR - RED) / (NIR + RED)

Used as an indicator of vegetation health and canopy vigor.

NDWI — Water-Related Vegetation Signal

NDWI = (NIR - SWIR) / (NIR + SWIR)

Used to derive a water-related vegetation signal and identify spatial changes associated with moisture stress.

HydroLens combines these signals with spatial boundaries and temporal observations to identify areas requiring further attention.

«Important: Satellite indices are indicators, not direct measurements of root-zone soil moisture. HydroLens treats them as inputs to a broader risk model rather than as ground-truth measurements.»

---

🔮 02 — Scenario Engine

What happens if a farming block experiences a 5–14 day dry spell?

What if the available water reserve is limited?

What if several fields enter stress simultaneously?

HydroLens allows an FPO manager to model scenarios such as:

Available Water
       ↓
Weather / Dry Spell
       ↓
Crop Vulnerability
       ↓
Projected Stress
       ↓
Resource Allocation
       ↓
Expected Impact

Example:

Scenario:
5-day heatwave
100 farming plots
100,000 L shared water reserve

        ↓

HydroLens evaluates:
• field vulnerability
• crop stage
• projected stress
• water demand
• available resource

        ↓

Output:
Prioritized irrigation allocation
+ projected risk
+ affected fields
+ resource utilization

---

☀️ 03 — Risk-Based Resource Prioritization

When water is scarce, equal allocation does not necessarily minimize crop damage.

HydroLens uses a constraint-based optimization layer to prioritize fields according to factors such as:

- Current risk level
- Crop stage
- Vegetation condition
- Estimated moisture deficit
- Available water
- Irrigation demand
- Solar pumping availability

The optimization objective can be represented as:

Minimize:
    Total Crop Stress Impact

Subject to:
    Water Reserve ≤ Available Water
    Pump Capacity ≤ Available Pump Capacity
    Irrigation Schedule ≤ Available Time Window

This converts HydroLens from a monitoring dashboard into a resource decision-support system.

---

☀️ Solar-Aware Irrigation

HydroLens can incorporate available solar-generation windows into irrigation scheduling.

Example:

11:30 AM ───────────────────── 02:30 PM
              ☀️
       Peak Solar Window
              ↓
      Irrigation Queue
              ↓
      Priority Fields

The goal is to coordinate water pumping with renewable-energy availability where the local infrastructure supports it, potentially reducing reliance on diesel-powered pumping.

---

🌾 04 — Harvest & Residue Intelligence

Water stress is not the only operational problem.

A concentrated harvest window can create downstream bottlenecks:

Field Risk
    ↓
Harvest Prediction
    ↓
Expected Harvest Volume
    ↓
┌───────────┬────────────┬──────────────┐
│ Storage   │ Transport  │ Residue Mgmt │
└───────────┴────────────┴──────────────┘

HydroLens aims to provide early visibility so FPOs can coordinate resources before harvest pressure peaks.

---

🛰️ System Architecture

                         HYDROLENS
                            │
                            ▼
              ┌─────────────────────────┐
              │    DATA INGESTION       │
              ├─────────────────────────┤
              │ Sentinel-2               │
              │ Landsat                  │
              │ Weather / Forecast Data  │
              │ Spatial Data              │
              │ ET / Soil Signals         │
              └────────────┬────────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │  GEOSPATIAL PROCESSING  │
              ├─────────────────────────┤
              │ Raster Processing        │
              │ NDVI / NDWI              │
              │ Cloud / Spatial Masks    │
              │ Field-level Aggregation  │
              └────────────┬────────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │   ML / ANALYTICS CORE   │
              ├─────────────────────────┤
              │ Risk Estimation          │
              │ Time-Series Analysis     │
              │ Moisture Trend           │
              │ Harvest Forecasting      │
              └────────────┬────────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │ SCENARIO + OPTIMIZATION │
              ├─────────────────────────┤
              │ Drought Simulation       │
              │ Water Constraints        │
              │ Solar Constraints        │
              │ OR-Tools Optimization    │
              └────────────┬────────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │     DECISION LAYER      │
              ├─────────────────────────┤
              │ FPO Dashboard            │
              │ Risk Map                 │
              │ Scenario Simulator       │
              │ Irrigation Priority      │
              └────────────┬────────────┘
                           │
                           ▼
              ┌─────────────────────────┐
              │      FARMER LAYER       │
              ├─────────────────────────┤
              │ WhatsApp Alerts          │
              │ SMS Notifications        │
              │ Irrigation Slots         │
              │ Action Recommendations   │
              └─────────────────────────┘

---

🏗️ Technical Architecture

1. Data Ingestion Layer

Sentinel-2
    │
Landsat-9
    │
Weather Data
    │
Spatial Layers
    │
    ▼
Data Normalization

2. Geospatial Analytics

Raw Satellite Imagery
        ↓
Band Extraction
        ↓
Cloud / Quality Masking
        ↓
Spatial Clipping
        ↓
NDVI + NDWI
        ↓
Field-Level Aggregation

3. Predictive Layer

Historical observations are transformed into temporal features for risk and trend estimation.

Satellite Time Series
        +
Weather Signals
        +
Crop Stage
        ↓
Predictive Model
        ↓
7–14 Day Risk / Trend Estimate

4. Optimization Layer

Risk Scores
    +
Water Availability
    +
Crop Vulnerability
    +
Solar Availability
    ↓
OR-Tools Constraint Solver
    ↓
Prioritized Irrigation Schedule

5. Delivery Layer

                    ┌───────────────┐
                    │ FastAPI       │
                    │ Backend       │
                    └───────┬───────┘
                            │
             ┌──────────────┴──────────────┐
             ▼                             ▼
      React Dashboard               Farmer Alerts
             │                             │
       Risk Maps                     WhatsApp/SMS
       Scenario UI
       Analytics

---

🛠️ Tech Stack

Layer| Technologies| Purpose
🛰️ Satellite Data| Sentinel-2, Landsat-9| Multispectral Earth observation
🌦️ Weather| Weather / IMD data sources| Forecast and environmental signals
🗺️ Geospatial| Rasterio, GeoPandas, GDAL, Shapely, PyProj| Raster processing and spatial analytics
🧮 Analytics| NumPy, Pandas, Scikit-learn| Feature engineering and statistical processing
🤖 ML| PyTorch| Predictive modelling and time-series experimentation
🔀 Optimization| Google OR-Tools, SciPy| Resource allocation and constraint solving
⚡ Backend| FastAPI, Uvicorn, Pydantic| REST API and application services
🗄️ Database| PostgreSQL + PostGIS| Spatial and application data
⚛️ Frontend| React.js| Interactive dashboard
🎨 UI| Tailwind CSS| Interface styling
🗺️ Maps| Mapbox GL JS / mapping layer| Spatial visualization
📊 Visualization| Recharts| Analytics and KPI visualization
📱 Alerts| Twilio / WhatsApp Business API| Farmer communication

---

🔄 End-to-End User Journey

“From Satellite Pass to Saved Harvest”

🛰️ OBSERVE
Satellite observation
       ↓
👁️ DETECT
Identify spatial risk
       ↓
🔮 PREDICT
Estimate near-term trend
       ↓
📊 SIMULATE
Test drought / water scenarios
       ↓
🔀 PRIORITIZE
Rank vulnerable fields
       ↓
☀️ OPTIMIZE
Align with available resources
       ↓
📱 ALERT
Send actionable information
       ↓
🌾 PROTECT
Reduce avoidable crop stress

Example workflow

1. Observe

A satellite observation covers a farming block.

2. Detect

HydroLens identifies a significant change in vegetation/water-related indicators for a field.

3. Predict

The temporal analytics layer estimates how the risk could evolve over the following days.

4. Simulate

The FPO manager enters a hypothetical dry spell and shared water constraint.

5. Prioritize

The optimization engine identifies fields requiring earlier intervention under the selected assumptions.

6. Schedule

Available solar pumping windows can be incorporated into the irrigation schedule.

7. Communicate

Farmers receive relevant irrigation or risk information through supported messaging channels.

---

📈 Proof of Value — Simulation Benchmark

Simulated 5-Day Heatwave Scenario

The following benchmark represents a controlled simulation, not a measured field trial.

100 farming plots
450 acres
100,000 L shared water reserve
5-day heatwave constraint

Scenario A — Equal Distribution

100,000 L / 100 plots
       ↓
1,000 L per plot
       ↓
Same allocation regardless of vulnerability

Scenario B — HydroLens Risk-Based Allocation

100,000 L reserve
       ↓
Risk + crop stage + vulnerability
       ↓
Priority-based allocation
       ↓
Solar-aware scheduling

Simulation Result

Metric| Equal Allocation| HydroLens Simulation
Severe-stress fields| 17| 6
Fields avoiding severe stress| —| 11
Simulated reduction in severe crop damage| —| ~65%

«⚠️ Benchmark note: These numbers are scenario-simulation outputs under the stated assumptions. They should not be interpreted as validated agricultural field results until calibrated and evaluated against ground-truth observations.»

---

🎯 Why HydroLens?

HydroLens focuses on the gap between “knowing there is a problem” and “deciding what to do with limited resources.”

Traditional workflow

Observe problem
      ↓
Manual assessment
      ↓
Delayed decision
      ↓
Resource allocation

HydroLens workflow

Satellite + Weather
        ↓
Continuous spatial signals
        ↓
Risk estimation
        ↓
Scenario simulation
        ↓
Optimization
        ↓
Actionable decision

The platform is designed around decision support, rather than simply displaying satellite imagery.

---

🧩 Key Differentiators

🛰️ Community-scale visibility

Instead of focusing only on individual sensor-equipped fields, HydroLens is designed to analyze contiguous agricultural blocks.

🔮 What-if simulation

FPOs can test resource constraints before implementing a response.

💧 Risk-based allocation

Water allocation can account for differences in vulnerability rather than treating every field identically.

☀️ Energy-aware planning

Irrigation scheduling can incorporate available solar pumping windows.

🌾 Beyond irrigation

The roadmap extends from water-risk intelligence into harvest, storage, transport and residue coordination.

---

📊 Dashboard Capabilities

The HydroLens dashboard is designed around the information an FPO decision-maker needs.

Overview

┌──────────────────────────────────────────────────────────┐
│                  HYDROLENS OVERVIEW                     │
├────────────┬────────────┬────────────┬──────────────────┤
│ Risk Score │ High Risk  │ Water Left │ Solar Capacity  │
├────────────┴────────────┴────────────┴──────────────────┤
│                                                        │
│                 COMMUNITY RISK MAP                    │
│                                                        │
│       🟢 Low     🟡 Moderate     🔴 Critical          │
│                                                        │
├────────────────────────────────────────────────────────┤
│              TOP PRIORITY FIELDS                       │
├────────────────────────────────────────────────────────┤
│ Field │ Crop │ Risk │ Stage │ Priority │ Action       │
└────────────────────────────────────────────────────────┘

Scenario Simulator

Users can modify:

- Dry-spell duration
- Available water
- Heatwave severity
- Solar availability
- Crop vulnerability assumptions

and inspect how the resulting allocation changes.

---

📱 Farmer Communication

HydroLens is designed to translate complex analytics into simple actions.

Example

🌾 HydroLens Alert

Your field is currently marked as
HIGH WATER-STRESS RISK.

Recommended irrigation window:
11:30 AM – 12:30 PM

Reason:
High vulnerability + available
solar pumping capacity.

Please follow your FPO's
local irrigation instructions.

The final messaging layer can be adapted for WhatsApp, SMS, or other low-bandwidth communication channels.

---

🗂️ Project Structure

HydroLens/
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   │   ├── risk/
│   │   │   ├── simulation/
│   │   │   └── alerts/
│   │   │
│   │   ├── core/
│   │   │   ├── config.py
│   │   │   └── environment.py
│   │   │
│   │   ├── services/
│   │   │   ├── satellite/
│   │   │   ├── geospatial/
│   │   │   ├── optimization/
│   │   │   └── alerts/
│   │   │
│   │   └── models/
│   │       └── predictive/
│   │
│   ├── requirements.txt
│   └── main.py
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Dashboard/
│   │   │   ├── RiskMap/
│   │   │   ├── ScenarioSimulator/
│   │   │   └── FarmerView/
│   │   │
│   │   ├── pages/
│   │   ├── services/
│   │   └── utils/
│   │
│   ├── package.json
│   └── tailwind.config.js
│
├── docs/
│   ├── architecture/
│   ├── research/
│   └── pitch/
│
├── README.md
└── LICENSE

---

⚡ Quick Start

Prerequisites

Make sure you have:

- Python 3.10+
- Node.js 18+
- npm
- PostgreSQL + PostGIS (optional for local prototype)
- Required API credentials configured in ".env"

---

1. Clone the repository

git clone https://github.com/your-username/HydroLens.git
cd HydroLens

---

2. Backend

cd backend

python -m venv venv

Windows

venv\Scripts\activate

macOS / Linux

source venv/bin/activate

Install dependencies:

pip install -r requirements.txt

Create your environment file:

cp .env.example .env

Configure the required variables.

Example:

SENTINEL_HUB_CLIENT_ID=
SENTINEL_HUB_CLIENT_SECRET=

MAPBOX_TOKEN=

DATABASE_URL=

TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_PHONE_NUMBER=

Start the API:

uvicorn main:app --reload --port 8000

Backend:

http://localhost:8000

API documentation:

http://localhost:8000/docs

---

3. Frontend

Open a new terminal:

cd frontend
npm install
npm start

Frontend:

http://localhost:3000

---

🔐 Environment Variables

Never commit API keys or credentials to GitHub.

Use:

.env

and keep it in ".gitignore".

Example:

.env
.env.local
venv/
__pycache__/
node_modules/
dist/
build/

---

🧪 Development & Validation

HydroLens can be evaluated at multiple levels:

Data Layer

- Satellite data availability
- Cloud / quality filtering
- Spatial alignment
- Temporal consistency

Analytics Layer

- NDVI / NDWI calculation
- Risk-score stability
- Time-series behaviour
- Crop-stage assumptions

Optimization Layer

- Constraint satisfaction
- Water-budget feasibility
- Allocation reproducibility
- Solar-window constraints

Product Layer

- Dashboard responsiveness
- Map interaction
- Scenario simulation
- Alert generation

---

🛣️ Roadmap

Phase 1 — MVP

🛰️ Satellite-based risk mapping
📊 HydroLens command dashboard
🗺️ Community risk visualization
👨‍🌾 Farmer-facing view

---

Phase 2 — Scenario & Optimization

🔮 Water-scarcity simulation
💧 Risk-based resource prioritization
☀️ Solar-aware irrigation scheduling
📈 Scenario comparison

---

Phase 3 — Harvest Intelligence

🌾 Harvest-window prediction
📦 Storage-demand forecasting
🚚 Transport coordination
♻️ Residue-demand forecasting

---

Phase 4 — Ground Validation & FPO Pilot

📍 Ground-truth collection
🌱 Field-level validation
🤝 FPO pilot deployment
📊 Model calibration
🔄 Feedback-driven model improvement

---

🔬 Research & Validation Direction

The next step beyond the MVP is ground validation.

HydroLens should be evaluated against:

- Ground soil-moisture measurements
- Crop-stage observations
- Irrigation records
- Weather observations
- Harvest outcomes
- Field-level yield data

This allows the satellite-derived indicators and predictive models to be calibrated for specific crops, regions and seasons.

---

👥 Team

Riya Arora

Full Stack Developer & AI Arc
