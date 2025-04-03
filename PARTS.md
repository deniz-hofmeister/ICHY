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
- **Description**: PDM to TDM audio converter
- **Channels**: [Number of PDM channels]
- **Output Format**: TDM compatible with Jetson platform
- **Sampling Rate**: [Supported sampling rates]
- **Package Size**: [Package dimensions]
- **Power Consumption**: [Power specifications]
- **Special Features**: [Key features]
- **Price Range**: [Approximate cost]
- **Supplier Link**: https://www.mouser.co.uk/new/analog-devices/adi-adau7118-converter/

#### Comparison Table

| Feature | TI PCMD3180 | ADI ADAU7118 |
|---------|------------|-------------|
| Channels | [# channels] | [# channels] |
| Sampling Rates | [rates] | [rates] |
| Package Size | [dimensions] | [dimensions] |
| Power | [consumption] | [consumption] |
| Key Advantage | [unique selling point] | [unique selling point] |
| Price | [cost] | [cost] |

*Note: Complete specifications need to be filled in from datasheets. Detailed comparison to be updated once datasheets are reviewed.*

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
