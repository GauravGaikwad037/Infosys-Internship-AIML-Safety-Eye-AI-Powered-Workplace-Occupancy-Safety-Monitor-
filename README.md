
# SafetyEye – AI-Powered Workplace Occupancy & Safety Monitor

Milestone 1 (Week 1–2): **Data Preparation & Environment Setup**

This VS Code–ready repo scaffolds your project and includes runnable scripts to:
- Define safety rules and project architecture
- Download the **Construction Site Safety Image Dataset (Roboflow) from Kaggle**
- Prepare/verify YOLOv8-compatible data layout
- Split into train/val/test
- Validate environment & GPU
- (Optional) Kick off a YOLOv8 training sanity check

> Dataset link: Kaggle – Construction Site Safety Image Dataset (Roboflow)

## Quick Start

### 1) Clone/Download
Unzip this folder and open it in **VS Code**.

### 2) Create Environment
You can use **conda** or **venv**.

**Conda (recommended):**
```bash
conda env create -f environment.yml
conda activate safetyeye
```

**venv:**
```bash
python -m venv .venv
# Activate:
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

### 3) Kaggle API setup (to auto-download the dataset)
- Create a Kaggle account → Account → *Create New API Token* to download `kaggle.json`.
- Place `kaggle.json` in one of:
  - Windows: `%USERPROFILE%\.kaggle\kaggle.json`
  - macOS/Linux: `~/.kaggle/kaggle.json`
  - Or this project root (script will copy it to the right place).
- Alternatively, set env vars in a `.env` file (see `.env.example`).

### 4) Prepare data
```bash
# 1) Download from Kaggle (automated). If you already downloaded manually, skip this.
python scripts/prepare_data.py --step download

# 2) Verify & arrange YOLOv8 structure
python scripts/prepare_data.py --step verify

# 3) Split into train/val/test (default 70/20/10)
python scripts/prepare_data.py --step split --train 0.7 --val 0.2 --test 0.1

# 4) Generate Ultralytics data.yaml pointing to splits
python scripts/prepare_data.py --step make-yaml
```

### 5) Check environment
```bash
python -m src.training.setup_env_check
```

### 6) (Optional) Run a tiny training sanity check
```bash
# Update configs/data.yaml paths if needed, then:
python -m src.training.train_yolov8 --model yolov8n.pt --epochs 5
```

## Repo Layout

```
SafetyEye/
├─ configs/
│  ├─ safety_rules.yaml        # Violation definitions
│  ├─ project.json             # Paths & project metadata
│  └─ data.yaml                # Ultralytics YOLOv8 dataset config (generated)
├─ data/
│  ├─ raw/                     # Raw Kaggle download
│  ├─ interim/                 # Any intermediate conversions
│  └─ yolov8/                  # Final YOLOv8 structure: images/ & labels/ with train/val/test
├─ notebooks/
│  └─ 01_explore_dataset.ipynb # (placeholder) Use to visually inspect samples
├─ scripts/
│  └─ prepare_data.py          # Orchestrates download→verify→split→yaml
├─ src/
│  ├─ data/
│  │  ├─ download_kaggle.py
│  │  ├─ verify_and_prepare.py
│  │  └─ split_dataset.py
│  ├─ training/
│  │  ├─ setup_env_check.py
│  │  └─ train_yolov8.py
│  └─ utils/
│     └─ logger.py
├─ .env.example
├─ .gitignore
├─ environment.yml
└─ requirements.txt
```


In later milestones, use these rules to generate alerts & dashboard stats.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stylish Image Gallery</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Load Inter font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Apply Inter font */
        body { 
            font-family: 'Inter', sans-serif; 
        }
    </style>
</head>
<body class="bg-gray-100 min-h-screen p-8 md:p-12">

    <div class="max-w-7xl mx-auto">
        
        <!-- Section Title -->
        <h1 class="text-3xl md:text-4xl font-bold text-gray-800 text-center mb-10">
            Project Showcase
        </h1>
        
        <!-- 
          Responsive Grid Gallery
          - 1 column on small screens (default)
          - 2 columns on medium screens (md:)
          - 3 columns on large screens (lg:)
          - gap-8 adds space between cards
        -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            
            <!-- Card 1 -->
            <div class="bg-white rounded-xl shadow-lg overflow-hidden transition-all duration-300 hover:shadow-2xl hover:-translate-y-1 transform">
                <!-- 
                  Image: I've replaced your local images with placeholders.
                  Just swap 'https://placehold.co/...' with your image paths 
                  (e.g., 'violation_2025-10-07_19-59-40.jpg')
                  when you add this to your GitHub project.
                -->
                <img src="violation_2025-10-07_19-59-40.jpg" alt="Violation Report" class="w-full h-48 object-cover">
                
                <!-- Card Content -->
                <div class="p-5">
                    <h3 class="text-lg font-semibold text-gray-900 mb-2">Violation Report</h3>
                    <p class="text-gray-600 text-sm">
                        Dashboard showing security and compliance violations detected on 2025-10-07.
                    </p>
                </div>
            </div>

            <!-- Card 2 -->
            <div class="bg-white rounded-xl shadow-lg overflow-hidden transition-all duration-300 hover:shadow-2xl hover:-translate-y-1 transform">
                <img src="daily_chart_2025-10-06.pngt" alt="Daily Chart" class="w-full h-48 object-cover">
                
                <!-- Card Content -->
                <div class="p-5">
                    <h3 class="text-lg font-semibold text-gray-900 mb-2">Daily Chart</h3>
                    <p class="text-gray-600 text-sm">
                        Daily user engagement and activity metrics for the period ending 2025-10-06.
                    </p>
                </div>
            </div>

            <!-- Card 3 -->
            <div class="bg-white rounded-xl shadow-lg overflow-hidden transition-all duration-300 hover:shadow-2xl hover:-translate-y-1 transform">
                <img src="metrics.jpg" alt="Key Metrics" class="w-full h-48 object-cover">
                
                <!-- Card Content -->
                <div class="p-5">
                    <h3 class="text-lg font-semibold text-gray-900 mb-2">Key Metrics</h3>
                    <p class="text-gray-600 text-sm">
                        An overview of the project's key performance indicators (KPIs) and growth metrics.
                    </p>
                </div>
            </div>
            
        </div>
        
    </div>
</body>
</html>



---

**Authoring tip:** Start with `yolov8n.pt` (smallest) to iterate quickly.
