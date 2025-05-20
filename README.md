# Iot-project
AltoTech
Problem - IoT Platform for Indoor Air Quality Data
Imagine you are an IoT engineer who is tasked with building a miniature IoT platform that reads real-time data from IAQ sensors (indoor air quality sensor), detects anomalies from the sensors, and notify the users of the anomalies.

📌 Sub-Problem 1 – IAQ Sensor Study & Recommendation
Research and identify the most suitable CO₂-temperature-humidity sensor brand for your platform. Survey at least 5 current IAQ sensor options in the market and make a comprehensive comparison in terms of important factors to consider (like price, sensor's technical specs, accuracy, power, Python-friendly interfaces) and then defend a single pick (or combo). Please discuss the reasoning behind your selection as well.

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
