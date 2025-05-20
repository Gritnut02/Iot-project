# Iot-project
AltoTech
Problem - IoT Platform for Indoor Air Quality Data
Imagine you are an IoT engineer who is tasked with building a miniature IoT platform that reads real-time data from IAQ sensors (indoor air quality sensor), detects anomalies from the sensors, and notify the users of the anomalies.

📌 Sub-Problem 1 – IAQ Sensor Study & Recommendation
Research and identify the most suitable CO₂-temperature-humidity sensor brand for your platform. Survey at least 5 current IAQ sensor options in the market and make a comprehensive comparison in terms of important factors to consider (like price, sensor's technical specs, accuracy, power, Python-friendly interfaces) and then defend a single pick (or combo). 
IAQ Sensor Comparison Table 
| Sensor Name           | CO₂ Range (ppm)           | Accuracy (CO₂)           | Built-in T/H?        | Interface | Power                          | Price (USD) | Python Support | Notes                                                               |
| --------------------- | ------------------------- | ------------------------ | -------------------- | --------- | ------------------------------ | ----------- | -------------- | ------------------------------------------------------------------- |
| **SCD30** (Sensirion) | 0–40,000 (400–10k usable) | ±(30 ppm + 3%)           | ✅ Yes                | I²C, UART | 3.3–5V, \~19–75mA              | \~\$50      | ✅ Yes          | High accuracy, professional use, auto-compensation, well-documented |
| **SCD40 / SCD41**     | 400–2000 / 5000           | ±(50 ppm + 5%) typical   | ✅ Yes                | I²C       | SCD40: \~15mA / SCD41: \~0.5mA | \~\$40–\$50 | ✅ Yes          | Compact, low-power, good for battery use, slightly lower precision  |
| **MH-Z19B** (Winsen)  | 0–10,000 (configurable)   | ±(50 ppm + 3%)           | ❌ No                 | UART, PWM | 5V, \~60mA                     | \~\$20–30   | ✅ Yes          | Cheap, DIY-friendly, requires calibration & external T/H sensor     |
| **CCS811** (AMS)      | 400–8192 (eCO₂)           | Estimated only           | ❌ No (needs pairing) | I²C       | Very low                       | \~\$5–\$20  | ✅ Yes          | VOC-based CO₂ estimate, not reliable for true ppm, low-power        |
| **BME680** (Bosch)    | (IAQ Index only)          | Estimated only (BSEC AI) | ✅ Yes                | I²C, SPI  | \~18mA active                  | \~\$20      | ✅ Yes          | All-in-one air sensor, CO₂ is estimated via VOCs, great for trends  |
| **Senseair S8**       | 400–5000                  | ±(40 ppm + 3%)           | ❌ No                 | UART      | 4.5–5.25V, 18mA                | \~\$30–40   | ✅ Yes          | Stable and accurate, used in HVAC, more industrial grade            |

After comparing different IAQ sensors, I decided to go with the Sensirion SCD30 as the best choice for this platform. While there are other good sensors like the SCD41, MH-Z19B, or BME680, I chose the SCD30 because it gives the most accurate and reliable CO₂ data, and it fits well with the goals of this project.

One of the main reasons is that the SCD30 uses NDIR technology, which means it measures CO₂ directly, instead of estimating it based on VOCs like some cheaper sensors do. This matters because if the system is going to send alerts or control anything based on CO₂ levels, the data needs to be accurate and consistent.

Another thing I really liked is that it has built-in temperature and humidity sensors. That means the sensor can automatically adjust the CO₂ readings based on environmental changes, and I don’t have to connect extra sensors or write extra code to handle that. It helps keep the design simple and clean.

Since I’m using Python and RabbitMQ for this project, I also wanted something that works smoothly with that. The SCD30 has great support with libraries from both Sensirion and Adafruit, and there are lots of examples available. That made it much easier to get started and focus on building the rest of the system.

I also considered things like power and voltage. The SCD30 works with both 3.3V and 5V and doesn’t use too much current, so it fits well with the kind of boards I’m working with, like Raspberry Pi or ESP32.

Finally, the SCD30 isn’t just for hobby projects — it’s used in real IAQ systems that follow professional standards like WELL and RESET®. That gave me confidence that it’s a reliable sensor that could be used in actual buildings, not just for demos or lab work.

In short, I picked the SCD30 because it combines accuracy, ease of use, and professional quality. Even though it’s not the cheapest, I believe it’s worth it — especially if the goal is to build something that could work beyond just a prototype.
| 🔑 Reason                      | 💡 Explanation                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------------- |
| 🔬 **High Accuracy**           | True NDIR measurement with stable and precise readings (400–10,000 ppm)               |
| 🌡️ **Integrated T/H Sensor**  | Provides built-in temperature and humidity compensation for better CO₂ accuracy       |
| ⚙️ **Python Support**          | Full support from Adafruit & Sensirion libraries for CircuitPython and Python         |
| 🔌 **Power-Compatible**        | Operates easily on 3.3V or 5V, suitable for Raspberry Pi, ESP32, and microcontrollers |
| 🛠️ **Professional Use Ready** | Used in certified IAQ monitors (WELL™, RESET®), making it ideal for real deployment   |
| 📚 **Well-Documented**         | Excellent datasheets, sample code, open-source drivers, easy integration              |

🧠 What I Learned from Choosing This Sensor
Making this decision wasn’t just about hardware — it was about thinking like an engineer:
Choosing accuracy over cheap alternatives
Thinking ahead for scalability and maintenance
Making sure the sensor fits both the technical and practical goals of the project
In a way, the SCD30 helped me think about quality, not just cost — and that mindset will help me in future projects too. 
The Sensirion SCD30 gave me everything I needed: accuracy, reliability, and ease of integration. I believe it's a great choice for students or professionals building any serious IAQ monitoring system.

Even though it’s a bit more expensive than some alternatives, I see it as an investment in building a better and more trustworthy system. Whether this system is used in a home, classroom, or office, the data it collects matters — and with the SCD30, I know that data is solid.

While the SCD30 is an excellent all-around choice for accurate and reliable CO₂ monitoring, there are a few scenarios where alternative sensors may be more suitable depending on project requirements.

The SCD41, also from Sensirion, is a great option if the system needs to run on ultra-low power, such as in battery-operated devices. Although it offers slightly lower accuracy and a limited range of up to 5,000 ppm, it still provides reliable performance for environments where power consumption is a critical constraint.

If the budget is limited, the MH-Z19B can be a practical alternative. It’s much more affordable and still uses NDIR technology for direct CO₂ measurement. However, it does not include built-in temperature or humidity sensors, so you’ll need to add those separately if compensation or additional environmental data is required. It also requires occasional manual calibration for long-term accuracy.

For applications that don’t need exact CO₂ values but instead focus on trends or general air quality, sensors like the CCS811 or BME680 might be a good fit. These sensors are much cheaper and smaller but only provide estimated CO₂ values based on VOC readings. They work well for low-cost, basic IAQ monitoring, such as detecting patterns in indoor pollution or ventilation habits, but they are not recommended for projects that rely on precise CO₂ levels for control or alerts.

| Sensor            | Use If...                                                               |
| ----------------- | ----------------------------------------------------------------------- |
| **SCD41**         | You need **ultra-low power** (battery) and can accept <5000 ppm range   |
| **MH-Z19B**       | Budget is limited and you don’t mind **external temp/humidity sensors** |
| **CCS811/BME680** | You only need **trends**, not precise CO₂, and want cheap sensors       |

📌 Sub-Problem 2 – Sensor Data Simulation
Since we don't provide real sensors for this problem, please write a Python code to emulate 15 mocked IAQ sensors which publish the data into RabbitMQ message bus every 15 seconds. The message data should contain all necessary IoT data points including temperature, relative humidity, and CO₂ concentration.

📌 Sub-Problem 3 – Real-Time Fault-Detection Agent
In real-life, IoT devices and sensors occasionally malfunction and exhibit problematic behaviors. Write a Python agent which subscribe to the real-time data from all 15 mocked IAQ sensors and detect these following fault cases:
Sensor Disconnection: Sensor stops sending data or the sensor sends identical data points for more than 10 minutes.
Sensor Out-of-Range Readings: Sensor publishes abnormally reading values outside the physical limit (for example, temperature of 999 ˚C)
Too High CO₂ Concentration: The indoor air quality becomes unacceptable when the concentration of CO₂ remains higher than 1000 ppm for more than 20 minutes
This fault-detection agent should not only be able to detect the problem but also can notify the user about the problem as well. The notification can come in many possible channels (ex. Emails, Mobile Notification, Real-time Dashboard). Please pick 1 way for your platform to communicate with the users and also discuss the reasons why you choose this option. Also, develop a working prototype or demo for your choice of notification as well.

📌 Sub-Problem 4 – Go Beyond (optional)
Due to the high number of candidates this year, it would be great if you go beyond the basics to make your demo stand out—if you have a cool idea, new innovative feature, or a bit of extra polish in mind, add it!!! Surprise us more!!!

🤔 What You Need to Submit
For the solution of your assignment please submit the following documents,
GitHub repo containing all the codes and discussions (you may write non-code discussion in README.md file and put it in the same repo)
A sequence diagram, flow chart, or any other type of diagrams you use to plan and design before actually writing the code
(Optional) Link to your demo website
(Optional) Demo video
💡 Useful Tips
Age of AI: You may utilize AI tools (ex. ChatGPT, Cursor IDE, etc.) as much as possible for the test and I strongly encourage you to do so.
Plan before you code: Spend a few minutes outlining your approach and key steps—clear planning keeps you focused and avoids back-tracking later.
Explain your decisions: Wherever you make a choice (sensor picked, threshold set, alert channel chosen), try to write your ideas and thoughts as much as possible to demonstrate your reasoning process and analytical thinking.
