# ROI Calculator Instructions
*How to build this in Google Sheets or Excel.*

**Sheet Structure:**

## Column A: Labels | Column B: Input (Yellow) | Column C: Calculation (Green)

### Section 1: The Inputs
*   **Role Name:** [Text Input] (e.g., Senior PM)
*   **Hourly Billable Rate:** $[Input] (e.g., $200)
*   **Number of Employees:** [Input] (e.g., 10)
*   **Hours Spent on Admin/Week:** [Input] (e.g., 4)

### Section 2: The "Cost of Inaction" (Formulas)
*   **Weekly Cost:** `=(Rate * Employees * Hours)`
    *   *Example Display:* $8,000 / week
*   **Monthly Cost:** `=(Weekly Cost * 4.3)`
    *   *Example Display:* $34,400 / month
*   **Annual Cost:** `=(Weekly Cost * 50)` (Assume 2 weeks vacation)
    *   *Example Display:* $400,000 / year

### Section 3: The Solution (Pilot)
*   **Target Reduction:** [Input]% (Default to 50%)
*   **Value Recovered:** `=(Annual Cost * Target Reduction)`
    *   *Example Display:* $200,000
*   **Pilot Investment:** $15,000 (Static)

### Section 4: The ROI (Big Green Numbers)
*   **Net Year 1 Gain:** `=(Value Recovered - Pilot Investment)`
    *   *Example Display:* **$185,000**
*   **Payback Period:** `=(Pilot Investment / (Value Recovered / 12))`
    *   *Example Display:* **0.9 Months**
*   **ROI %:** `=(Net Gain / Pilot Investment) * 100`
    *   *Example Display:* **1,233%**

---

**Visual Tip:**
Keep it clean. High contrast.
When presenting on Zoom, zoom in to 150% so they can see the numbers clearly.
Only let *them* give you the numbers for Section 1. Do not guess.
