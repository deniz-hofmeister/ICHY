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
