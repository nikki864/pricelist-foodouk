[README.md](https://github.com/user-attachments/files/28543174/README.md)
# 🤖 Foodomarket AI Price List Builder

Upload **any** Excel supplier catalog — AI figures out which columns are product names, 
conditioning/units, and prices. Then choose a cuisine and it automatically curates a 
list of the best 10 products (or any number you choose).

---

## 📁 Structure

```
foodomarket_ai/
├── app.py              ← Main Streamlit app (AI-powered)
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Set your Anthropic API key

```bash
# macOS / Linux
export ANTHROPIC_API_KEY="sk-ant-..."

# Windows (PowerShell)
$env:ANTHROPIC_API_KEY = "sk-ant-..."
```

You can get an API key at https://console.anthropic.com

### 3. Run the app

```bash
streamlit run app.py
```

Opens at **http://localhost:8501**

---

## 🚀 How to Use

### Step 1 — Upload
- Upload **1 or 2** Excel files (any format, any column names)
- Click **"🔍 Analyse Files with AI"**

### Step 2 — AI Analysis
- AI reads your columns and identifies:
  - Product name column
  - Conditioning / unit / packaging column
  - Price column
  - Category, Supplier, Cuisine (if present)
- AI also infers which **cuisine types** are represented in the catalog
- All products are merged into a unified database

### Step 3 — Build Your List
- Choose your **Target Cuisine** (e.g. Tunisian, Italian, Lebanese…)
- Optionally filter by **Categories**
- Set the **number of products** (default: 10)
- Add any **extra instruction** for the AI (e.g. "include at least 2 seafood items")
- Click **"🚀 Build AI List"**

### Step 4 — Export
- Download as **Excel** (.xlsx) — formatted with brand colors
- Download as **PDF** (.pdf) — professional branded document

---

## 💡 What Excel Formats Are Supported?

The app can handle virtually any structure:
- Headers on row 1, 2, or 3
- Columns in any order
- French, Arabic, or English column names
- Multiple sheets (picks the largest)
- Files with extra blank rows/columns
- Merged header cells (best effort)

The AI column detection works by reading a sample of your data and reasoning about which column is most likely the product name, price, and conditioning — even if columns are named in other languages.

---

## 🔑 API Usage

This app calls the Claude API (claude-sonnet-4-20250514) 2–3 times per session:
1. Column detection (once per file)
2. Cuisine/category inference (once)
3. Product list generation (each time you click Build)

Each call uses approximately 500–1000 tokens. Costs are minimal (fractions of a cent per run).
