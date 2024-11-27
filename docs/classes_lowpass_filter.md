This class is designed to **smooth out accelerometer data** by removing high-frequency noise (quick and insignificant changes in movement). It uses a mathematical technique called a **low-pass filter** to focus on slower, meaningful movement patterns. This is useful when analyzing movement data because it makes trends and significant motions clearer.

---

### Step-by-Step Explanation:

1. **Input Data:**
    - The input is a table (DataFrame) with three columns: **x, y, z**. These represent movement measurements along three axes.
2. **Low-Pass Filter:**
    - The filter removes fast, noisy signals from the data. For example:
        - If you’re walking, the filter keeps the steady up-and-down motion of your steps but removes tiny vibrations caused by your device or environment.
3. **How It Works:**
    - A mathematical function (called a **Butterworth filter**) is applied to the data.
    - It keeps movement data below a certain speed (frequency), determined by the **cutoff frequency**. Movements faster than this speed are considered noise and are removed.
4. **Filter Settings:**
    - **Cutoff Frequency:** The speed at which the filter decides whether to keep or remove a signal (e.g., 5 Hz means it keeps motions slower than 5 cycles per second).
    - **Sampling Rate:** The rate at which the device records movement data (e.g., 25 Hz means 25 data points per second).
    - **Filter Order:** Determines the sharpness of the filtering. A higher order makes the cutoff more precise.
5. **Smoothing the Data:**
    - The class applies the low-pass filter to the **x, y, and z** columns of the data, smoothing them to remove noise.
6. **Output:**
    - The filtered data is returned as a table (DataFrame) with the same structure as the input.
    - The smoothed columns (**x, y, z**) are ready for further analysis.
7. **Error Handling:**
    - If the input data doesn’t include the required columns (**x, y, z**), the class raises an error to ensure proper usage.
8. **Friendly Messages:**
    - After the filter is applied, the class prints a message: “Low-pass filter applied successfully,” so the user knows the process is complete.
