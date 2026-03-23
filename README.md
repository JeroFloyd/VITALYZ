# 🧠 VITALYZ – Smart Health Monitoring & Predictive Risk System

I built this app during my internship at Qatar University where I worked under Dr. Kishor Kumar Sadasivuni. VITALYZ is an intelligent health monitoring system that combines wearable sensor data, real-time analytics, and machine learning to predict potential health risks such as heatstroke, organ stress, and dehydration. The system is designed to enable **preventive healthcare** by continuously analyzing physiological signals and providing actionable insights.

---

## 🚀 Overview

VITALYZ integrates a custom wristband device that streams real-time physiological data to the mobile application. This data is processed using a combination of rule-based logic and machine learning models to detect anomalies and predict risks before they become critical.

---

## 📊 Data Acquisition

The system collects the following real-time vitals:

* ❤️ Heart Rate (BPM)
* 🌡️ Body Temperature (°C)
* 💧 Skin Conductivity (Electrodermal Activity)
* 🏃 Activity Level (motion/acceleration)
* ⏱️ Time-based trends (continuous monitoring)

These inputs are transmitted to Firebase and processed locally/on-device using TensorFlow.

---

## 🔥 Heatstroke Prediction Model

Heatstroke risk is calculated using a **composite risk score** derived from multiple physiological parameters.

### Key Factors:

* Elevated body temperature
* Increased heart rate
* High skin conductivity (sweating response)
* Sustained exposure over time

### Risk Score Formula:

```
Heatstroke Risk Score (HRS) = 
w1 * normalized(Body Temperature) +
w2 * normalized(Heart Rate) +
w3 * normalized(Skin Conductivity) +
w4 * exposure_time_factor
```

Where:

* `w1, w2, w3, w4` are weighted coefficients
* Values are normalized between 0 and 1

### Interpretation:

* **0.0 – 0.4** → Low Risk
* **0.4 – 0.7** → Moderate Risk
* **0.7 – 1.0** → High Risk (Alert Triggered)

The model also considers **rate of change** (sudden spikes) to detect rapid onset conditions.

---

## 💧 Hydration Monitoring System

Hydration levels are inferred indirectly using:

* Skin conductivity trends
* Heart rate variability
* Activity intensity

### Logic:

* Increasing heart rate + decreasing skin conductivity → possible dehydration
* High activity + low recovery rate → hydration deficit

### Hydration Score:

```
Hydration Score = 
1 - (HR_deviation + EDA_drop + activity_stress) / 3
```

Lower scores indicate higher dehydration risk.

---

## 🫀 Organ Stress Detection

Organ stress is predicted using **combined cardiovascular strain indicators**.

### Inputs:

* Resting vs active heart rate difference
* Recovery time after activity
* Temperature deviation from baseline

### Stress Index:

```
Stress Index = 
(HR_current - HR_rest) / HR_rest + 
recovery_delay_factor + 
temperature_variation
```

Higher values indicate increased physiological strain.

---

## 💊 Medication Effectiveness Tracking

The system evaluates how the body responds after medication intake.

### Method:

* Compare pre-medication vs post-medication vitals
* Analyze trend improvements over time

### Effectiveness Metric:

```
Effectiveness = 
(vital_improvement_score over time) / baseline_deviation
```

Used to determine whether a medication is having a positive physiological impact.

---

## 🤖 Machine Learning Integration

* TensorFlow Lite models are used for:

  * Pattern recognition in vital trends
  * Risk classification (Low / Medium / High)
  * Personalized predictions

* Models are trained on:

  * Simulated physiological datasets
  * Time-series health data patterns

---

## ⚙️ System Architecture

* **Frontend:** Flutter (Dart)
* **Backend:** Firebase (Realtime Database / Firestore)
* **ML Engine:** TensorFlow Lite (on-device inference)
* **Hardware Integration:** Custom wearable wristband

---

## 🔔 Alert System

The app triggers alerts when:

* Heatstroke risk exceeds threshold
* Abnormal heart rate patterns detected
* Hydration drops below safe levels

Alerts include **preventive suggestions**, such as:

* Hydrate immediately
* Reduce physical activity
* Move to a cooler environment

---

## 📱 Deployment

* Platform: Android
* Designed for real-time, low-latency processing
* Optimized for mobile performance

---

## ⚠️ Disclaimer

VITALYZ is a preventive health and wellness tool and is **not a substitute for professional medical advice, diagnosis, or treatment**.

---

## 🔒 License

This project is proprietary and protected under an "All Rights Reserved" license.

Unauthorized copying, modification, or distribution is strictly prohibited.
