# Reflective Intelligence System

 Overview

This project builds an intelligent system that understands user emotional states from noisy reflections and contextual signals, and converts them into meaningful actions.

The system is designed not just for prediction, but for **decision-making under uncertainty**.

---
 Problem Nature

This is not a standard classification problem. The system must handle:

* Noisy and short text inputs
* Missing and inconsistent metadata
* Contradictory signals
* Imperfect labels

---

 Approach

\1. Preprocessing

* Missing values filled using median (numeric) and "unknown" (categorical)
* Text cleaned and standardized

---

### 2. Feature Engineering

#### Text Features

* TF-IDF (1–2 grams, 3000 features)

#### Metadata Features

* sleep_hours
* energy_level
* stress_level

Metadata features are scaled and weighted to balance their importance relative to text.

---

 3. Model Design

 Emotional State Model

* XGBoost Classifier
* Multi-class classification

 Intensity Model

* XGBoost Classifier (ordinal treated as classification)
* Labels converted from (1–5) → (0–4)

---

 4. Pipeline Design

A shared feature pipeline is used for both models to ensure:

* Consistency
* No feature mismatch
* Reusability

---

 5. Decision Engine (Core)

A multi-layer rule-based system using:

* emotional state
* intensity
* stress
* energy
* time of day
* uncertainty

It outputs:

* what_to_do
* when_to_do

---

 6. Uncertainty Modeling

Uncertainty is computed using:

* prediction confidence
* entropy of probabilities
* reflection quality

This allows the system to:

* avoid risky recommendations
* fallback to safe actions

---

 7. Output

Final predictions include:

* predicted_state
* predicted_intensity
* confidence
* uncertain_flag
* what_to_do
* when_to_do

---

## Ablation Study

| Model         | Performance            |
| ------------- | ---------------------- |
| Text only     | Lower (misses context) |
| Metadata only | Weak (no semantics)    |
| Combined      | Best performance       |

**Conclusion:** Combining text and metadata significantly improves robustness.

---

 Key Insights

* Text provides emotional meaning
* Metadata stabilizes predictions
* Uncertainty is critical in real-world systems
* Decision layer is more important than raw accuracy

---

How to Run

1. Upload dataset in Colab
2. Run pipeline cells sequentially
3. Generate `predictions.csv`

---

 Tech Stack

* Python
* Scikit-learn
* XGBoost
* Pandas
* NumPy

---

 Final Note

This system is designed as a **decision-making system under uncertainty**, not just a classifier.
