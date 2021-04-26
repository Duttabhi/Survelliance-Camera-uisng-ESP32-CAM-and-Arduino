# Surveillance-Camera-using-ESP32-CAM-and-Arduino

**Using the Wifi and pre-configured features to capture image, record video, do image processing and much more**

Check the CameraWebServer.ino code file.

ESP 32 CAM module (HW-297, AI-Thinker) with Arduino UNO

Check the Ranual PDF for step by step details.

Objective: Program an ESP32-CAM using Arduino to take pictures in specified time interval and store in the memory card. It deletes the data if the memory limit reaches.

Please [check](https://youtu.be/cwKTPlZjHkY) the YouTube video also. Do share and subscribe to the [channel](https://www.youtube.com/channel/UChRnDCfvbl_HCKYUfgMyIFA/playlists). 


Some **important settings** are as follows:

**Install Arduino IDE**

1. Visit https://www.arduino.cc/en/main/software

2. Download the IDE based on your Operating System.

3. Open the IDE.

**Get the ESP32 Add-on**

1. Got to **File menu**
2. Select **Preferences**
3. Paste the link in Additional Boards Manger test box: https://dl.espressif.com/dl/package_esp32_index.json
4. Click ok.
5. Click on Tools in the Menu Bar.
6. Go to Boards Manager and type ‘esp32’.
7. Install the version ‘1.0.4’ (it has some Face Recognition capabilities and is more trusted over 1.0.6, as far as my experience).
8. Go to tools again and select ‘Board: ESP32 Wrover Module’.

**Modify CameraWebServer Example on Arduino IDE**

Remark: You can copy the code from CameraWebServer.ino. There are supporting files for it as: (1) app_httpd.cpp (2) camera_index.h (3) camera_pins.h

1. Go to Examples > ESP32 > Camera > CameraWebServer.
2. Add 2 more headers:
3. #include "soc/soc.h"
4. #include "soc/rtc_cntl_reg.h "
5. Update your Wi-Fi credentials:
6. const char* ssid = “Your Wi-Fi ssid";
7. const char* password = “Your Wi-Fi password";
8. Add following line under void setup() method to supress the Brown out error due to pwer fluctuations: **WRITE_PERI_REG(RTC_CNTL_BROWN_OUT_REG, 0);**

**Connections should be done as follows:**

<img src="https://github.com/Duttabhi/Survelliance-Camera-uisng-ESP32-CAM-and-Arduino/blob/master/webServer.PNG" width=400>

**Uploading the project**

Following steps should be noticed

1. First connecting... will be seen
2. Now Downloading(1%)... Downlaoding(100%)
3. Then a Hard reset message will be there
4. After this remove the GPIO pin
5. Open the **serial monitor** from Tools menu
6. Press the reset button
7. You should see the URL for opening web server

**Making camera to cpature image after every 30 seconds automatically**

Remark: You need to press the reset button at the start to trigger the camera.

**Install Arduino IDE**: as above

**Get the ESP32 Add-on**: as above

**Code**

Remark: You can copy code from MemoryCapture.ino file

Some remarks of the code are

1. Pins for CAMERA_MODEL_AI_THINKER are defined at the beginnning but in the tools you should select Wrover Module (it's just the setting you know)
2. All the intialization is done in **void setup(){}**
3. The capturing and storing procedure is written in **void loop(){}** so that it can run again and again
4. Inside the loop() function a delay(30000) determines 30 seconds
5. **static int pictureNumber = 0;** is added to intialize the numbering from 0 and increase there after
6. In the end **esp_deep_sleep_start();** and codes nearby it are commented so that it may not go to sleep forever

**Connections should be done as follows:**

<img src="https://github.com/Duttabhi/Survelliance-Camera-uisng-ESP32-CAM-and-Arduino/blob/master/timeLapse.PNG" width=400>

**Uploading the project**: as above
