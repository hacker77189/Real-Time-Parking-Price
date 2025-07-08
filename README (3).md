# 🚗 Real-Time Dynamic Pricing for Urban Parking Lots

An end-to-end, real-time intelligent pricing system that dynamically updates parking rates for 14 urban lots based on real-time data streams. Built using Python, Pandas, NumPy, and **Pathway**, with real-time interactive visualizations in **Bokeh**.

> 📘 Capstone Project – **Summer Analytics 2025**  
> 🧠 Hosted by: *Consulting & Analytics Club × Pathway*

---

## 📌 Project Overview

Static parking rates lead to either overcrowding or underuse. This project simulates an intelligent pricing engine that adjusts parking fees in **real-time** based on:

- Occupancy trends  
- Queue length and congestion  
- Traffic flow and special events  
- Vehicle type and competitive pricing

---

## 🧠 Pricing Models

### ✅ Model 1: Baseline Linear Pricing

A simple, interpretable pricing logic based on current occupancy.

> **Formula:**
```python
price[i] = price[i - 1] + α × (occupancy[i] / capacity[i])
```

- Incremental price updates from previous value  
- Proportional to current occupancy ratio  
- No erratic jumps, ensures smooth pricing
- Used as a baseline reference

---

### ✅ Model 2: Demand-Based Pricing Model

Captures real-world demand signals to compute price dynamically.

> **Demand function:**
```python
demand = α × (occupancy / capacity) 
       + β × queue_length 
       − γ × traffic 
       + δ × is_special_day 
       + ε × vehicle_weight
```

> **Pricing function:**
```python
price = base_price × (1 + λ × normalized_demand)
```

- Demand is normalized to ensure **bounded and stable** pricing  
- All features are combined using interpretable weights  
- Final price is clipped between `0.5×` and `2×` base price (`$10`)  
- Enhances intelligence over baseline with multi-feature awareness

---

### 🔁 Coming Soon: Model 3 (Competitive Pricing)

> Uses geographic distance and pricing of nearby lots to adjust current price:
- Reroute users if nearby lots are cheaper and less crowded
- Exploit competitive advantage when nearby lots are more expensive

---

## 🔁 Real-Time Simulation using Pathway

Simulates a streaming environment for decision-making:

- **Ingests 18 data points per day** over 73 days
- Processes features **live**
- Outputs real-time prices for each parking space

---

## 📈 Visualizations

Implemented using **Bokeh** for interactive plots:
- Real-time pricing line plots for all 14 parking spaces
- Demand and occupancy overlays
- Animated visual for evolving trends

---

## 💾 Dataset Details

- **14 parking locations**
- Time span: **73 days × 18 time steps/day**
- Features:
  - `Occupancy`, `Capacity`, `QueueLength`
  - `Latitude`, `Longitude`
  - `Traffic`, `IsSpecialDay`, `VehicleType`

---

## 🚀 Run Instructions

1. **Clone the repo:**
   ```bash
   git clone https://github.com/hacker77189/Real-Time-Parking-Price.git
   cd Real-Time-Parking-Price
   ```

2. **Open `Real-Time-Parking.ipynb` on Google Colab**

3. **Install requirements in Colab:**
   ```python
   !pip install pathway pandas numpy bokeh
   ```

4. **Run each cell** to simulate, price, and plot.

---

## 📚 References

- 📖 [Pathway: From Jupyter to Deploy](https://pathway.com/developers/user-guide/deployment/from-jupyter-to-deploy/)
- 📘 [Pathway Real-Time App Guide](https://pathway.com/developers/user-guide/introduction/first_realtime_app_with_pathway/)
- 🌐 [Summer Analytics 2025](https://www.caciitg.com/sa/course25/)

---

## 👤 Author

**Minhaj Alam**  
GitHub: [@hacker77189](https://github.com/hacker77189)

---

## 📄 License

MIT License – feel free to fork, extend, and share with credit.

---