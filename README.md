# Illustration of Image Classification
The subsequent demonstration provides a recorded illustration of live image classification that has been executed on the Arduino Nicla Vision. The Nicla Vision's inbuilt camera is utilized to capture live images, following which the CNN model predicts the class of the image, along with its corresponding probability and inference time. It is to be note that the CNN model's computations are performed on the Arduino device, despite its resource constraints.
<p align="center">
<img src="https://user-images.githubusercontent.com/118956460/235283716-c6f0db76-2d03-4890-ad68-d6d1c4e0af46.gif" width="300" height="353" />
</p>

# Getting Started (Windows)
### Required Dependencies
* Edge Impulse CLI
* Arduino CLI

### [Installing Edge Impulse CLI](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-installation#installation-windows)
1. Start by creating an [Edge Impulse account](https://studio.edgeimpulse.com/signup).
2. Install [Python 3](https://www.python.org).
3. Install [Node.js](https://nodejs.org/en) v14 or higher.
    * Remember to check the 'Automatically install the necessary tools. Note that this will also install Chocolatey. The script will pop-up in a new window after the installation completes' check-box in the installation wizard during the installation.
    * It will open a powershell window after the installation wizard of Node.js finishes and install all the necessary tools.
4. Finally open a new cmd terminal (as administrator) and install the edge impulse cli tools with this code
        
        npm install -g edge-impulse-cli --force

### [Installing Arduino CLI](https://arduino.github.io/arduino-cli/0.32/installation/#latest-release)
* Follow this 1 minute, detailed [insctruction video](https://www.youtube.com/watch?v=1jMWsFER-Bc) to install Arduino CLI

Upon successful installation of Edge Impulse CLI and Arduino CLI, we are ready to proceed. However, prior to advancing, I would like to share some troubleshooting techniques that have helped me in resolving certain errors encountered during the installation of Edge Impulse CLI. To verify the correct installation of Edge Impulse CLI on your computer, execute the following code on the Windows command prompt:
        
        edge-impulse-daemon --clean
If everything is installed properly it should ask you to enter your login details of your edge impulse account. 

### Troubleshooting Edge Impulse CLI installation <a name="Troubleshoot"></a>
In case you come across the following error message whilst installing Edge Impulse CLI, the subsequent steps can be taken to rectify the issue.
<p align = "center">
<img src="https://user-images.githubusercontent.com/118956460/235285637-8f734415-4e3a-4503-a5ac-c70a246b538b.png" />
</p>

1. Open a new Power Shell window with administrator access and to list available versions of nvm (node version manager) run <a name="steps"></a>
         
         nvm list available
2. Then install the latest version of nvm with this code

         nvm install latest
3. After the installation run the following codes

         nvm use 16.3.0
         npm install -g edge-impulse-cli --force
4. If the installation proceeds without any errors, everything is well and good. However, if an error occurs with regards to Visual Studio, as shown below, then the subsequent troubleshooting steps can be implemented.
>...<br>
npm ERR! gyp ERR! find VS **************************************************************<br>
npm ERR! gyp ERR! find VS You need to install the latest version of Visual Studio<br>
npm ERR! gyp ERR! find VS including the "Desktop development with C++" workload.<br>
npm ERR! gyp ERR! find VS For more information consult the documentation at:<br>
npm ERR! gyp ERR! find VS https://github.com/nodejs/node-gyp#on-windows<br>
npm ERR! gyp ERR! find VS **************************************************************<br>
npm ERR! gyp ERR! find VS<br>
npm ERR! gyp ERR! configure error<br>
npm ERR! gyp ERR! stack Error: Could not find any Visual Studio installation to use<br>
...<br>

5. Download and install `Desktop development with C++` from this link: [Visual Studio](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community)
<p align = "center">
<img src="https://user-images.githubusercontent.com/118956460/235292426-979919f7-2cae-4269-a75a-813a5412d9c4.png" />
</p>

6. After installing Visual Studio retry the above mentioned [steps](#steps).

Follow this thread for more information on troubleshooting edge impulse cli installation: [Edge-impulse-cli install](https://forum.edgeimpulse.com/t/edge-impulse-cli-install/1293/15)

# Connecting Nicla Vision to Edge Impulse (Windows)

1. Download the [latest edge impulse firmware](https://cdn.edgeimpulse.com/firmware/arduino-nicla-vision-firmware.zip) and extract the zip file.
2. Connect Arduino Nicla Vision to your PC with a micro-USB cable and press the reset button twice to enter the bootloader indicated by flashing green LED on Nicla Vision.
3. Open the file named `flash_windows.bat` from the unziped files, and let the flash script run, once it is finished blue LED should turn on in your Arduino Nicla Vision.
4. Then run this command on a new cmd prompt `edge-impulse-daemon` and log in to your edge impulse account. Then select the project you want Arduino Nicla Vision to connect. `edge-impulse-daemon --clean` can be run if you want to re-login to edge impulse or select a different project to connect your Nicla Vision.
5. Open your edge impulse project in your browser, you should be able to see Arduino Nicla vision in your Devices tab.
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235293796-994913cf-3459-4124-825a-860c434ccf16.png" />
</p>

# Collecting Data
For gathering data, which comprises of labeled images, one can either upload images onto Edge Impulse directly or collect data from Arduino Nicla Vision. Here, the steps for collecting data from Nicla Vision will be outlined, as uploading data is a straighforward process.
1. Go to the Data acquisition tab, select Nicla Vision from the 'Device dropdown menu' and camera from the 'Sensor dropdown menu'. Once you select the camera you should see a live feed of the camera.
2. Type the class name in the Label box, and get the object in the frame of the camera. Click on 'Start sampling' to capture an image, it will automatically be uploaded to your project with the label you mentioned before.

Video Demonstration of collecting data: [Data Collection in Edge Impulse](https://www.youtube.com/embed/dY3OSiJyne0?start=240stop=250)
