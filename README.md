STM32 microcontrollers using STM32 HAL library.
🚀 Features

Seven-Segment Display Control: Displays digits 0-9 with proper segment patterns
IR Sensor Integration: Detects objects and increments counter
Debouncing: Prevents multiple counts from single detection
Auto Reset: Counter resets to 0 after reaching 9
HAL Library: Uses STM32 HAL for better portability

🛠️ Hardware Requirements

STM32 microcontroller (tested on STM32F4xx series)
Common cathode seven-segment display
IR sensor module (active high output)
Current limiting resistors (220Ω - 330Ω for each segment)
Breadboard and jumper wires

📋 Pin Configuration
Seven-Segment Display
SegmentSTM32 PinDescriptionAPA0Top horizontalBPA1Top right verticalCPA2Bottom right verticalDPA3Bottom horizontalEPA4Bottom left verticalFPA5Top left verticalGPA6Middle horizontalDPPA7Decimal point
IR Sensor
ComponentSTM32 PinDescriptionIR SensorPB0 (configurable)Digital input
🔧 Circuit Diagram
STM32           Seven-Segment Display
PA0 ----[330Ω]---- Segment A
PA1 ----[330Ω]---- Segment B
PA2 ----[330Ω]---- Segment C
PA3 ----[330Ω]---- Segment D
PA4 ----[330Ω]---- Segment E
PA5 ----[330Ω]---- Segment F
PA6 ----[330Ω]---- Segment G


PB0 --------------- IR Sensor OUT
3.3V -------------- IR Sensor VCC
GND --------------- IR Sensor GND
                    Display Common Cathode
📂 Project Structure
stm32-7segment-ir-counter/
├── Core/
│   ├── Inc/
│   │   └── main.h
│   └── Src/
│       └── main.c
        └── main.txt
├── Drivers/
│   └── STM32F4xx_HAL_Driver/
├── README.md
🚀 Getting Started
Prerequisites

STM32CubeIDE or any STM32-compatible IDE
STM32CubeMX (for configuration)
STM32 HAL library
Hardware components listed above

Installation

Clone the repository
bashgit clone https://github.com/yourusername/stm32-7segment-ir-counter.git
cd stm32-7segment-ir-counter

Open in STM32CubeIDE

Import the project into your workspace
Build the project (Ctrl+B)


Hardware Setup

Connect the seven-segment display to PA0-PA7 with current limiting resistors
Connect the IR sensor to PB0 (or configure as needed)
Power the circuit with 3.3V/5V as required


Flash the Program

Connect your STM32 via ST-Link
Flash the program to your microcontroller



🎯 How It Works

Initialization: The system initializes GPIO pins and displays '0'
Sensor Monitoring: Continuously monitors IR sensor input
Edge Detection: Detects rising edge (object detection)
Counter Increment: Increments display counter (0-9)
Display Update: Updates seven-segment display with new digit
Debouncing: 200ms delay prevents multiple counts
Auto Reset: Counter resets to 0 after reaching 9

Code Structure

Segment Patterns: Hex values for each digit (0-9)
Edge Detection: Prevents continuous counting
HAL Functions: Clean, portable GPIO operations
Debouncing: Software-based bounce elimination

⚙️ Configuration
Customizing Pins
Edit the pin definitions in main.h:
c#define IR_Sensor_Pin GPIO_PIN_0
#define IR_Sensor_GPIO_Port GPIOB
Adjusting Debounce Delay
Modify the delay in main.c:
cHAL_Delay(200); // Adjust this value (milliseconds)
Display Type
For common anode displays, invert the segment patterns:
cuint8_t segment[10] = {
    ~0x3f,// 0 (inverted)
    ~0x06,// 1 (inverted)
    // ... etc
};
🐛 Troubleshooting
IssueSolutionDisplay shows wrong digitsCheck wiring and segment patternsMultiple counts per detectionIncrease debounce delayNo response from IR sensorVerify sensor wiring and powerDisplay too dim/brightAdjust resistor values
🔮 Future Enhancements

 Multiple digit displays
 Different counting modes (up/down)
 EEPROM storage for count persistence
 LCD display option
 Interrupt-based sensor reading
 PWM brightness control

🤝 Contributing

Fork the repository
Create a feature branch (git checkout -b feature/enhancement)
Commit changes (git commit -am 'Add new feature')
Push to branch (git push origin feature/enhancement)
Create a Pull Request


🙏 Acknowledgments

STMicroelectronics for HAL library
STM32 community for support and resources
Open source embedded development communit
Show Image

⭐ Star this repository if you found it hel
