# ICHY - Component Selection

## Microphone Selection

### Selected Model: Infineon IM73D122
- **Interface**: PDM (Pulse Density Modulation)
- **Package Size**: 4.00 x 3.00 x 1.20 mm
- **SNR**: 73 dB(A) - Ultra-high SNR
- **AOP (Acoustic Overload Point)**: 120/122 dBSPL (1%/10% THD)
- **Current Consumption**: 980 μA @ 3.072 MHz
- **Sensitivity**: -26 dBFS
- **LFRO (Low Frequency Roll-Off)**: 20 Hz
- **Key Features**: Ultra-high SNR & sensitivity

### Selection Rationale
The IM73D122 was selected for the 16-element microphone array due to:
- **Ultra-high SNR**: Provides cleanest signal for precise beamforming and direction finding
- **High Sensitivity**: Optimal for capturing distant sound sources
- **PDM Interface**: Compatible with Jetson platform's digital interfaces
- **Low Frequency Response**: 20Hz roll-off extends well below our 1kHz-8kHz target range
- **Uniform Characteristics**: Infineon MEMS microphones offer matched frequency response required for phased array applications

### Alternative Models Considered

| Model | Main Features | Interface | Package Size [mm] | SNR | AOP (1/10%THD) | Current | Sensitivity | LFRO [Hz] |
|-------|--------------|-----------|------------------|-----|----------------|---------|-------------|-----------|
| IM69D130 | High SNR and high AOP | PDM | 4.00 x 3.00 x 1.20 | 69 dB(A) | 128/130 dBSPL | 980 μA @ 3.072 MHz | -36 dBFS | 28 |
| IM69D120 | High SNR and sensitivity | PDM | 4.00 x 3.00 x 1.20 | 69 dB(A) | 118/120 dBSPL | 980 μA @ 3.072 MHz | -26 dBFS | 28 |
| IM69D127 | High performance in small size | PDM | 3.60 x 2.50 x 1.00 | 69 dB(A) | 123/127 dBSPL | 980 μA @ 3.072 MHz | -34 dBFS | 40 |
| IM69D128S | Ultra-low current consumption | PDM | 3.50 x 2.65 x 1.00 | 69 dB(A) | 125/128 dBSPL | 520 μA @ 3.072 MHz | -37 dBFS | 30 |
| IM70D122 | High SNR and sensitivity | PDM | 3.50 x 2.65 x 1.00 | 70 dB(A) | 120/122 dBSPL | 980 μA @ 3.072 MHz | -26 dBFS | 30 |
| IM72D128 | Ultra-high SNR | PDM | 4.00 x 3.00 x 1.20 | 72 dB(A) | 126/128 dBSPL | 980 μA @ 3.072 MHz | -36 dBFS | 20 |
| IM73D122 | Ultra-high SNR & sensitivity | PDM | 4.00 x 3.00 x 1.20 | 73 dB(A) | 120/122 dBSPL | 980 μA @ 3.072 MHz | -26 dBFS | 20 |

## Data Acquisition & Processing Components

### PDM to TDM Conversion Options

#### Option 1: Texas Instruments PCMD3180/PCMD3180-Q1
- **Description**: 8-Channel Audio Analog-to-Digital Converter (PDM to TDM/I2S)
- **Channels**: 8 PDM microphones simultaneous conversion
- **Output Format**: TDM, I2S, or left-justified (LJ) formats (compatible with Jetson platform)
- **Sampling Rate**: 8kHz to 768kHz programmable output sample rate
- **Package Size**: 24-pin WQFN package
- **Power Consumption**: 2.5mW/channel at 48kHz sample rate (1.8V supply)
- **Special Features**: 127dB dynamic range, programmable digital volume control, microphone bias voltage, phase-locked loop (PLL), programmable high-pass filter, bi-quad filters, low-latency filter modes
- **Temperature Range**: –40°C to +125°C
- **Supplier Link**: https://www.mouser.co.uk/new/texas-instruments/ti-pcmd3180-audio-adc/

#### Option 2: Analog Devices ADAU7118
- **Description**: 8-Channel PDM to TDM/I2S audio converter
- **Channels**: 8 PDM microphones (4 stereo pairs)
- **Output Format**: I2S or TDM (up to TDM-16) compatible with Jetson platform
- **Sampling Rate**: 4kHz to 192kHz output sampling rate
- **Package Size**: 16-lead, 3mm × 3mm, 0.50mm pitch LFCSP
- **Power Consumption**: 1.2mA operating current for 8 channels at 48kHz (1.8V supply)
- **Special Features**: 126dB A-weighted SNR, 24-bit resolution, selectable I2C control, configurable TDM slot routing, dual PDM clock outputs, automatic PDM clock generation
- **Temperature Range**: -40°C to +85°C
- **Supply Voltage**: I/O (1.70V to 3.63V), DVDD (1.10V to 1.98V)
- **Supplier Link**: https://www.mouser.co.uk/new/analog-devices/adi-adau7118-converter/

#### Option 3: Tempo Semiconductor TSDP18xx
- **Description**: Octal PDM to TDM/I2S converter (8-Channel DMIC Aggregator)
- **Channels**: 8 PDM microphones
- **Output Format**: I2S (1 or 2 channels), Left-Justified (1 or 2 channels), or TDM (1-8 channels)
- **Sampling Rate**: 8kHz to 384kHz output sampling rate
- **Resolution**: 16-bit or 24-bit Linear PCM
- **Power Consumption**: Ultra-low power (<1μA in standby)
- **Special Features**: >142dB SNR, 6th order 24-bit filtering, flexible oversampling options (32x to 512x), supports SCLK polarity inversion, configurable FRMCLK widths
- **Supply Voltage**: IOVDD (1.8V or 3.3V), DVDD (1.8V)
- **Supplier Link**: https://temposemi.com/wp-content/uploads/2019/09/TSDP18xx_DS.pdf

