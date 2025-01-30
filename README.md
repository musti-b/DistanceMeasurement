# DistanceMeasurement

## Description
This project measures distances using sensors and provides a visual representation of the results through a display and LEDs. The system is designed to be intuitive and efficient, making it ideal for applications in automation, robotics, and safety systems. The project utilizes an ultrasonic distance sensor to capture measurements, which are then processed and displayed in real time. The LEDs serve as indicators for specific predefined ranges, providing immediate feedback on the measured distance.

The system is configured so that:
- **LED 1** lights up when the measured distance is **less than 1 meter**.
- **LED 2** lights up when the measured distance is **1 meter or more**.

Additionally, this system is designed to be easily replicable and customizable, catering to a wide range of use cases. By integrating affordable and accessible components like the Raspberry Pi and HC-SR04 sensor, the project demonstrates how advanced functionality can be achieved with minimal resources. This makes it suitable for educational purposes as well as practical implementations in various industries.

Future enhancements could include:
- Adding wireless communication for remote monitoring.
- Expanding the system with additional sensors for more complex measurements.
- Integrating a web interface to visualize data.

Detailed documentation ensures that users can set up and adapt the system with ease, even if they have limited technical experience.

## Features
- Accurate distance measurement using an ultrasonic sensor.
- Real-time display of results on an OLED or TFT screen.
- LED indicators for predefined distance ranges:
  - **LED 1**: Lights up for distances under 1 meter.
  - **LED 2**: Lights up for distances 1 meter or more.
- Affordable and accessible components for easy replication.
- Customizable and scalable design for various applications.

## Components Used
1. **Raspberry Pi Zero**
   - [Raspberry Pi Zero Official Page](https://www.raspberrypi.com/products/raspberry-pi-zero/)
2. **1.8" TFT Display** (or OLED display as an alternative)
   - [Adafruit 1.8" TFT Display Guide](https://www.az-delivery.de/products/1-8-zoll-spi-tft-display)
3. **Ultrasonic Distance Sensor** (e.g., HC-SR04)
   - [HC-SR04 Datasheet](https://www.electroschematics.com/hc-sr04-datasheet/)
4. **LEDs** (various colors for range indication)
   - [LED Basics and Guide](https://at.rs-online.com/web/p/leds/2285821?cm_mmc=AT-PLA-DS3A-_-google-_-CSS_AT_DE_Pmax_Test-_--_-2285821&matchtype=&&gad_source=1&gclid=Cj0KCQiA7se8BhCAARIsAKnF3rznNKA2HxQ9wTGR13j7zl4i7LzCYaMpnD7EsVWj06SVfzmgmllRapkaAu71EALw_wcB&gclsrc=aw.ds)
5. **Resistors** (for current limiting)
   - [Resistor Calculator](https://at.rs-online.com/web/p/durchsteckwiderstande/1987413?gb=s)
6. **Jumper Wires** (for connections)
   - [Amazon Jumper Wires](https://www.amazon.com/s?k=jumper+wires)
7. **Breadboard** (for prototyping)
   - [Breadboard Basics](https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard/all)

## Setup

### System Update and Preparation
1. Update and upgrade the Raspberry Pi:
   ```bash
   sudo apt update
   sudo apt upgrade -y
   ```

2. Install dependencies for Python 3.10:
   ```bash
   sudo apt install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev curl libbz2-dev
   ```

3. Download and install Python 3.10:
   ```bash
   curl -O https://www.python.org/ftp/python/3.10.9/Python-3.10.9.tgz
   tar -xf Python-3.10.9.tgz
   cd Python-3.10.9
   ./configure --enable-optimizations
   make -j $(nproc)
   sudo make altinstall
   ```

### Virtual Environment Setup
1. Install the virtual environment package:
   ```bash
   sudo apt install -y python3.10-venv
   ```

2. Create a virtual environment:
   ```bash
   python3.10 -m venv myprojectenv
   source myprojectenv/bin/activate
   ```

3. Install the required libraries:
   ```bash
   pip install RPi.GPIO Pillow adafruit-circuitpython-st7735r
   ```

### Hardware Configuration
1. Connect the **ultrasonic sensor** to the Raspberry Pi Zero's GPIO pins.
2. Wire the LEDs to GPIO pins with appropriate resistors for current limiting.
3. Connect the **TFT display** to the Raspberry Pi using SPI or I2C.
4. Enable SPI on the Raspberry Pi:
   ```bash
   sudo raspi-config
   ```

### Hardware Diagram
The following diagram illustrates the hardware connections for the project:

#### System Overview
![image](https://github.com/user-attachments/assets/d5e0348d-e3e6-413b-800a-8c15430dc286)

- **Ultrasonic Sensor**: Measures distance and sends the value to the Raspberry Pi Zero.
- **Raspberry Pi Zero**: Processes the distance data and controls the output.
- **LEDs**: Indicate distance ranges depending on the measured value.
  - **LED 1**: Lights up for distances below 1 meter.
  - **LED 2**: Lights up for distances equal to or greater than 1 meter.
- **OLED Display**: Shows the measured distance in real-time.
- **PC Connection**: Allows the measured values to be displayed on a PC for additional processing or monitoring.

#### Wiring Diagram
![image](https://github.com/user-attachments/assets/35d44442-e018-43f4-beb3-121a6cb7eaf1)

### Connection Table
![image](https://github.com/user-attachments/assets/6b9ea8e7-44de-404c-ba29-5c20a131fc14)


### Software Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/DistanceMeasurement.git
   cd DistanceMeasurement
   ```

2. Run the Python script:
   ```bash
   python distance_sensor.py
   ```

### System Behavior
- The distance will be measured in real time and displayed on the TFT or OLED display.
- The LEDs will indicate the range based on the measured distance:
  - **LED 1**: Lights up if the distance is **< 1 meter**.
  - **LED 2**: Lights up if the distance is **≥ 1 meter**.

### Optional Enhancements
- Modify the `config.py` file to adjust the distance thresholds or LED behaviors.
- Enable PC communication for advanced data visualization or remote control.


