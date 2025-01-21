
# UWB-Workshop

This is the instruction for UWB workshops with Murata Type 2BP Evaluation Board on Windows PC to run a demo code.  
The demo code will set up communication between the 2BP EVB and an Iphone to show the direction and range of the UWB EVB.  
Please go through the PPT if you do not know anything about UWB.  

## 1. Install and Setup the Software Development Environment


### 1.1 Install terminal tool  

Install terminal tool such as **Putty** or **Tera Term**  


### 1.2 Install [FTDI VCP dirver](https://ftdichip.com/drivers/vcp-drivers/)  

Test the driver by plugging in the development board. Open device manager on your computer. If the driver is installed successfully, you should see a new COM port (e.g. com3) showing up under Ports when the board is plugged in.


### 1.3 Install Python  

Python 3.7 or later is required. Dounload from: [Python Download](https://www.python.org/downloads/)  

### 1.4 Install Python libraries  

>pip install matplotlib pyserial zmq pycryptodome  

Install pip if you dont have it on your PC  

>py -3 –m ensurepip


### 1.5 MCUXpresso IDE 

Download MCUXpresso IDE 11.3 or later and run the installer. You may need to create NXP 
account to download the installer from: 
[MCUXpresso Integrated Development Environment (IDE)](https://www.nxp.com/design/design-center/software/development-software/mcuxpresso-software-and-tools-/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE)  


### 1.6 Download QN9090 SDK  

  1. QN9090 SDK is the basic SDK for MCUXpresso. 
  Visit the [SDK site](https://mcuxpresso.nxp.com/en/select)  
  2. Under Select Board /Processor Tab, search for "QN9090", then you can find boards -QN9090DK6
  ![image](https://github.com/user-attachments/assets/8ae745c4-97b7-4af9-bc3f-aceb71e7c7a9)  
  Scole down and click **BUILD SDK** button.  
  3. Make sure the Host OS is correct and Toolchain is MCUXpresso IDE. **Select All** the dependencies, then click **BUILD SDK** button  
  ![image](https://github.com/user-attachments/assets/078a6a5f-e794-4f3b-91ab-eaa6648bdd9a)  
  Click **Download** button.  
  4. EULA may appear. Read carefully and follow the instructions.  
  5. Download will start automatically, and you will get SDK_x.x.x_QN9090DK6.zip.  

###  1.7 Install QN9090DK SDK  

  1. Launch MCUXpresso IDE.  
  2. Type Workspace directory as you want and click Launch button.
     ![image](https://github.com/user-attachments/assets/0734e72b-b8e2-4959-bafa-29eaba0522e1)
  3. If you see the Welcome page, click “X” button on the Welcome tab
  4. Find SDK_x.x.x_QN9090DK6.zip on explorer and drag and drop the zip file into Installed SDKs tab (No need to do this again if you see the SDK in the Installed SDKs window).
     ![image](https://github.com/user-attachments/assets/6d397a61-7db4-4d85-8448-bd666eb2af79)  

### 1.8 Install DK6Programmer

  1. Unzip the SDK_x.x.x_QN9090DK6.zip file.  
  2. Run the installer (JN-SW-4407 DK6 Production Flash Programmer v4564.exe) in tools/JN-SW-4407-DK6-Flash-Programmer.
     ![image](https://github.com/user-attachments/assets/804ffb7b-3fc8-4455-a9af-4e66a81d5b70)

  3. Click **I Agree**.  
  4. Click **Install**.
  5. DK6Programmer application is installed.
     ![image](https://github.com/user-attachments/assets/a02a00e9-2bd1-4f4f-a854-17d86006d6ee)


## 2. Import Sample Project
  1. Launch MCUXpresso IDE. 
  2. Type Workspace directory as you want and click Launch button
  3. Unzip UWBIOT_SR150_v04.06.00_MCUx.zip into the directory you selected above
  4. From menu, select File ➔ Import
     ![image](https://github.com/user-attachments/assets/9acd9224-adcc-4ca4-9d6d-121946b0cb7a)
  5. Select General ➔ Existing Projects into Workspace and click the Next button
     ![image](https://github.com/user-attachments/assets/a122d717-e5b0-4932-abfa-769f63fd1e5c)
  6. Click the Browse … button. Select UWBIOT_SR150_v04.06.00_MCUx folder you unzipped in the previous step.
  7. You will see imported projects in Project Explorer window.
     ![image](https://github.com/user-attachments/assets/3deb4fff-22a7-4b05-b865-c64c45d1afd7)

## 3. Applying Patch File

  1. Inside MUCXpresso UWBIOT_SR150_Vxx.xx.xx_MCUx project, Right click on **RhodesV4_SE<Debug>**.
  2. Point **Team**
     ![image](https://github.com/user-attachments/assets/1f2aae77-bf43-4335-bcbc-2185d3bd9316)

  4. Click **Apply Patch**
  5. Click **Browse**
  6. Select your path of **2bp_prebuilt_vxx.xx.xx.patch**.
  7. Click **Finish**

## 4. Build and Program Sample Application
  The SDK includes several sample applications. Select one sample application at a time. 
  1. Launch MCUXpresso IDE. 
  2. Type a Workspace directory as you want and click Launch button
  3. Expand RhodesV4_SE and double click **UWBIOT_APP_BUILD.h**
     ![image](https://github.com/user-attachments/assets/6fcffb4a-73d2-45a0-84b3-478740b752a0)

  4. Comment out (disable define) **UWBIOT_APP_BUILD__DEMO_BINDING** and uncomment (enable define) **UWBIOT_APP_BUILD__DEMO_NEARBY_INTERACTION**
     ![image](https://github.com/user-attachments/assets/951ef9f1-6f82-401c-910b-695ed23d5e45)

  5. From the menu, select Project ➔ Build All
     ![image](https://github.com/user-attachments/assets/2b5c9770-9990-4ca9-8458-51ce80b42b45)
     
  7. You can see build log in Console window. Wait for a while to see the Build Finished
     ![image](https://github.com/user-attachments/assets/773c0236-3d6e-4349-bb4d-43551ea8652f)
     
  8. You can find binary images in uwbiot-top\project\RhodesV4_SE\Debug. **RhodesV4_SE.bin**
     ![image](https://github.com/user-attachments/assets/793bb571-2c25-42f8-9838-6a1a5ae4ac62)
     
  9. Use DK6Programmer to upload the program
     Copy the bin file (uwbiot-top\project\RhodesV4_SE\Debug) generated by the build to the folder where the DK6Programmer was installed.
  10. Open the DK6Programmer path in powershell
     ![image](https://github.com/user-attachments/assets/031be8e6-fc63-43c3-b195-02f962326393)
     
  11. Execute the DK6Programmer application.
      Flashing command:
      >./DK6Programmer.exe -V 0 -P 1000000 -s COMx -Y -p xxxx.bin

      Replace the COM number and file name.  
      Example of execution is shown below.  
      ![image](https://github.com/user-attachments/assets/34686266-76c3-4393-af6f-1b763967b86d)

  12.  Launch Putty and select the **Serial** connection type.Enter the correct COM port number. If you use SDK v04.02.01 or earlier, then the baud rate is 115200 bps. If you use SDK v04.04.03 or later then the baud rate is 3000000 bps.
      ![image](https://github.com/user-attachments/assets/ce0b263f-266e-4f10-bb6c-c3288a80387d)
      ![image](https://github.com/user-attachments/assets/a3a8a7a7-d47c-40c7-b9d6-47c1e7c83a51)
      ![image](https://github.com/user-attachments/assets/06bf985b-3700-43ba-9d55-deb969f18a01)


## Install NXP UWB AR DEMO App

“NXP Trimensions AR” application is available on App Store. Install this App to perform the test.   
![image](https://github.com/user-attachments/assets/a33268a5-0fce-435f-a01c-bfdd53c78a8e)

Once the “NXP Trimensions AR” app is run, the iPhone 12 will detect the Type 2BP EVK and start 
ranging. This app shows both range and direction.  



**Congratrulations**, you have completed the demo setup.





