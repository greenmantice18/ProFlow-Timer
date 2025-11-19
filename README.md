# 🍅 ProFlow: Advanced Pomodoro Productivity Hub

> **A precision-focused productivity timer that solves the JavaScript "Event Loop" drift issue.**

🔗 **[Live Demo](https://greenmantice18.github.io/ProFlow-Timer/)

## 💡 Project Overview
ProFlow is an advanced implementation of the Pomodoro technique. Unlike basic timers that rely on `setInterval` (which drifts when the browser is inactive), this application uses **Delta-Time Calculation** to maintain atomic accuracy.

It demonstrates the shift from simple DOM manipulation to **complex internal state management**, handling "Focus" and "Break" cycles, audio feedback, and persistent data logging.

## ⚙️ Technical Implementation
This project focuses on three core engineering challenges:

### 1. The Drift-Correction Algorithm
Standard `setInterval` is inaccurate for time-critical apps because the JavaScript Event Loop can be blocked by other tasks.
* **Naive approach:** `interval starts -> wait 1000ms -> decrement -> repeat`. (Drifts over time).
* **My Approach:** `Start Timestamp` is captured. On every tick, the code calculates `(Date.now() - StartTime)` to determine the exact elapsed time, ensuring the timer never lags, even if the tab sleeps.

### 2. State Machine Architecture
The app does not rely on the DOM for data. It uses a centralized State Object (`state.mode`, `state.timeLeft`, `state.isRunning`) to manage transitions between **Focus Mode** (Red) and **Break Mode** (Green).

### 3. Browser API Integration
* **Notification API:** Requests permission to send system-level alerts when the timer ends, allowing users to work in other tabs.
* **Audio API:** Uses the `Audio()` constructor for auditory feedback without blocking the main thread.
* **LocalStorage:** Serializes completed session objects to JSON to persist productivity history across browser refreshes.

## ✨ Key Features
- **Accurate Timing:** Self-correcting timer logic.
- **Auto-State Transition:** Automatically switches themes and durations between Focus (25m) and Break (5m).
- **Session Logging:** Tracks completed tasks with timestamps in a history log.
- **Smart Titles:** Updates `document.title` dynamically (e.g., `(14:59) Focus`) so the timer is visible in the browser tab.
- **Responsive UI:** Built with Bootstrap 5 for mobile and desktop compatibility.

## 🛠️ Tech Stack
* **Core:** HTML5, CSS3, Vanilla JavaScript (ES6+)
* **Styling:** Bootstrap 5, FontAwesome
* **APIs:** Notification API, Audio API, LocalStorage, Date API

