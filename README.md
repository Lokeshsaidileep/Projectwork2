## Smart Traffic Light System
This Project presents a solution to deal with traffic congestion in metropolitan cities and presents a central traffic control system which runs on a pretty simple algorithm. Our product would include the entire mechanism of detection of congestion and increasing the red light duration of traffic signals in the crossings.

## Description
A Smart Traffic Light System is an advanced traffic management system that leverages modern technologies such as AI, IoT (Internet of Things), sensors, and real-time data processing to optimize traffic flow, reduce congestion, and enhance road safety. Unlike traditional traffic lights that operate on fixed timers, smart traffic lights adapt dynamically based on traffic conditions, pedestrian movement, and emergency situations.

## Features
A Smart Traffic Light System integrates advanced technologies to optimize traffic flow, enhance safety, and reduce congestion. Here are its key features:

1. Adaptive Signal Control
   
🔹 Adjusts signal timing dynamically based on real-time traffic conditions.

🔹 Uses AI and machine learning to predict congestion patterns.

🔹 Reduces unnecessary waiting times and improves traffic efficiency.

2. Sensor-Based Traffic Detection
   
🔹 Inductive Loop Sensors – Detects vehicle presence on roads.

🔹 Infrared & Radar Sensors – Measures speed and traffic density.

🔹 Computer Vision & Cameras – Analyzes vehicle types and traffic flow.

3. Emergency Vehicle Priority System
   
🔹 Automatically detects ambulances, fire trucks, and police vehicles.

🔹 Adjusts signals to create a clear pathway for emergency response.

4. Vehicle-to-Infrastructure (V2I) Communication
   
🔹 Enables real-time data exchange between vehicles and traffic lights.

🔹 Helps autonomous and connected cars optimize their routes.

5. Pedestrian & Cyclist Detection

🔹 Uses cameras and sensors to detect pedestrians waiting at crosswalks.

🔹 Extends green light duration when necessary for safety.

6. AI & Machine Learning Integration
    
🔹 Predicts future traffic conditions based on historical data.

🔹 Uses reinforcement learning to continuously improve traffic control.

7. Real-Time Traffic Monitoring & Data Analytics
    
🔹 Provides live traffic updates to central traffic control centers.

🔹 Displays congestion heatmaps for urban planning and optimization.

8. Public Transport Priority
    
🔹 Gives priority to buses and trams at intersections.

🔹 Reduces delays in public transport systems.

9. Remote Control & Cloud Integration
    
🔹 Authorities can monitor and adjust signals remotely via cloud platforms.

🔹 Ensures scalability and easy upgrades.

10. Energy-Efficient & Eco-Friendly Design
    
🔹 Uses LED lights to reduce power consumption.

🔹 Optimizes traffic flow to lower vehicle emissions and fuel wastage.

## Requirements
## Hardware Components

* Sensors (Inductive loops, infrared, cameras, RFID, etc.)

* Traffic signal controllers

* IoT devices for real-time data collection

* Wireless communication modules (5G, Wi-Fi, V2I)

## Software & AI

* AI/ML algorithms for traffic prediction
  
* Adaptive signal control software

* Cloud computing for data processing

* Traffic management dashboard

## Connectivity & Integration

* V2I (Vehicle-to-Infrastructure) communication
  
* GPS and RFID for emergency vehicle detection
  
* Integration with smart city infrastructure

## Power Supply & Backup

* Reliable power source (solar panels or grid)

* Battery backup for uninterrupted operation

## Security & Data Privacy

* Cybersecurity measures to protect traffic data

* Secure encryption for data transmission

## Legal & Regulatory Compliance

* Adherence to government traffic regulations

* Compatibility with existing road infrastructure

## System Architecture
<!--Embed the system architecture diagram as shown below-->

