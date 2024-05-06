## Table of Content: 
### 1. Introduction
### 2. Software
### 2.1 Python
### 2.2 Arduino C++
### 3. Hardware setup
### 4. Conclusion

---


## 1. Introduction to the Deep Space Probe Simulator (DSPS)

#### What is DSPS?

The Deep Space Probe Simulator (DSPS) is an innovative, educational toolkit designed to replicate the functions and challenges of a space probe operating in deep space environments. This simulator serves as a hands-on educational platform, providing users with an immersive experience in aerospace technology, control systems, and environmental sensing. 

#### Purpose of the Project

The primary goal of the DSPS is to inspire and educate future engineers, scientists, and hobbyists by providing a realistic experience of designing, building, and operating a space probe. Through this simulator, users can gain practical insights into the complexities of space exploration technology, including hardware design, software control, and the integration of various electronic sensors.

#### Why Create DSPS?

In the realm of educational tools, there remains a significant gap in resources that combine the technical challenges of aerospace engineering with accessible, hands-on learning. The DSPS project aims to fill this gap by offering a detailed and scalable model that mimics real-world systems used in space missions. This includes:

- **Environmental Data Gathering:** Utilizing sensors to measure conditions such as temperature, humidity, and pressure, simulating the data collection done by space probes in different celestial environments.
- **Wireless Communication:** Implementing modules that manage data transmission over distances, echoing the communication hurdles faced by space missions between spacecraft and Earth.
- **Software Control Mechanisms:** Developing an interface that allows users to send commands and receive data, providing insights into the software and network requirements of space mission control.

#### Target Audience

The DSPS is intended for:
- **Educational Institutions:** As a teaching aid for students in science, technology, engineering, and mathematics (STEM) fields, especially those focused on space technology and remote sensing.
- **Hobbyists and Amateurs:** Individuals passionate about space and technology, looking to explore these interests through a practical, hands-on project.
- **Research and Development Groups:** Teams working on satellite technology and remote sensing, who can use the DSPS as a prototype for testing and validation.

#### Educational and Professional Development

By engaging with the DSPS, users will:
- Develop a solid understanding of the technical requirements and challenges involved in space probe missions.
- Acquire hands-on experience in electronics and software programming through the construction and customization of their version of the DSPS.
- Enhance their problem-solving and critical thinking skills by troubleshooting hardware and software issues during the simulation.

The DSPS project not only broadens the knowledge and skills of those involved but also aims to ignite a passion for space exploration and innovation, paving the way for the next generation of engineers and scientists.

---

## 2. Software

Software is pivotal in the development and operation of the Deep Space Probe Simulator (DSPS). It serves as the critical interface through which data is both retrieved from and transmitted to the hardware components. To facilitate a thorough understanding and effective utilization of the DSPS, the following guidelines are systematically divided into comprehensive sections, ensuring a structured approach to deployment and operation.

The instructional content begins with an introduction to the Python programming segment. This section details the specific code necessary for initiating and managing communication protocols between the DSPS hardware and the software interface. Following this, the focus shifts to the Arduino platform. Here, you will learn how to configure and program the Arduino to interact seamlessly with the DSPS, which is essential for real-time data handling and processing.
Subsequently, the guidelines elucidate the procedure for establishing a robust connection between your computing device and the DSPS. This involves setting up the necessary network or direct connections, configuring relevant settings, and ensuring reliable communication pathways are in place.

Finally, the manual covers the procedures for data streaming. This portion instructs on how to effectively capture, transmit, and visualize the data generated by the DSPS. By following these step-by-step instructions, users will be equipped to harness the full capabilities of the DSPS, ensuring optimal performance and functionality in various applications. Each section is designed to build upon the previous one, thereby providing a cohesive and comprehensive framework for DSPS deployment and use.

### 2.1 Python

