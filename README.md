# 🎰 Monte Carlo's Bayes Roulette

> **A Stochastic European Roulette Simulator, Table Heatmap & Non-Replacement Recency Engine**

![License: MIT](https://img.shields.io/badge/License-MIT-amber.svg)
![Type](https://img.shields.io/badge/Type-Vanilla%20JS%20%2F%20Single--File-emerald.svg)
![Localization](https://img.shields.io/badge/Languages-EN%20%7C%20ES%20%7C%20PT-blue.svg)

---

## 📌 Overview

**Monte Carlo's Bayes Roulette** is an interactive, browser-based probability engine that contrasts real-world independent events against a custom **subjective pseudo-sampling without replacement model**.

In an authentic casino roulette wheel, every spin is an independent event with replacement ($P(X_t = i) = \frac{1}{37} \approx 2.703\%$). Believing a number is "due" because it hasn't appeared recently is known as the **Gambler's Fallacy**. This software explicitly tests and models that psychological premise by dynamically lowering the weight of drawn pockets and gradually restoring them as subsequent spins pass.

The entire application runs from a **single, portable `index.html` file** with zero external dependencies, no server requirements, and no local installations needed.

---

## ✨ Features

* **🎡 Realistic Animated Wheel:** Full SVG wheel rotation and counter-rotating ball physics with cubic/quintic ease-out deceleration curves.
* **📐 Recency Weight Decay Engine:** Pockets decay in likelihood upon landing and exponentially recover over subsequent rounds.
* **🟢 Vertical European Table & Heatmap:** High-contrast betting felt with color-coded heatmap scales for:
  * Single Pockets (0–36)
  * Split Bets (2 numbers, horizontal & vertical borders)
  * Corner Bets (4-number intersections)
  * Outside Bets (Red/Black, Odd/Even, High/Low, Dozens, Columns)
* **📝 Practical Mode (Casino History Analyzer):** Input real past numbers drawn at a live table to immediately see the engine's "due" probability distribution.
* **🎛️ Live Parameter Tuning:** Real-time sliders to calibrate:
  * **Decay Penalty ($\alpha$):** Severity of weight drop upon hitting.
  * **Recovery Speed ($\lambda$):** Rate of exponential weight recovery.
* **🌐 Trilingual Localization:** Switch effortlessly between **English**, **Español**, and **Português**.
* **🌓 Light & Dark Luxury Themes:** Toggle between a deep emerald casino felt and an ivory parlor palette.

---

## 🔬 Mathematical Architecture

The core non-replacement pseudo-model calculates dynamic weights $W_i(t)$ for each pocket $i \in \{0, \dots, 36\}$:

$$W_i(t) = \max\left(1 - \alpha \cdot e^{-\lambda \cdot k_i},\; 0.05\right)$$

Where:
* $k_i$ is the number of spins elapsed since pocket $i$ last appeared ($k_i = \infty$ if never drawn).
* $\alpha \in [0, 1]$ represents the initial recency penalty.
* $\lambda > 0$ dictates the exponential recovery speed.

Normalized probability:

$$P(X_t = i) = \frac{W_i(t)}{\sum_{j=0}^{36} W_j(t)}$$

### Recency Proof Example:
If Number **3** was drawn 10 spins ago ($k_3 = 10$) and Number **8** was drawn 2 spins ago ($k_8 = 2$):

$$W_3 = 1 - 0.70 \cdot e^{-0.10 \cdot 10} \approx 0.742$$
$$W_8 = 1 - 0.70 \cdot e^{-0.10 \cdot 2} \approx 0.427$$

Because $W_3 > W_8$, Number **3 is mathematically modeled to have a higher probability of return** than Number 8.

---

## 🚀 Quick Start

### Running Locally
No installation required:
1. Clone this repository or download `index.html`.
2. Double-click `index.html` to open it in any web browser (Chrome, Safari, Firefox, Edge).

### Live Web Access (GitHub Pages)
This project is configured to work out-of-the-box with GitHub Pages:
1. Fork or push to your repository.
2. Go to **Settings** > **Pages**.
3. Select `Branch: main` and `/ (root)`.
4. Click **Save** to access the live public URL.

---

## ⚠️ Educational Disclaimer

This simulator is designed strictly for **mathematical education, stochastic modeling, and probability analysis**. In physical casino gaming, roulette spins are independent Bernoulli trials governed by a fixed house edge. Past numbers do not influence future outcomes on an unbiased wheel.

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.