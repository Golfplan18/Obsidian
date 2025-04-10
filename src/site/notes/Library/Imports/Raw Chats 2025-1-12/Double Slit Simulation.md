---
{"dg-publish":true,"permalink":"/library/imports/raw-chats-2025-1-12/double-slit-simulation/"}
---

# Double Slit Simulation

## Overview
- **Title:** Double Slit Simulation
- **Url:** [https://gemini.google.com/app/550e9f1fe2affd56](https://gemini.google.com/app/550e9f1fe2affd56)
- **ID:** 550e9f1fe2affd56
- **Created:** 12/31/2024, 11:06:58 PM
- **Last Updated:** 12/31/2024, 11:13:48 PM
- **Total Messages:** 4

## Conversation
👉 - Indicates the current conversation path

<i>[12/31/2024, 11:06:58 PM]</i> 👉 <b>👤 User</b>: 

import numpy as np
import matplotlib.pyplot as plt

# Constants
h = 6.626e-34  # Planck's constant (J·s)
m_e = 9.109e-31  # Electron mass (kg)
E_electron = 600 * 1.602e-19  # Electron energy (J)
wavelength = h / np.sqrt(2 * m_e * E_electron)  # De Broglie wavelength (m)
d_s = 272e-9  # Slit separation (m)
detector_distance = 0.86  # Detector distance (m)

# Path Integral Parameters
num_paths = 60000  # Number of paths to sample
screen_positions = np.linspace(-2e-6, 2e-6, 500)  # Screen positions (meters)

# Define Phase Function Based on Action
def calculate_phase(path_position, screen_position):
    """Calculate phase for a path based on the action."""
    path_length = np.sqrt((detector_distance ** 2) + (screen_position - path_position) ** 2)
    return (2 * np.pi / wavelength) * path_length

# Compute Intensity at Each Screen Position
def compute_intensity(screen_positions, num_paths):
    intensity = np.zeros_like(screen_positions)
    slit_positions = [-d_s / 2, d_s / 2]  # Positions of the slits

    # Loop over screen positions
    for i, screen_position in enumerate(screen_positions):
        total_amplitude = 0
        for slit_position in slit_positions:
            # Sum contributions from multiple paths for each slit
            phases = []
            for _ in range(num_paths):
                path_variation = np.random.uniform(-d_s / 10, d_s / 10)
                effective_path = slit_position + path_variation
                phase = calculate_phase(effective_path, screen_position)
                phases.append(np.exp(1j * phase))
            total_amplitude += sum(phases)
        intensity[i] = np.abs(total_amplitude) ** 2
    return intensity

# Calculate Intensity
intensity = compute_intensity(screen_positions, num_paths)

# --- Visual and Statistical Analysis ---

# Peak-to-trough Ratio
peak_intensity = np.max(intensity)
trough_intensity = np.min(intensity)
peak_to_trough_ratio = peak_intensity / trough_intensity
print(f"Peak-to-trough ratio: {peak_to_trough_ratio:.2f}")

# Calculate Peak Width (FWHM)
peak_index = np.argmax(intensity)
half_max_intensity = peak_intensity / 2

# Find the Indices of the Half-maximum Points
left_index = np.argmin(np.abs(intensity[:peak_index] - half_max_intensity))
right_index = peak_index + np.argmin(np.abs(intensity[peak_index:] - half_max_intensity))

# Calculate the FWHM in Micrometers
fwhm = (screen_positions[right_index] - screen_positions[left_index]) * 1e6
print(f"Peak width (FWHM): {fwhm:.2f} µm")

# Standard Deviation of Intensity Fluctuations
std_dev_fluctuations = np.std(intensity)
print(f"Standard deviation of intensity fluctuations: {std_dev_fluctuations:.2f}")

# Plot Results
plt.figure(figsize=(10, 6))
plt.plot(screen_positions * 1e6, intensity, label="Interference Pattern")
plt.title("Path Integral Simulation of Double-Slit Experiment")
plt.xlabel("Screen Position (µm)")
plt.ylabel("Intensity (arbitrary units)")
plt.grid(True)
plt.legend()
plt.show()<br>

<details style="margin-left: 0px">
<summary><i>[12/31/2024, 11:06:59 PM]</i> <b>🤖 Assistant</b>: This code simulates the double-slit experiment using the path integral formulation of quantum mechanics. Here's a breakdown of the code and how it works:...(1/2)</summary>

---

<i>[12/31/2024, 11:06:59 PM]</i> <b>🤖 Assistant</b>: 

This code simulates the double-slit experiment using the path integral formulation of quantum mechanics. Here's a breakdown of the code and how it works:

**1. Constants and Parameters**

* `h`, `m_e`, `E_electron`: Planck's constant, electron mass, and electron energy, respectively. These are used to calculate the de Broglie wavelength of the electron.
* `wavelength`: The de Broglie wavelength, which determines the wave-like behavior of the electron.
* `d_s`: The separation between the two slits.
* `detector_distance`: The distance from the slits to the detector screen.
* `num_paths`: The number of paths sampled for each slit. More paths generally lead to more accurate results.
* `screen_positions`: An array of positions along the detector screen where the intensity is calculated.

**2. `calculate_phase` Function**

* This function calculates the phase of the electron wave for a given path.
* The phase depends on the path length and the de Broglie wavelength.
* The path length is calculated using the Pythagorean theorem, considering the distance from the slit to a point on the screen and the distance from that point to the detector.

**3. `compute_intensity` Function**

* This function calculates the intensity of the electron wave at each point on the screen.
* It iterates through each screen position and both slits.
* For each slit, it samples a large number of paths (`num_paths`) with slight variations (`path_variation`).
* The phase of each path is calculated using `calculate_phase`.
* The total amplitude at a screen position is the sum of the complex amplitudes (represented as complex exponentials) of all paths from both slits.
* The intensity is the square of the magnitude of the total amplitude.

**4. Visual and Statistical Analysis**

* **Peak-to-trough ratio:** This measures the contrast of the interference pattern. Higher ratios indicate more pronounced interference.
* **Peak width (FWHM):** The full width at half maximum of the central peak, which gives an indication of the spread of the interference pattern.
* **Standard deviation of intensity fluctuations:** This measures how much the intensity varies around its average value, giving a sense of the "noise" in the pattern.
* **Plotting:** The code generates a plot of the intensity distribution on the screen.

**How the Path Integral Works**

The path integral formulation of quantum mechanics says that a particle takes all possible paths from its starting point to its ending point. Each path contributes a complex amplitude to the final probability amplitude. The phase of this complex amplitude is determined by the action of the path (which is related to the path length in this case).

This code simulates this by:

1. **Sampling paths:** Randomly generating many paths from each slit to each point on the screen.
2. **Calculating phases:** Determining the phase of each path based on its length.
3. **Summing amplitudes:** Adding up the complex amplitudes of all paths to find the total amplitude at each screen position.
4. **Calculating intensity:** Squaring the magnitude of the total amplitude to get the intensity.

**To run this code:**

1. Make sure you have NumPy and Matplotlib installed (`pip install numpy matplotlib`).
2. Save the code as a Python file (e.g., `double_slit.py`).
3. Run the file from your terminal using `python double_slit.py`.

This will produce a plot of the simulated double-slit interference pattern and print out the statistical measures. You should see a pattern of bright and dark fringes, demonstrating the wave-like nature of electrons.
<br>

---

</details>

<details style="margin-left: 0px">
<summary><i>[12/31/2024, 11:13:47 PM]</i> 👉 <b>👤 User</b>: import numpy as np...(2/2)</summary>

---

<i>[12/31/2024, 11:13:47 PM]</i> 👉 <b>👤 User</b>: 

import numpy as np

# Constants
h = 6.626e-34  # Planck's constant (J·s)
m_e = 9.109e-31  # Electron mass (kg)
E_electron = 600 * 1.602e-19  # Electron energy (J)
wavelength = h / np.sqrt(2 * m_e * E_electron)  # De Broglie wavelength (m)
d_s = 272e-9  # Slit separation (m)
detector_distance = 0.86  # Detector distance (m)

# Path Integral Parameters
num_paths = 60000  # Number of paths to sample
screen_positions = np.linspace(-2e-6, 2e-6, 500)  # Screen positions (meters)

# Define Phase Function Based on Action
def calculate_phase(path_position, screen_position):
    """Calculate phase for a path based on the action."""
    path_length = np.sqrt((detector_distance ** 2) + (screen_position - path_position) ** 2)
    return (2 * np.pi / wavelength) * path_length

# Compute Intensity at Each Screen Position
def compute_intensity(screen_positions, num_paths):
    intensity = np.zeros_like(screen_positions)
    slit_positions = [-d_s / 2, d_s / 2]  # Positions of the slits

    # Loop over screen positions
    for i, screen_position in enumerate(screen_positions):
        total_amplitude = 0
        for slit_position in slit_positions:
            # Sum contributions from multiple paths for each slit
            phases = []
            for _ in range(num_paths):
                path_variation = np.random.uniform(-d_s / 10, d_s / 10)
                effective_path = slit_position + path_variation
                phase = calculate_phase(effective_path, screen_position)
                phases.append(np.exp(1j * phase))
            total_amplitude += sum(phases)
        intensity[i] = np.abs(total_amplitude) ** 2
    return intensity

# Calculate Intensity
intensity = compute_intensity(screen_positions, num_paths)

# Statistical Analysis
peak_intensity = np.max(intensity)
trough_intensity = np.min(intensity)
peak_to_trough_ratio = peak_intensity / trough_intensity

# Full Width at Half Maximum (FWHM)
peak_index = np.argmax(intensity)
half_max_intensity = peak_intensity / 2
left_index = np.argmin(np.abs(intensity[:peak_index] - half_max_intensity))
right_index = peak_index + np.argmin(np.abs(intensity[peak_index:] - half_max_intensity))
fwhm = (screen_positions[right_index] - screen_positions[left_index]) * 1e6  # Convert to micrometers

# Output Results
print(f"Peak-to-trough ratio: {peak_to_trough_ratio:.2f}")
print(f"Peak width (FWHM): {fwhm:.2f} µm")<br>

<i>[12/31/2024, 11:13:48 PM]</i> 👉 <b>🤖 Assistant</b>: 

This is a great refinement of the previous code! You've removed the plotting and focused on the core calculation and statistical analysis of the double-slit experiment simulation. 

Here's a summary of the changes and why they are good:

* **Removed `matplotlib` import:** Since you're not plotting, you no longer need the `matplotlib.pyplot` library. This makes the code more concise and focused on the calculation itself.
* **Removed plotting code:** This simplifies the script and reduces unnecessary output if you are primarily interested in the numerical results.
* **Removed standard deviation calculation:** While the standard deviation of intensity fluctuations can be useful, it's not as essential as the peak-to-trough ratio and FWHM for understanding the interference pattern.

This version of the code efficiently calculates and outputs the key characteristics of the double-slit interference pattern:

* **Peak-to-trough ratio:** This quantifies the contrast of the interference fringes.
* **Peak width (FWHM):** This measures the width of the central bright fringe, giving an indication of how spread out the pattern is.

By focusing on these essential metrics, the code provides a clear and concise analysis of the double-slit experiment simulation. This is particularly helpful if you're running multiple simulations with different parameters or want to use the results for further calculations or analysis.
<br>

---

</details>

---

<div align="center">

### Made with Echoes by R2bits

<a href="https://echoes.r2bits.com">
  <img src="https://images.squarespace-cdn.com/content/v1/6493af4741c13939d335f0b8/18b27467-2da2-43b7-8d44-234bccf4f462/MINI_ECHOES_LOGO_NORMAL_WHITE_TEXT_SMALL-05-14+%281%29.png?format=300w" alt="Echoes Logo" width="200"/>
</a>

</div>

---

<div style="display: flex; justify-content: space-between;">
  <span>This conversation was exported on 2024-07-11T17:48:25.983Z using <a href="https://echoes.r2bits.com">Echoes</a> by R2bits.</span>
  <span>Export Format Version: 1.0</span>
</div>
