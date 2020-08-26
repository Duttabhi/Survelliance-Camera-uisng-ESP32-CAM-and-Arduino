# Survelliance-Camera-uisng-ESP32-CAM-and-Arduino
ESP 32 CAM module (HW-297, AI-Thinker) with Arduino UNO
Check the README PDF for step by step details.

Objective: Program an ESP32-CAM using Arduino to take pictures in specidied time interval and store in the memory card. It deletes the data if memory limit reaches.

Please [check](https://youtu.be/cwKTPlZjHkY) the YouTube video also. Do share and subscribe the [channel](https://www.youtube.com/channel/UChRnDCfvbl_HCKYUfgMyIFA/playlists). 


Some **important settings** are as follows:

**Install Arduino IDE**
• Visit https://www.arduino.cc/en/main/software
• Download the IDE based on your Operating System.
• Open the IDE.

**Get the ESP32 Add-on**
• Click on Tools in the Menu Bar.
• Go to Boards Manager and type ‘esp32’.
• Install the version ‘1.0.4’ (it has some Face Recognition capabilities).
• Go to tools again and select ‘Board: ESP32 Wrover Module’.

**Modify CameraWebServer Example on Arduino IDE**
• Go to Examples > ESP32 > Camera > CameraWebServer.
• Add 2 more headers:
1. #include "soc/soc.h"
2. #include "soc/rtc_cntl_reg.h "
• Update your Wi-Fi credentials:
1. const char* ssid = “Your Wi-Fi ssid";
2. const char* password = “Your Wi-Fi password";
• Add following line under void setup() method:
1. WRITE_PERI_REG(RTC_CNTL_BROWN_OUT_REG, 0);

**Sample Image:**

<img src="https://github.com/Duttabhi/Survelliance-Camera-uisng-ESP32-CAM-and-Arduino/blob/master/esp32%20cam.jpg" width=400>

