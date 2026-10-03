```markdown
# 🌾 HydroLens — Satellite-Powered Agricultural Water & Climate Intelligence

<p align="center">
  <b><i>“See the Risk. Plan Before the Loss.”</i></b>
</p>

<p align="center">
  <a href="#-about-hydrolens"><img src="https://img.shields.io/badge/Hackathon-Schneider%20Electric%20Yuva%20Yodha-00D2FF?style=for-the-badge&logo=schneiderelectric" alt="Hackathon"></a>
  <a href="#-track-alignment"><img src="https://img.shields.io/badge/Challenge-1%3A%20Sustainable%20Agriculture-00E5C0?style=for-the-badge&logo=leaf" alt="Challenge 1"></a>
  <a href="#-tech-stack"><img src="https://img.shields.io/badge/Stack-Python%20%7C%20FastAPI%20%7C%20React%20%7C%20Mapbox-061D23?style=for-the-badge&logo=python" alt="Tech Stack"></a>
  <a href="#-license"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="License"></a>
</p>

---

## 📌 About HydroLens

**HydroLens** is an end-to-end climate resilience and agricultural intelligence platform built for **Farmer Producer Organizations (FPOs)**, water cooperatives, and regional agricultural officers. 

During dry spells and heatwaves, smallholder farmers understand their individual plots well, but regional decision-makers face a critical **community visibility gap**—they cannot easily observe how moisture stress develops across hundreds of neighboring fields or determine where limited irrigation resources should be prioritized before water stress becomes critical.

While traditional in-situ soil probes carry high deployment costs and maintenance hurdles across fragmented smallholder plots, **HydroLens reduces dependence on field-level hardware**. By synthesizing open multispectral satellite observations (Sentinel-2, Landsat-9), localized IMD weather forecasts, crop-stage growth models, and off-grid solar generation capacity, HydroLens delivers:

1. **Community-Scale Risk Mapping** across contiguous farming blocks.
2. **Predictive Scenario Simulations** under severe drought and heatwave constraints.
3. **Risk-Prioritized Resource Allocation** aligned with clean solar pumping shifts.
4. **Harvest & Post-Harvest Intelligence** to coordinate storage, transport, and residue management.

---

## 🎯 The 4 Solution Pillars

HydroLens operates across four interconnected functional modules:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                   HYDROLENS PLATFORM                                   │
├──────────────────────────┬──────────────────────────┬──────────────────────────────────┤
│ 01. COMMUNITY WATER RISK │ 02. SCENARIO ENGINE      │ 03. RESOURCE PRIORITIZATION      │
│ Satellite-based NDWI &   │ Simulates 5-14 day dry   │ Prioritizes critical fields &    │
│ NDVI canopy moisture     │ spells against shared    │ aligns shifts with peak solar    │
│ maps across 100+ fields. │ water tank reserves.     │ hours to reduce diesel reliance. │
├──────────────────────────┴──────────────────────────┴──────────────────────────────────┤
│ 04. HARVEST & RESIDUE INTELLIGENCE                                                     │
│ Predicts harvest timing & volume to flag storage, transport, & residue bottlenecks.   │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

1. **🌊 01 — Community Water Risk:** Processes 10m-resolution Sentinel-2 and Landsat multispectral imagery to calculate Normalized Difference Water Index (NDWI) and NDVI canopy vigor across contiguous farming blocks without requiring heavy ground hardware.
2. **🔮 02 — Scenario Engine:** Enables FPO managers to simulate drought and heatwave conditions, evaluating competing resource allocation strategies before water stress becomes critical.
3. **☀️ 03 — Resource Prioritization (Solar-Enabled):** Ranks vulnerable fields by crop stage and soil moisture deficit, scheduling irrigation queues to match peak off-grid solar pump generation hours to reduce diesel dependence.
4. **🌾 04 — Harvest & Residue Intelligence:** Predicts upcoming harvest windows and crop yields, helping communities coordinate storage, transport logistics, and residue-management resources before harvesting windows become critical.

---

## 🏗️ System Architecture

The HydroLens pipeline transforms raw orbital imagery and meteorological signals into actionable FPO dashboard insights and farmer WhatsApp/SMS alerts.

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│                            1. DATA INGESTION LAYER                               │
│                                                                                  │
│   ┌──────────────────┐   ┌──────────────────┐   ┌────────────────────────────┐   │
│   │ Sentinel-2 (10m) │   │  Landsat-9 (30m) │   │  IMD Weather Forecast APIs │   │
│   └────────┬─────────┘   └────────┬─────────┘   └─────────────┬──────────────┘   │
│            │                      │                           │                  │
│            └──────────────┬───────┴───────────────────────────┘                  │
│                           ▼                                                      │
│   ┌─────────────────────────────────────────┐   ┌────────────────────────────┐   │
│   │ OpenET Evapotranspiration / Soil Data   │   │ ISRO Bhuvan Spatial Layers │   │
│   └───────────────────────┬─────────────────┘   └─────────────┬──────────────┘   │
└───────────────────────────┼───────────────────────────────────┼──────────────────┘
                            ▼                                   ▼
┌──────────────────────────────────────────────────────────────────────────────────┐
│                          2. ANALYTICS & ML CORE ENGINE                           │
│                                                                                  │
│   ┌──────────────────────────────────────────────────────────────────────────┐   │
│   │ Python Geospatial Pipeline (Rasterio, GeoPandas, GDAL, Shapely)          │   │
│   │  • Multispectral Band Math: NDWI = (NIR - SWIR) / (NIR + SWIR)          │   │
│   │  • NDVI Canopy Vigor Index & Soil Moisture Depletion Calibration         │   │
│   └───────────────────────────────────┬──────────────────────────────────────┘   │
│                                       ▼                                          │
│   ┌──────────────────────────────────────────────────────────────────────────┐   │
│   │ PyTorch Predictive Time-Series Model                                     │   │
│   │  • 7–14 Day Soil Moisture Depletion & Harvest Window Prediction          │   │
│   └───────────────────────────────────┬──────────────────────────────────────┘   │
└───────────────────────────────────────┼──────────────────────────────────────────┘
                                        ▼
┌──────────────────────────────────────────────────────────────────────────────────┐
│                        3. OPTIMIZATION & SCENARIO ENGINE                         │
│                                                                                  │
│   ┌──────────────────────────────────────────────────────────────────────────┐   │
│   │ Google OR-Tools Constraint Solver                                        │   │
│   │  • Objective: Minimize Crop Stress Impact Across Block                   │   │
│   │  • Constraints: Shared Water Tank Volume (L) vs. Peak Solar kW Available  │   │
│   └───────────────────────────────────┬──────────────────────────────────────┘   │
└───────────────────────────────────────┼──────────────────────────────────────────┘
                                        ▼
┌──────────────────────────────────────────────────────────────────────────────────┐
│                            4. DELIVERY & USER LAYER                              │
│                                                                                  │
│      ┌──────────────────────────────────┐    ┌────────────────────────────┐      │
│      │  React.js + Mapbox GL Dashboard  │    │  Twilio / WhatsApp API     │      │
│      │  (For FPOs & Water Cooperatives) │    │  (Action Alerts for Farmers)│     │
│      └──────────────────────────────────┘    └────────────────────────────┘      │
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology / Library | Purpose |
| :--- | :--- | :--- |
| **Data Ingestion** | Sentinel Hub API, USGS EarthExplorer, IMD API | Ingests Sentinel-2 L2A, Landsat-9, and localized weather forecasts |
| **Geospatial Processing**| `rasterio`, `geopandas`, `gdal`, `shapely`, `pyproj` | Satellite band extraction, NDWI/NDVI masking, polygon clipping |
| **ML & Analytics** | `PyTorch`, `scikit-learn`, `numpy`, `pandas` | Predictive soil moisture depletion curves & harvest timing models |
| **Optimization** | `Google OR-Tools`, `scipy.optimize` | Constraint-satisfaction solver for water allocation vs. solar shifts |
| **Backend API** | `FastAPI`, `Uvicorn`, `Pydantic`, `PostgreSQL/PostGIS` | Asynchronous REST APIs and spatial geospatial data querying |
| **Frontend Web UI** | `React.js`, `Tailwind CSS`, `Mapbox GL JS`, `Recharts` | Interactive FPO command dashboard & scenario simulation UI |
| **Farmer Messaging** | `Twilio API`, `WhatsApp Business API` | Low-bandwidth SMS/WhatsApp alert dispatch to smallholder farmers |

---

## 🔄 User Journey: "From Satellite Pass to Saved Harvest"

```
 🛰️ Satellite Pass ────► 👁️ Detect Risk ────► 🔮 Predict Trend ────► 📊 Simulate Scenario
                                                                             │
 🛡️ Protect & Save ◄──── ☀️ Plan Solar Shift ◄──── 🔀 Prioritize Fields ◄────┘
