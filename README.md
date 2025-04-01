# ICHY - 16-Element Microphone Phased Array

## Project Overview
ICHY is a 16-element microphone phased array designed for high-precision audio source localization and beamforming. This document outlines the key design considerations, components, and implementation approach.

## Key Design Elements

### Hardware
- **Microphones**: 16 MEMS microphones with matched frequency response
- **Geometry**: Circular array configuration for 360° coverage
- **Spacing**: λ/2 spacing to prevent spatial aliasing at target frequencies
- **ADC**: Simultaneous sampling across all channels
- **Processing Unit**: FPGA or high-performance MCU for real-time processing

### Signal Processing
- **Beamforming Algorithm**: Delay-and-sum with optional adaptive algorithms
- **Calibration**: Inter-microphone calibration methodology
- **Filtering**: Band-pass filtering to focus on frequencies of interest
- **Direction Finding**: MUSIC or SRP-PHAT algorithm implementation

### Software
- **DSP Pipeline**: Real-time processing chain
- **Visualization**: Direction-of-arrival display
- **Interface**: Configuration and monitoring interface
- **Data Storage**: Recording capabilities for post-processing

### Performance Targets
- **Angular Resolution**: <5° at target frequency range
- **Frequency Range**: 1kHz - 8kHz optimal operation
- **Processing Latency**: <50ms for real-time applications

## Data Acquisition Architecture

### Minimal Hardware Configuration for Jetson Processing

#### Essential Hardware Components
- **Microphones**: 16 digital MEMS microphones (I2S/PDM output)
- **Clock Source**: Single master clock with distribution network to ensure phase alignment
- **Audio Codec/Interface**: Audio interface with multi-channel input capabilities
- **Physical Array Structure**: Precise physical positioning framework for microphones
- **Power Conditioning**: Clean power supply with proper isolation

#### Non-Replaceable Hardware Elements
1. **Microphone Transducers**: Physical conversion of sound to electrical signals cannot be done in software
2. **Clock Synchronization Hardware**: Physical timing alignment between microphones (~1μs precision)
3. **Physical Array Geometry**: Precise spatial positioning that affects beamforming accuracy
4. **Signal Conditioning**: Analog filters and buffers to maintain signal integrity
5. **ADC Hardware**: Conversion from analog to digital (integrated in digital MEMS mics)

### Jetson-Based Processing Approach
- **Direct Interfaces**: Utilize Jetson's I2S/SPI interfaces for direct microphone connection where possible
- **Audio Interface Options**:
  1. Direct connection of PDM microphones to Jetson's hardware interfaces
  2. Multi-channel audio codec with TDM output connected to Jetson
  3. USB audio interface with multi-channel capability

### Software-Replaceable Components
- **Digital Filtering**: All filtering can be performed in software on Jetson
- **Beamforming Algorithms**: Implemented entirely in CUDA on Jetson GPU
- **Signal Conditioning**: Digital gain, normalization in software
- **Channel Synchronization**: Fine synchronization adjustments in software
- **Calibration**: Software-based microphone calibration routines
- **Direction Finding**: All direction finding algorithms in CUDA

### Jetson Processing Implementation
- **Nvidia Jetson Advantages**:
  1. **Integrated Solution**: ARM CPU cores + CUDA-capable GPU on single board
  2. **Direct I/O**: Hardware interfaces for connecting to microphone array
  3. **Unified Memory**: Shared memory architecture for efficient CPU-GPU data exchange
  4. **Complete Software Stack**: CUDA libraries for signal processing optimization
  
- **Jetson Signal Processing Pipeline**:
  1. **Data Acquisition**: 
     - Direct digital sampling from microphones via I2S/PDM interfaces
     - DMA transfer to Jetson memory with minimal CPU involvement
  
  2. **Pre-Processing on CPU**:
     - Initial buffering and sample rate conversion if needed
     - Channel synchronization fine-tuning
     - Data preparation for GPU processing
  
  3. **GPU Processing with CUDA**:
     - Batch processing of multi-channel audio data
     - FFT-based operations across all channels in parallel
     - Beamforming coefficients calculation
     - Direction-of-arrival estimation using MUSIC/SRP-PHAT
  
  4. **Real-time Visualization and Output**:
     - Direction finding results visualization
     - Beamformed audio output
     - Optional raw data storage for post-processing

- **Optimized Jetson Implementation**:
  - Use of Jetson-specific optimizations (cuDNN, TensorRT if applicable)
  - Zero-copy memory operations between CPU and GPU when possible
  - Asynchronous processing to maintain real-time performance
  - GPU kernel fusion to minimize data movement

### Power and Thermal Considerations
- **Power Distribution**: Clean, low-noise power supply to each microphone
- **Isolation**: Digital/analog domain isolation to prevent noise coupling
- **Thermal Design**: Heat dissipation strategy for continuous operation

## Next Steps
- Detailed microphone selection and array geometry calculation
- Electronics design and component selection
- DSP algorithm implementation
- Mechanical design and housing
- Software development and user interface
- Testing and calibration methodology

## References
- Key academic papers and resources for phased array design
- Component datasheets and reference implementations