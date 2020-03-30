# SIT210-Task3.1P-WebHook
SIT210-Task3.1P-WebHook Programming task for university assignment


Dan Jeffs S215475485
SIT210 Task 3.1P

Task Submission Details
Q1. Provide brief summary (less than two paragraphs) of your
understanding of Webhooks and their usage.

Web-hooks provide simplified method of access to the API of other web systems and software. They are used to retrieve (GET) or send (POST) information to and from we services and sensors.

Q2: Describe the steps you have taken to create this application similar
to an instruction manual. Use bullet points and be concise when
possible. Your instructions should be enough for another person reading
them to recreate what you have done (You might as well opt for creating
a video)
1.	I created a system using my Particle Argon and an AM2303 temp and humidity sensor. There are several pre-written libraries available for getting the data from the sensor to the particle. 
2.	I opted for the Adafruit_DHT.h library to access the device as it seemed more stable.
3.	I then modified the example code given in the library to include the following lines – 
// Read Dew Point 
  float dp = DHT.getDewPoint();
  // Read Humidity
  float h = DHT.getHumidity();
  // Read temperature as Celsius
  float t = DHT.getCelsius();
  // Read temperature as Farenheit
  float f = DHT.getFahrenheit();
  Particle.publish("readings", String::format("{\"Hum(\%)\": %4.2f, \"Temp(°C)\": %4.2f, \"DP(°C)\": %4.2f}", h, t, dp));
 Particle.publish("Temperature", String::format("%4.2f",t),PRIVATE);
4.	I also removed most of the print to console lines.
5.	I then proceeded to setup the API’s from both ThingSpeak and from Particle to push the data between the services making sure that the API access was looking for the right word in the output “Temperature” as per my code in particle. 

Q3: Submit the graph of your ThinkSpeak chart over a period of 5
minutes (create some artificial change in the reading if you can, e.g.
change the luminosity of the room by turning lights on and off) by taking
a screenshot of your thing speak similar to the sample below.
 


Q4: Create a repository named SIT210-Task3.1P-WebHook on Github.
Upload your code to the repository. Include the link to your repository
here.
https://github.com/DanJeffs/SIT210-Task3.1P-WebHook



Q5: Describe a real-life usage scenario for your system (less than one
paragraph).
This would be quite useful for gathering data for a household, web connected, smart temp monitoring and switching, heating and cooling system. I also plan on using this specific piece of code do display temp and humidity data on a Magic Mirror project I’m working on.