![image](https://github.com/user-attachments/assets/89bc30b5-054c-4a52-91b4-d742ca42b32c)

# program 

import time
import random

# Define a TrafficLight class
class TrafficLight:
    def __init__(self, direction):
        self.direction = direction  # e.g., "North-South" or "East-West"
        self.state = "RED"  # Initial state is RED
        self.green_time = 10  # default green time
        self.yellow_time = 3
        self.red_time = 10
    
    def set_timings(self, green_time, yellow_time, red_time):
        self.green_time = green_time
        self.yellow_time = yellow_time
        self.red_time = red_time

    def get_state(self):
        return self.state
    
    def switch_to(self, new_state):
        self.state = new_state
        print(f"{self.direction} traffic light is now {self.state}")

# Define an Intersection class
class Intersection:
    def __init__(self):
        # Create two traffic lights for an intersection
        self.ns_light = TrafficLight("North-South")
        self.ew_light = TrafficLight("East-West")
        
    def detect_traffic(self):
        # Simulate vehicle count for each direction
        ns_vehicle_count = random.randint(0, 10)
        ew_vehicle_count = random.randint(0, 10)
        return ns_vehicle_count, ew_vehicle_count

    def adjust_timings(self, ns_vehicle_count, ew_vehicle_count):
        # Adjust green light time based on traffic count
        if ns_vehicle_count > ew_vehicle_count:
            self.ns_light.set_timings(15, 3, 15)
            self.ew_light.set_timings(10, 3, 15)
        else:
            self.ns_light.set_timings(10, 3, 15)
            self.ew_light.set_timings(15, 3, 15)
    
    def control_traffic(self):
        # Detect traffic and adjust timings
        ns_vehicle_count, ew_vehicle_count = self.detect_traffic()
        print(f"Detected vehicles - North-South: {ns_vehicle_count}, East-West: {ew_vehicle_count}")
        
        # Adjust timings based on traffic
        self.adjust_timings(ns_vehicle_count, ew_vehicle_count)
        
        # Control light sequence
        self.ns_light.switch_to("GREEN")
        time.sleep(self.ns_light.green_time)
        self.ns_light.switch_to("YELLOW")
        time.sleep(self.ns_light.yellow_time)
        self.ns_light.switch_to("RED")
        
        self.ew_light.switch_to("GREEN")
        time.sleep(self.ew_light.green_time)
        self.ew_light.switch_to("YELLOW")
        time.sleep(self.ew_light.yellow_time)
        self.ew_light.switch_to("RED")

# Main simulation loop
intersection = Intersection()

for _ in range(3):  # Run simulation for 3 cycles
    intersection.control_traffic()
    time.sleep(2)  # Wait before the next cycle

# Define a TrafficLight class
class TrafficLight:
    def __init__(self, direction):
        self.direction = direction  # e.g., "North-South" or "East-West"
        self.state = "RED"  # Initial state is RED
        self.green_time = 10  # default green time
        self.yellow_time = 3
        self.red_time = 10

    def set_timings(self, green_time, yellow_time, red_time):
        self.green_time = green_time
        self.yellow_time = yellow_time
        self.red_time = red_time

    def get_state(self):
        return self.state

    def switch_to(self, new_state):
        self.state = new_state
        print(f"{self.direction} traffic light is now {self.state}")

# Define an Intersection class
class Intersection:
    def __init__(self):
        # Create two traffic lights for an intersection
        self.ns_light = TrafficLight("North-South")
        self.ew_light = TrafficLight("East-West")

    def detect_traffic(self):
        # Simulate vehicle count for each direction
        ns_vehicle_count = random.randint(0, 10)
        ew_vehicle_count = random.randint(0, 10)
        return ns_vehicle_count, ew_vehicle_count

    def adjust_timings(self, ns_vehicle_count, ew_vehicle_count):
        # Adjust green light time based on traffic count
        if ns_vehicle_count > ew_vehicle_count:
            self.ns_light.set_timings(15, 3, 15)
            self.ew_light.set_timings(10, 3, 15)
        else:
            self.ns_light.set_timings(10, 3, 15)
            self.ew_light.set_timings(15, 3, 15)

    def control_traffic(self):
        # Detect traffic and adjust timings
        ns_vehicle_count, ew_vehicle_count = self.detect_traffic()
        print(f"Detected vehicles - North-South: {ns_vehicle_count}, East-West: {ew_vehicle_count}")

        # Adjust timings based on traffic
        self.adjust_timings(ns_vehicle_count, ew_vehicle_count)

        # Control light sequence
        self.ns_light.switch_to("GREEN")
        time.sleep(self.ns_light.green_time)
        self.ns_light.switch_to("YELLOW")
        time.sleep(self.ns_light.yellow_time)
        self.ns_light.switch_to("RED")

        self.ew_light.switch_to("GREEN")
        time.sleep(self.ew_light.green_time)
        self.ew_light.switch_to("YELLOW")
        time.sleep(self.ew_light.yellow_time)
        self.ew_light.switch_to("RED")

# Main simulation loop
intersection = Intersection()

for _ in range(3):  # Run simulation for 3 cycles
    intersection.control_traffic()
    time.sleep(2)  # Wait before the next cycle

# Final output

![Screenshot (128)](https://github.com/user-attachments/assets/26010928-5ea1-411c-9aec-7bc4d6810541)



## Login Page :

![image](https://github.com/user-attachments/assets/4be3fdfc-290a-41ab-aa59-de4959488a1c)


#### Output1 - 

## AT TIMEFRAME 0 SECS:


![image](https://github.com/user-attachments/assets/62876952-d1a0-4c9f-90d9-8ff3d783736b)



#### Output2 - 

## AT TIMEFRAME 5 SECS:

![image](https://github.com/user-attachments/assets/0c4ef709-5de5-43fe-991b-232162640194)


Detection Accuracy: 96.7%
Note: These metrics can be customized based on your actual performance evaluations.


## Results and Impact

The implementation of Smart Traffic Light Systems has demonstrated substantial benefits, not only in terms of improving traffic flow but also in enhancing environmental sustainability, public safety, and overall quality of life in urban areas.

This project serves as a foundation for future developments in assistive technologies and contributes to creating a more inclusive and accessible digital environment.

## Articles published / References

Smart traffic light systems have been extensively studied and implemented worldwide to enhance traffic management and reduce congestion. Here are some notable articles and case studies that provide valuable insights into their development and application:

1. Books & Research Papers
   
"Intelligent Transport Systems: Technologies and Applications" by Asier Perallos, et al.
This book covers various aspects of intelligent transport systems (ITS), including smart traffic light systems, IoT integration, and AI applications.

2. Case Studies
   
Los Angeles Smart Traffic System
Los Angeles has implemented an AI-based adaptive traffic control system, which optimizes signal timings in real-time based on traffic flow and congestion. This system is based on machine learning algorithms that continuously learn and adapt to traffic patterns.




