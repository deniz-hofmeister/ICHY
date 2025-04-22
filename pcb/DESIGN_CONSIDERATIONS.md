# What acoustic frequencies should i be targeting to have the best possible chance at detecting drones at long range?

For long-range acoustic detection of drones, it’s best to focus on frequency ranges that balance two factors:

1. **Propagation Efficiency:**  
   Lower-frequency sounds tend to propagate further because they experience less atmospheric attenuation compared to higher frequencies. This makes them more suitable for long-range detection.

2. **Signal Strength and Signature:**  
   Small drones typically produce most of their acoustic energy in the lower to mid-frequency range, especially due to the rotor blade passage frequency and motor noise. At the same time, higher harmonics (above 1 kHz) can be useful for identification but tend to attenuate faster over distance.

Below is a more detailed breakdown:

### Primary Frequency Range

- **50 Hz to 300 Hz:**  
  Many studies and measurements have shown that the fundamental noise produced by rotor blades, as well as the motor vibrations of small to medium drones, often fall in this range. These lower frequencies tend to be less absorbed by the atmosphere, making them ideal for long-range detection.

### Supporting Frequency Range

- **300 Hz to 500 Hz:**  
  While still in a relatively low-frequency domain, this range can capture secondary or harmonic components of the mechanical noise. These signals can sometimes enhance detection when the drone’s primary signature overlaps with environmental noise.

### Higher Frequencies (Above 1 kHz)

- **Higher Harmonics:**  
  While you might observe strong signals around 1 kHz or above in some close-range spectral analyses, these frequencies are more susceptible to atmospheric attenuation and scattering at long range. They may be more useful for close-range classification or identification rather than initial detection over a long distance.

### Practical Considerations

- **Ambient Noise:**  
  When targeting the 50–300 Hz range, be aware that urban and rural environments can have their own low-frequency noise (e.g., traffic rumble, HVAC systems, wind), which might interfere with drone detection. Signal processing techniques like filtering and beamforming may be necessary.

- **Sensor Sensitivity:**  
  Ensure that your acoustic sensors/microphones are sensitive enough in the low-frequency range. Some microphones are optimized for voice frequencies (roughly 300 Hz–3 kHz) and may need adjustments or selection changes to capture low-frequency drone noise effectively.

- **Detection Algorithms:**  
  Use algorithms that can pick out the signature patterns (e.g., periodic pulses from rotor blades) around these frequencies to distinguish drone noise from background noise.

### Summary

For long-range detection of drones, the **best chance is typically in the low-to-mid frequency range (about 50–300 Hz)** due to lower atmospheric attenuation and the inherent acoustic signature of the drones’ motors and rotors. While you may also analyze higher frequencies (>1 kHz) for additional classification details, focusing primarily on the 50–300 Hz range provides a robust starting point for detection over longer distances.

# How can 50 Hz to 300 Hz be the target frequency if the drones spin their propellers as 1000s of RPM?

When we say that the optimal frequency range for long-range detection is 50–300 Hz, it doesn't mean the drone propellers aren't spinning at thousands of RPM. Here’s why:

### Converting RPM to Hertz

- **RPM and Revolutions per Second:**  
  RPM (Revolutions Per Minute) can be converted to Hertz (cycles per second) by dividing by 60. For example, if a propeller spins at 6000 RPM:
  
  \[
  \text{Frequency (Hz)} = \frac{6000\ \text{RPM}}{60} = 100\ \text{Hz}
  \]
  
- **Blade Passage Frequency:**  
  Many drone propellers are multi-bladed. The blade passage frequency, which is often more prominent in the acoustic spectrum, is the product of the rotational frequency and the number of blades. For a two-blade propeller at 6000 RPM:
  
  \[
  \text{Blade Passage Frequency} = 100\ \text{Hz} \times 2 = 200\ \text{Hz}
  \]
  
  This calculation places the sound squarely in the 50–300 Hz range.

### Why the Target Range Works for Drone Detection

- **Fundamental Frequency Matches:**  
  Even though the motor itself can reach thousands of RPM, the acoustic signatures that propagate well over long distances are typically linked to the overall mechanical and aerodynamic interactions, such as the fundamental rotation or the blade passage frequency.
  
- **Lower Frequency Propagation:**  
  Low-frequency sounds (like those in the 50–300 Hz range) are less affected by atmospheric attenuation. This makes them more effective for long-range detection compared to higher frequencies, which tend to dissipate faster.

- **Noise and Harmonics:**  
  While drones do produce higher-frequency noise components (due to motor whine or high-frequency turbulence), these are secondary, and the lower-frequency components (resulting from the fundamental operation as described above) are more robust for detection.

### Summary

Even though a drone's propeller might spin at thousands of RPM, the conversion of those speeds into Hertz (cycles per second) and the multiplication due to the number of blades means that many of the dominant acoustic signals fall into the 50–300 Hz range. This frequency band is effective for long-range detection because it benefits from lower atmospheric attenuation and captures the primary mechanical signatures of the drone.

# What should be the inter microphone distance if it will be designed with 500 Hz as the core design frequency?

When designing a microphone array for spatial detection using a specific design frequency, one key guideline is to space the microphones so that you avoid spatial aliasing and are sensitive to the desired frequency content. A common rule-of-thumb is to keep the inter-microphone distance less than or equal to half the wavelength of the core frequency.

### Step-by-Step Calculation

1. **Determine the Wavelength (λ):**  
   The wavelength is given by the formula:  

   \[
   \lambda = \frac{c}{f}
   \]

   where:  
   - \( c \) is the speed of sound (approximately 343 m/s in air at room temperature), and  
   - \( f \) is the frequency.

   For a target frequency of 500 Hz:

   \[
   \lambda = \frac{343\, \text{m/s}}{500\, \text{Hz}} \approx 0.686\, \text{m}
   \]

2. **Determine the Maximum Inter-Microphone Distance:**  
   To avoid aliasing, the inter-microphone distance should be no more than half the wavelength:

   \[
   \text{Maximum distance} = \frac{\lambda}{2} \approx \frac{0.686\, \text{m}}{2} \approx 0.343\, \text{m}
   \]

### Recommended Design

For a design frequency of 500 Hz, you should aim for an inter-microphone distance of approximately **0.34 meters (34 centimeters)** or less. This spacing ensures that your array can accurately capture the phase differences of acoustic waves at 500 Hz and minimizes the risk of spatial aliasing.

### Additional Considerations

- **Array Geometry:**  
  The above calculation applies to linear spacing. For circular or planar arrays, the geometry might introduce additional factors, but the half-wavelength rule remains a good starting point.

- **Environmental Conditions:**  
  The speed of sound can vary slightly with temperature and humidity, so consider these factors if your application operates in varying environments.

- **Wideband Applications:**  
  If your array is intended for a wide range of frequencies, you may need to optimize the spacing for the lowest frequency of interest (since lower frequencies have longer wavelengths) while noting that the design frequency here is 500 Hz.

By following the half-wavelength guideline at your target frequency, your microphone array should be well-tuned for optimal detection performance at 500 Hz.
