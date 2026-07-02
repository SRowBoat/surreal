## Surreal Number Learning Tool

# Code Architecture & Project Licensing

This document provides a technical breakdown of the interactive single-page application engine and outlines its open-source licensing terms.

---

## 🛠️ Code Architecture Overview

The application is built entirely as a single-page, dependency-free interactive system. Below is a breakdown of how the background engine processes John Horton Conway's mathematical logic in real-time:

* **State Machine Navigation:** View routing is completely controlled by a global state index (`currentStep`). Clicking **Next** or **Back** fires a transition function that selectively modifies the DOM by adding or removing Tailwind's structural hiding elements (`.hidden`), eliminating the need for page refreshes.
* **The Binary Decelerator Engine (Step 4):** When you interact with the "Tug of War" console, the JavaScript engine simulates an iterative binary search across bounds to translate user path signals directly into rational decimal values:
    * Clicking **L (Left)** updates the lower boundary limit:  
      `currentRangeMin = currentFractionValue;`
    * Clicking **R (Right)** updates the upper boundary limit:  
      `currentRangeMax = currentFractionValue;`
    * The system recalculates the precise midpoint configuration:  
      `(currentRangeMin + currentRangeMax) / 2`  
      and dynamically updates the user-facing translation matrix.
* **Front-End Layer:** Styles are compiled on the fly using a Tailwind CSS CDN injection layer. It uses isolated slate color blocks (`bg-slate-950`, `text-slate-100`) to create a readable, modern, dark-mode terminal vibe suited for long-form reading.

---

## 📄 Open Source License (MIT)

This project is released under the standard, permissive MIT License model. It is completely free of restrictive upstream constraints and is fully safe for redistribution, modification, or personal forks.

---

### 🗺️ The "Morse Code" Cheat Sheet

Remember the rule:
* **$L$ (Left)** pushes the value **higher**.
* **$R$ (Right)** pulls the value **lower**.

Here is how you spell out different numbers starting from the middle ($0.5$ or $1/2$):

#### 1. How to reach exactly $0.25$ (which is $1/4$)
To get smaller fractions, you have to pull the ceiling down to shrink the number.
* **Start at:** $0.5$ 
* **Click $R$:** This pulls the ceiling down. The midpoint drops strictly between $0$ and $0.5$.
* **Result:** **$0.25$** ($1/4$).
* **Code:** `R`

#### 2. How to reach exactly $0.200$ (which is $1/5$)
Because $1/5$ doesn't divide cleanly by $2$, your boundaries will bounce back and forth, narrowing down on the target like a heat-seeking missile.
* **Start at:** $0.5$
* **Click $R$:** Value drops to $0.25$ *(Too high! Need to push up).*
* **Click $R$:** Value drops to $0.125$ *(Too low! Need to push up).*
* **Click $L$:** Value jumps to $0.188$ *(Still a bit too low).*
* **Click $L$:** Value jumps to $0.219$ *(Slightly too high).*
* **Click $R$:** Value drops to $0.203$...
* **Code:** `R` $\rightarrow$ `R` $\rightarrow$ `L` $\rightarrow$ `L` $\rightarrow$ `R` *(Keep alternating, and you will get infinitely closer to exactly $0.2$).*

---

### 🚀 How to Reach Infinity ($\omega$)

To get to infinity, you can't just click $L$ and $R$ back and forth. You have to break the machine. 

Imagine a path where you **only click $L$ forever and ever**, and never click $R$ a single time. 

* **Click $L$:** You get $1$
* **Click $L$ again:** You get $2$
* **Click $L$ again:** You get $3$
* **Keep clicking $L$ infinitely:** You outrun every normal counting number. Because you never clicked $R$, there is no ceiling holding you down. The universe looks at this endless trail of Left clicks and creates **$\omega$ (Omega)**—the first surreal infinity.

### How to use this in the App:
Go back to **Step 4** in your browser, look at the two buttons, and try typing the code `R R L L` consciously. Watch the digital scale shift and bend to hit those exact decimal points!