```

1. **Observe (Satellite Pass):** Sentinel-2 captures multispectral bands over a 450-acre farming block.
2. **Detect (Moisture Drop):** Automated pipeline computes NDWI and flags Plot A-12 (Groundnut) as entering critical canopy water stress.
3. **Predict (Risk Forecasting):** Time-series ML model projects soil moisture depletion over the next 7 days.
4. **Simulate (Drought Scenario):** FPO manager inputs a 5-day forecasted dry spell into the Scenario Simulator with a 100,000L shared water reserve.
5. **Prioritize (Resource Allocation):** Constraint solver ranks 15 high-vulnerability fields and assigns water priority over non-stressed plots.
6. **Plan (Solar Shift Sync):** Irrigation queues are scheduled during peak off-grid solar generation (11:30 AM – 02:30 PM), reducing diesel reliance.
7. **Protect (Farmer Action):** Smallholders receive WhatsApp alerts with designated solar pumping time slots, protecting crop yields and post-harvest resources.

---

## 📈 Proof of Value: Scenario Simulation Benchmark

Under a simulated **5-day heatwave constraint** across 100 farming plots (450 acres) with a **100,000L shared water reserve**:

* **Uncoordinated Equal Distribution (Approach A):** Distributing 1,000L equally to all plots leaves every field under-hydrated, resulting in **17 fields suffering severe, unrecoverable crop failure** (~38% block yield loss).
* **HydroLens Risk-Based AI Allocation (Approach B):** Directing water to highest-vulnerability plots during peak solar hours restricts severe stress to **only 6 fields**—saving **11 farms from critical crop loss** (a **65% reduction in crop damage**).

---

## 🚀 Quickstart & Installation

### Prerequisites
* Python 3.10+
* Node.js 18+
* PostgreSQL with PostGIS extension (or SQLite for local testing)

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/HydroLens.git
cd HydroLens
```

