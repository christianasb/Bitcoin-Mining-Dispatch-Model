# Bitcoin-Mining-Dispatch-Model

This repo contains a Colab-ready notebook that builds and evaluates a Bitcoin mining dispatch model for ERCOT.  
It uses ERCOT 15-minute prices and Hashrate Index hashprice to decide when to mine and to backtest profitability.

---

## 📂 Files
- **bitcoin_mining_dispatch.ipynb** — main notebook with steps, code, prints, and charts.  
- **README.md** — this guide.  

---

## ⚙️ How to Run (Google Colab)
1. Open the notebook in **Google Colab**.  
2. In **Section 1: User Inputs**, set:
   - `facility_size` (MW)  
   - `machine_efficiency` (W/TH)  
   - `date_start`, `date_end`  
   - `LZ_selection` (e.g., `"ALL"`, `"LZ_HOUSTON"`)  
   - `ercot_price` (e.g., `"lmp_with_adders"`)  
   - `use_fixed_PPA` and `PPA_price_MWh` if using a PPA  
   - `API_KEY` for Hashrate Index  
3. Upload your ERCOT CSVs to `/content/ercot_csv` in Colab.  
4. Go to **Runtime > Run all** to execute the full workflow.  

---

## 📊 What It Prints
- **Profitability assessment**  
  Average revenue, cost, and margin per MWh (from miner efficiency + hashprice).  
- **Dispatch logic**  
  Sample rows showing when the mine is ON or OFF.  
- **Backtest results**  
  Totals for revenue, cost, profit, uptime, and energy consumed.  
- **Summaries by zone**  
  Zone-by-zone comparison of profitability.  
- **High-level insights**  
  Hour-of-day run rates, top and bottom profit days, and contiguous ON/OFF blocks.  
- **Visualizations**  
  - Cumulative profit over time  
  - Average run rate by hour of day  
  - Distribution of gross margin per MWh  

---

## 📝 Notes
- **Hashprice** is network-wide and identical across all zones at a given time.  
- **Electricity price** (spot or PPA) drives the cost per MWh and determines dispatch.  
- If your ERCOT column names differ, the notebook automatically tries to resolve them.  
- Adding a small buffer (e.g., margin > $1/MWh) can make dispatch more conservative.  
