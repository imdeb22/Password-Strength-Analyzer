# Password-Strength-Analyzer

A sleek, lightweight, terminal-inspired password security evaluation tool. It analyzes string strength in real-time using **Shannon Information Entropy**, checks inputs against common/historical credentials, and provides secure alternative suggestion engines.

---

## Features

* **Real-Time Entropy Calculation:** Computes the password's information entropy in bits dynamically as you type.
* **Cyberpunk / Monospace Aesthetic:** Designed with a clean, dark-mode terminal UI built for developers and security enthusiasts.
* **Criteria Checklist:** Tracks standard security metrics visually:
  * Length $\ge$ 12 characters
  * Uppercase letters (`A-Z`)
  * Lowercase letters (`a-z`)
  * Numbers (`0-9`)
  * Symbols / Special characters (`!@#`)
* **Local Reuse Database:** Cross-references entries instantly against known common passwords (e.g., `admin123`, `password123`) to explicitly flag compromised inputs.
* **Integrated Generators:** * **Passphrase Generator:** Creates multi-word memorable combinations (Xkcd-style).
  * **Random Generator:** Spits out highly complex 16-character alphanumeric/symbolic strings.

---

## How the Entropy Algorithm Works

The application calculates strength using information theory. The bit-entropy value is evaluated via:

$$E = L \times \log_2(R)$$

Where:
* $E$ = Shannon Entropy in bits
* $L$ = Length of the user password string
* $R$ = Dynamic pool size based on character variety:
  * Lowercase present: $+26$
  * Uppercase present: $+26$
  * Numbers present: $+10$
  * Symbols present: $+32$

### Security Tiers

| Entropy Value (Bits) | Security Rating | UI Indicator |
| :--- | :--- | :--- |
| **Matches Database** | `REUSED` | Muted Gray |
| **< 40** | `CRITICAL` | Bright Red |
| **40 - 59** | `WEAK` | Orange |
| **60 - 79** | `STRONG` | Yellow |
| **80+** | `SECURE` | Bright Green |

---

## Project Structure & Setup

This tool is entirely self-contained within a single vanilla HTML file, making it extraordinarily fast and completely dependency-free.

### Run LocalCode Architecture Overview

* **UI Layer:** Native responsive CSS with a strict monospace font stack (`Consolas`, `Andale Mono`, etc.) utilizing media queries for fluid scaling down to mobile viewports.
* **Logic Layer:** Pure native JavaScript (`ES6`) listening to input field state mutations.
* **State Reset Handling:** Includes a comprehensive `resetUI()` listener to clear states, colors, and string memories immediately if the form is cleared.

---

## License

This utility is open-source and free to use for personal or professional compliance profiling. Feel free to tweak the `historyDatabase` or `wordList` arrays in the script block to broaden its analysis scope!