### 2. Backend Setup
```bash
# Navigate to backend folder
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure Environment Variables
cp .env.example .env
# Add your Sentinel Hub, Mapbox, and Twilio API keys to .env

# Run FastAPI Server
uvicorn main:app --reload --port 8000
```

### 3. Frontend Setup
```bash
# Navigate to frontend folder (in a new terminal)
cd frontend

# Install dependencies
npm install

# Start development server
npm start
```
*Open `http://localhost:3000` in your browser to view the FPO Command Dashboard and Scenario Simulator UI.*

---

## 🗺️ Project Directory Structure

```
HydroLens/
├── backend/
│   ├── app/
│   │   ├── api/             # FastAPI routes (satellites, simulation, alerts)
│   │   ├── core/            # Config & environment settings
│   │   ├── services/        # Satellite ingestion, NDWI calculation, OR-Tools solver
│   │   └── models/          # PyTorch soil moisture depletion models
│   ├── requirements.txt
│   └── main.py              # Application entry point
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/      # FPO Dashboard, Satellite Map, Simulator UI, Mobile Alert
│   │   ├── pages/           # Main route views
│   │   └── utils/           # Mapbox layers & API fetchers
│   ├── package.json
│   └── tailwind.config.js
├── docs/                    # Architecture diagrams, pitch deck PDFs
├── README.md
└── LICENSE
```

---

## 👥 Team & Acknowledgments

* **Riya Arora** — *Full Stack Developer & AI Architect*
* **Manasvi Chugh** — *Full Stack Developer & Geospatial Systems Lead*

Developed for the **Schneider Electric Yuva Yodha Energy Tech Hackathon** under **Challenge 1: Sustainable Agriculture — Energy, Water & Productivity**. Special thanks to Schneider Electric India for inspiring digital, clean energy solutions for smallholder resilience.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
```
