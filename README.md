# JEE-kcet-comdk-rank-predictor
 🚀 AI-Powered College Predictor (2025 Production Edition)

![Python](https://img.shields.io/badge/Python-3.12-blue?style=for-the-badge&logo=python&logoColor=white)
![Data Source](https://img.shields.io/badge/Data-Official_2025_Round_3-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production_Ready-success?style=for-the-badge)
![Exam Support](https://img.shields.io/badge/Supports-KCET_%7C_COMEDK_%7C_JEE-orange?style=for-the-badge)

📖 Executive Summary
The AI College Predictor is a sophisticated Machine Learning tool engineered to guide engineering aspirants in Karnataka through the complex admission landscape.

Unlike generic predictors that rely on static lookup tables, this system utilizes Polynomial Regression to model the non-linear relationship between raw marks and rank. It then cross-references this predicted rank against a high-precision database constructed from the Official COMEDK 2025 Round 3 Allotment List (Notified Aug 22, 2025).

The tool addresses the "Mark-to-Rank" ambiguity by training on difficulty-calibrated trend lines for KCET, COMEDK, and JEE Main, offering students a realistic probability assessment of securing seats in top-tier institutions like **RVCE, BMSCE, and MSRIT.

---

🛠️ Technical Architecture

1. The Prediction Engine (Machine Learning)
The core of the system is a `sklearn` pipeline that transforms raw marks into a predicted rank.
* **Algorithm:** Polynomial Regression (Degree 3).
* **Why Degree 3?** Rank distribution is not linear. A difference of 5 marks at the top (e.g., 175 vs 180) impacts rank far less than 5 marks in the middle (e.g., 90 vs 95). A 3rd-degree polynomial captures this "bell curve" density perfectly.
* **Training Data:** Calibrated using 2024-2025 paper difficulty statistics.

2. The Database (Official 2025 Cutoffs)
The backend database is a curated subset of the **2025 Round 3 Engineering Cutoff Ranks**.
* Source: Official Allotment PDF (22.08.2025).
* Scope: Covers Tier-1 (Global Placements), Tier-2 (High Value), and Tier-3 (Regional Leaders).
* Granularity: Includes specific branch cutoffs for CSE, ISE, ECE, AI & ML, and Data Science.

3. The Recommendation Logic
The system applies a "Safety Margin Classification" to every prediction:
* 🟢 SAFE: Your rank is < 80% of the cutoff (High Probability).
* 🟡 LIKELY: Your rank is < 100% of the cutoff (Moderate Probability).
* 🔴 BORDERLINE: Your rank is slightly above the cutoff (Requires Spot Round/Luck).

---

📊 Deep-Dive: 2025 Data Analysis
The project includes hard-coded intelligence derived from the 2025 admission cycle. Below are key insights integrated into the tool:

| Tier | Institution | Branch (CSE) Cutoff (Round 3) | Analysis |
| :--- | :--- | :--- | :--- |
| Tier 1 | RV College of Engineering (RVCE) | 542    | Extremely competitive. Closed under Rank 600. |
| Tier 1 | MS Ramaiah (MSRIT)               | 1,341  | Remains the top choice after RVCE. |
| Tier 1 | BMS College of Engineering       | 3,689  | Slightly higher cutoff, offering a wider window. |
| Tier 2 | Dayananda Sagar (DSCE)           | 5,479  | The "Golden Gate" for sub-5k rankers. |
| Tier 2 | Bangalore Inst. of Tech (BIT)    | 9,177  | Excellent value for ranks near 10k. |
| Tier 2 | CMR Institute of Tech (CMRIT)    | 18,084 | Major jump in cutoff, showing high demand. |
| Tier 2 | Sir M Visvesvaraya (Sir MVIT)    | 22,026 | A "Safe Harbor" for ranks between 20k-25k. |

> Note: All ranks listed are COMEDK GM (General Merit) Cutoffs.

---

💻 Installation & Usage

To run this analytics tool on your local machine:

Prerequisites
* Python 3.10+
* Pip (Python Package Manager)

Step 1: Clone the Repository
```bash
git clone [https://github.com/YOUR_USERNAME/AI-College-Predictor.git](https://github.com/YOUR_USERNAME/AI-College-Predictor.git)
cd AI-College-Predictor

**Step 2: Install Dependencies
We use scikit-learn for the ML model and pandas for data handling.

Bash
pip install pandas numpy scikit-learn

Step 3: Configure & Run
Open the app.py file (or whatever you named the script) and modify the User Inputs section at the top:

Python
# --- USER INPUTS ---
MY_EXAM = 'COMEDK'   # Options: 'KCET', 'COMEDK', 'JEE'
MY_MARKS = 115       # Enter your marks here
Then execute the script:

Bash
python app.py
🚀 Future Roadmap
Seat Matrix Integration: Dynamic adjustment of probabilities based on total available seats.
Category Support: Adding cutoffs for SC/ST/OBC and Hyderabad-Karnataka (371J) quotas.
Web Interface: Porting the logic to a Streamlit or Flask web app for public access.

⚠️ Disclaimer
Predictive Nature: This tool uses statistical modeling. Actual ranks depend on the number of test-takers and the specific difficulty distribution of the 2026 paper.
Data Validity: Cutoff data is strictly from the 2025 cycle. Admission trends may shift in 2026 due to new policy changes or seat additions.
Advisory: Use this tool for strategic planning, but always rely on official counseling brochures for final decision-making.