To get started:
1. Open your favourite IDE, for this I recommend VS Code.
2. Create a new folder which will hold your Python script.
3. Create a main.py script in the new folder you just made.
4. Clone or copy the main.py code from this git repository. (https://github.com/deneskosztyuk/DSPS_Guide-Deep-Space-Probe-Simulator/blob/main/main.py)
5. Head to the "Terminal" tab in VS Code (or press "ctrl+`" on Windows, alternatively you can click on the View tab at the top and choose Terminal from the list)
6. In the Terminal that just opened install the necessary python libraries in order to make the main.py script work.
To install the necessary libraries paste the following command into your Termnial: "pip install requests pillow flask matplotlib"

#### Here is a detailed breakdown what each library is used for in the application.
- **Standard Python Libraries:**
  - `os`: Provides a way of using operating system dependent functionality.
  - `signal`: Set handlers for asynchronous events.
  - `threading`: Construct higher-level threading interfaces on top of the lower level thread module.
  - `itertools`: Functions creating iterators for efficient looping.
  - `datetime`: Classes for manipulating dates and times.
  - `math`: Mathematical functions (according to the C standard).

- **Third-Party Libraries:**
  - `requests`: Allows you to send HTTP/1.1 requests easily.
  - `tkinter as tk`: Standard Python interface to the Tk GUI toolkit.
  - `PIL (Python Imaging Library)`: Adds image processing capabilities.
    - `Image`: Provides a class with the same name which is used to represent a PIL image.
    - `ImageTk`: Contains support to create and modify Tkinter BitmapImage and PhotoImage objects from PIL images.
    - `ImageSequence`: An iterator to loop over an image sequence.
  - `flask`: A micro web framework for Python.
    - `Flask`: The class that acts as the central object. It is an instance of this class that becomes the WSGI application.
    - `request`: The request object used by default in Flask. Contains all the information about the request.
    - `jsonify`: Creates a JSON response from a dictionary.
  - `matplotlib`: A plotting library for Python and its numerical mathematics extension NumPy.
    - `Figure`: The top level container for all the plot elements.
    - `backend_tkagg`: A backend for Matplotlib to be used with Tkinter.
    - `gridspec`: Specifies the geometry of the grid that a subplot will be placed in.

At this point all the necessary libraries are installed and you shouldn't get any errors.

### 2.2 Arduino IDE & C++ 

- Go ahead and download Arudino IDE if you haven't already: https://www.arduino.cc/en/software
- Open the Arduino IDE. Before you paste the code from this repository we need to install a few things here as well, type in each name individually until you installed all libraries from the list below:
  - **WiFi**: For connecting to the internet using the WiFi protocol.
  - **Wire**: For communication with I2C / TWI devices.
  - **Adafruit_Sensor**: For a unified sensor interface.
  - **Adafruit_BME280**: For interfacing with the BME280 sensor (temperature, humidity, and pressure).
  - **HTTPClient**: For making HTTP requests.
  - **ArduinoJson**: For JSON encoding and decoding.

You can install these libraries by opening the Arduino IDE, going to `Sketch > Include Library > Manage Libraries...`, and then searching for each library by name. Once found, you can click on the library and then click the "Install" button to install it.
Remember that some of these libraries may have dependencies on other libraries, so make sure to check the documentation for each library to ensure you have all the necessary components installed for your project.

- Once you installed the necessary libraries, go ahead and copy the code that ends with .ino from this repository.
(https://github.com/deneskosztyuk/DSPS_Guide-Deep-Space-Probe-Simulator/blob/main/dsps.ino)
This section will be a bit more comprehensive but dont worry, just read throug the guide carefully.
There are a few things you will need to change in the `dsps.ino` file, find the:
`const char* ssid = "ENTER YOUR WIFI NETWORKS NAME EXACTLY";  // Replace with your hotspot's SSID
const char* password = "CHANGE THIS TO YOUR NETWORKS PASSWORD";  // Replace with your hotspot's password`
Replace the values in the quotation marks, in the `ssid` enter the exact name of your home WiFi network.
In the same manner, replace the values in the quotation marks, in the `password`, enter the exact password of your WiFi network.
This setup will ensure both DSPS and the PC you are using are running on the same network as the device uses HTTP to send and recieve requests and data.

- Further down, on line 36 you will see the following code line: `http.begin("CHANGE THIS TO YOUR IPv4/sensor-data"); // Your server's URL, example: http.begin("192.168.1.1/sensor-data");`

Here you will need to enter the IPv4 that you will get when you run the main.py script in VS Code, check the console and find the IPv4 address, copy it and paste it into the dsps.ino line where it says `"CHANGE THIS TO YOUR IPv4"`

With this setup we are done with the software part.

### 3. Hardware

##### Hardware prerequisites
To setup the DSPS you will need the following hardware, you can find these cheap on places like `Amazon`.
- Breadboard
- ESP32 Microcontroller
- Micro USB cable (Make sure its capable of data transfer and not just charging, check the description)
- BME280 Sensor
- Jump wires (male to male, female to male)
- LEDs

1. Place the breadboard on a flat surface, use a red jump wire to connect both positive lines marked with `+` on both side, do the same for the `-`, this ensures the entire board can be powered and grounded no matter from where you would want to connect your wires up.

2. Connect a wire from the `3V3` pin on the ESP32 to the `+` positive line on the breadboard. This will supply 3 volts across the board.

3. Setup the BME280. Place the BME280 on the breadboard:
- Connect the `GND` pin to the `-` on the breadboard.
- Connect the `VIN` pin to the `+` on the breadboard.
- Connect the `SCL` pin of the BME280 to pin `22` on the ESP32.
- Connect the `SDL` pin of the BME280 to the pin `21` on the ESP32.
Now you have the BME280 sensor successfully setup.

4. [Optional] You can setup an LED to give visual feedback on the connection status of your hardware setup.
- Connect the short leg of the LED to ground (`-` line on the breadboard)
- Connect the long one to one end of a 220 Ohm resistor, the other leg of the resistor connect to pin `23` on the ESP32.

---

## Conclusion

Now that you succesfully setup both codes and the hardware, go ahead and Verify button in the Arduino IDE, once succesfully compiled press the `Upload` button next to it to upload your code to the ESP32, once successful you should see BME280 readings in the `Serial Monitor` (second tab at the bottom once the code has been uploaded, or the maginifying glass icon in the top right). Once that's done, head on to VS Code and run your main.py code, you will see the DSPS Control Software switch on, from this point you can start playing around with it as you successfully made a simple satellite probe in a home setting.

If for any reason you experience issues or bugs, use the `Contact Me` on my webpage: [denesk.co.uk](https://www.denesk.co.uk/)