#### Comparison Table

| Feature | TI PCMD3180 | ADI ADAU7118 | Tempo TSDP18xx |
|---------|------------|-------------|---------------|
| Channels | 8 PDM microphones | 8 PDM microphones (4 stereo pairs) | 8 PDM microphones |
| Sampling Rates | 8kHz to 768kHz | 4kHz to 192kHz | 8kHz to 384kHz |
| Resolution | N/A | 24-bit | 16-bit or 24-bit |
| Package Size | 24-pin WQFN | 16-lead, 3mm × 3mm LFCSP | N/A |
| Power | 2.5mW/channel @ 48kHz | 1.2mA total @ 48kHz (1.8V) | <1μA standby |
| SNR | 127dB dynamic range | 126dB A-weighted SNR | >142dB |
| Temperature Range | -40°C to +125°C | -40°C to +85°C | N/A |
| Output Formats | TDM, I2S, LJ | I2S or TDM (up to TDM-16) | I2S, LJ, TDM (1-8 channels) |
| Key Advantage | Highest sampling rate, wider temp range | Lower power, smaller package | Highest SNR, ultra-low power |
| Special Features | HPF, bi-quad filters | Dual PDM clocks | 6th order filtering, flexible oversampling |

### PDM to TDM Converter Selection Analysis

After evaluating all three options, we've carefully considered the requirements for connecting 16 Infineon IM73D122 PDM microphones to an NVIDIA Jetson platform. Since each converter chip can handle 8 PDM inputs, two chips will be required regardless of which solution is chosen.

#### TI PCMD3180 Analysis
**Pros:**
- Highest maximum sampling rate (768kHz) providing significant headroom
- Wide temperature range (-40°C to +125°C) for operation in varied environments
- 127dB dynamic range, well above the microphones' 73dB SNR
- Comprehensive filtering options (HPF, bi-quad filters)

**Cons:**
- Higher power consumption (2.5mW/channel)
- Larger package size (24-pin WQFN)
- More complex implementation compared to alternatives

#### ADI ADAU7118 Analysis
**Pros:**
- Lowest specified active power consumption (1.2mA total for 8 channels)
- Smallest package size (3mm × 3mm LFCSP) optimizing PCB space
- Automatic PDM clock generation simplifies design
- Dual PDM clock outputs beneficial for synchronization
- TDM-16 support enables efficient interface to the Jetson platform
- 126dB SNR exceeds microphone specifications by a wide margin

**Cons:**
- Lower maximum sampling rate than alternatives (though 192kHz is still more than adequate)
- Narrower temperature range than the TI option (-40°C to +85°C)

#### Tempo TSDP18xx Analysis
**Pros:**
- Highest SNR (>142dB) of all options
- Excellent standby power consumption (<1μA)
- Flexible oversampling options (32x to 512x)
- 6th order 24-bit filtering

**Cons:**
- Active power consumption not clearly specified
- Package size not specified
- Less detailed documentation available compared to TI and ADI offerings

#### Final Selection: ADI ADAU7118

We have selected the ADI ADAU7118 as the optimal PDM to TDM converter for this application for the following reasons:

1. **Power Efficiency**: The ADAU7118 provides the lowest specified active power consumption, which is critical for a 16-element array that requires two converter chips.

2. **Compact Design**: The smallest package size (3mm × 3mm) enables a more compact microphone array design.

3. **Simplified Implementation**: 
   - Automatic PDM clock generation reduces design complexity
   - Dual PDM clock outputs simplify microphone synchronization
   - TDM-16 support creates a more standardized interface to the Jetson processor

4. **Adequate Performance**: The 126dB SNR and 192kHz maximum sampling rate significantly exceed our requirements for the 1kHz-8kHz target frequency range.

5. **Interface Efficiency**: The TDM-16 capability allows both chips to have their outputs potentially combined into a single synchronized data stream, simplifying the connection to the Jetson platform.

6. **System Integration**: The automatic features and well-documented specifications facilitate integration with the other components in the system.

While the TSDP18xx offers superior SNR and the PCMD3180 provides higher maximum sampling rates, these advantages aren't necessary given the microphones' specifications and the project's target frequency range. The ADAU7118 provides the optimal balance of power efficiency, form factor, simplicity, and performance for this application.

### Clock Distribution
- TBD: Precision clock distribution network for synchronizing all 16 microphones

### Audio Interface
- TBD: Multi-channel PDM interface compatible with Jetson platform

### Computing Platform
- **Selected Platform**: NVIDIA Jetson (specific model to be determined)
- **Rationale**: Integrated ARM CPU + CUDA-capable GPU for real-time audio processing and beamforming

## Additional Resources
- [Infineon XENSIV™ Sensor Solutions Catalog 2024](https://www.infineon.com/dgdl/Infineon-xensiv_sensor_solutions_2024-ProductSelectionGuide-v01_00-EN.pdf?fileId=5546d462636cc8fb0164229c09f51bbe&da=t)
- [IM73D122 Datasheet](https://www.infineon.com/cms/en/product/sensor/mems-microphones/mems-microphones-for-consumer/im73d122/)
