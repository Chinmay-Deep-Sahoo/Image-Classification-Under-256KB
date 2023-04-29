# Illustration of Image Classification<a name="live"></a>
The subsequent demonstration provides a recorded illustration of live image classification that has been executed on the Arduino Nicla Vision. The Nicla Vision's inbuilt camera is utilized to capture live images, following which the CNN model predicts the class of the image, along with its corresponding probability and inference time. It is to be note that the CNN model's computations are performed on the Arduino device, despite its resource constraints.
<p align="center">
<img src="https://user-images.githubusercontent.com/118956460/235283716-c6f0db76-2d03-4890-ad68-d6d1c4e0af46.gif" width="300" height="353" />
</p>

# Getting Started (Windows) <a name="GS"></a>
### Required Dependencies <a name = "RD"></a>
* Edge Impulse CLI
* Arduino CLI

### [Installing Edge Impulse CLI](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-installation#installation-windows)<a name = "ECLI"></a>
1. Start by creating an [Edge Impulse account](https://studio.edgeimpulse.com/signup).
2. Install [Python 3](https://www.python.org).
3. Install [Node.js](https://nodejs.org/en) v14 or higher.
    * Remember to check the 'Automatically install the necessary tools. Note that this will also install Chocolatey. The script will pop-up in a new window after the installation completes' check-box in the installation wizard during the installation.
    * It will open a powershell window after the installation wizard of Node.js finishes and install all the necessary tools.
4. Finally open a new cmd terminal (as administrator) and install the edge impulse cli tools with this code
        
        npm install -g edge-impulse-cli --force

### [Installing Arduino CLI](https://arduino.github.io/arduino-cli/0.32/installation/#latest-release)<a name = "ACLI"></a>
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

# Connecting Nicla Vision to Edge Impulse (Windows)<a name = "Connect"></a>

1. Download the [latest edge impulse firmware](https://cdn.edgeimpulse.com/firmware/arduino-nicla-vision-firmware.zip) and extract the zip file.
2. Connect Arduino Nicla Vision to your PC with a micro-USB cable and press the reset button twice to enter the bootloader indicated by flashing green LED on Nicla Vision.
3. Open the file named `flash_windows.bat` from the unziped files, and let the flash script run, once it is finished blue LED should turn on in your Arduino Nicla Vision.
4. Then run this command on a new cmd prompt `edge-impulse-daemon` and log in to your edge impulse account. Then select the project you want Arduino Nicla Vision to connect. `edge-impulse-daemon --clean` can be run if you want to re-login to edge impulse or select a different project to connect your Nicla Vision.
5. Open your edge impulse project in your browser, you should be able to see Arduino Nicla vision in your Devices tab.
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235293796-994913cf-3459-4124-825a-860c434ccf16.png" />
</p>

# Collecting Data<a name = "Collect"></a>
For gathering data, which comprises of labeled images, one can either upload images onto Edge Impulse directly or collect data from Arduino Nicla Vision. Here, the steps for collecting data from Nicla Vision will be outlined, as uploading data is a straighforward process.
1. Go to the Data acquisition tab, select Nicla Vision from the 'Device dropdown menu' and camera from the 'Sensor dropdown menu'. Once you select the camera you should see a live feed of the camera.
2. Type the class name in the Label box, and get the object in the frame of the camera. Click on 'Start sampling' to capture an image, it will automatically be uploaded to your project with the label you mentioned before.

Video Demonstration of collecting data: [Data Collection in Edge Impulse](https://www.youtube.com/embed/dY3OSiJyne0?start=240)

# Building Machine Learning Model<a name = "Model"></a>
This section will detail the steps involved in designing the machine learning architecture which will be utilized for training on the collected data. One may either construct and train their own custom model or opt to use pre-trained models provided by Edge Impulse, which can be utilized for transfer learning and fitting our dataset. The subsequent steps are tailored towards transfer learning.
1. Go to the 'Create impulse' tab under 'Impulse design' and select input image width and height in the 'Image data' block.
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235295375-04e8bcc9-8070-4f14-a518-36f8f66eef4c.png" />
</p>

2. Add an image block by clicking on the 'Add a processing block' and selecting Image.
3. Then add a Classification block by clicking on the 'Add a learning block' and selecting Classification. Then click on 'Save Impulse'
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235295586-6a0874c2-d4b8-4f64-a169-82089e50801e.png" />
</p>

4. Next, go the 'Image' tab under 'Impulse design', select the Color depth as RGB or Grayscalse and click on 'Save parameters' and then click 'Generate features'.
5. Finally, go to the 'Classifier' tab under 'Impulse design' and select appropriate parameters and click on 'Start training' to train our machine learning model.
6. Wait for the model to complete the training and then move to the next section.

Video Demonstration of Building Model: [Build Model](https://www.youtube.com/embed/dY3OSiJyne0?start=529)

# Model Selection through EON Tuner<a name = "EON"></a>
An alternative method of designing a model involves searching for the optimal model which can accommodate the resource constraints of the Arduino Nicla Vision. EON Tuner offers an AutoML feature which enables the discovery of the optimal model to enhance the accuracy of our image classification task. The following section will detail the steps required to identify the optimal model.
1. Go to the 'EON Tuner' tab and select your target device i.e Nicla Vision, then select your acceptable latency and click on 'Start EON tuner'.
2. Once the search process is finished, a list of different models along with their respective accuracy, latency, RAM, and ROM usage will be displayed as illustrated in the following image.
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235297208-ff27fc43-1bc6-4c0d-bdbc-2ddd502bd275.png" />
</p>

3. Find the model which fits the RAM and ROM requirements with the best accuracy and train that model again in the 'Classifier' tab.

# Deploying Model to Nicla Vision<a name = "Deploy"></a>
Deploying the trained weights to our device is a simple process in Edge Impulse, which can be done in just three easy steps. Once the model is trained and finalized, follow the steps below to deploy it to the device.
1. Go to the 'Deployment' tab and scroll down to the 'Build firmware' section.
<p align = "center">
   <img src="https://user-images.githubusercontent.com/118956460/235298264-90fe0a5e-ab64-468a-98f7-377a81804622.png" />
</p>

2. Next, choose 'Arduino Nicla Vision' as the device and scroll down to click on the 'Build' button. Wait for the process to complete, and upon completion, your browser will automatically download a zipped file with required firmware for Nicla Vision.
3. Finally, enter the bootloader mode of the Arduino Nicla Vision by pressing the reset button twice. Afterward, unzip the downloaded file and open the `flash_windows.bat` file. Let it finish.

### Issues while deployement<a name = "deploy-issue"></a>
If the model is taking more RAM than available in Arduino Nicla Vision you might get an error while building the firmware in edge impulse. To resolve this issue, you can either train a smaller model or use the EON Tuner feature as described earlier to search for an optimal model that satisfies the device's resource constraints while maximizing accuracy.

# Running Live Classification on Arduino Nicla Vision<a name = "live"></a>
After completing the previous sections successfully, you can now proceed with the following steps to perform inference on your trained model for real-world image classification using live camera input from your device.
1. Open cmd in Windows.
2. Run the following command to show the classification results in the command prompt. Results includes predicted probability of each class. 
         
         edge-impulse-run-impulse
3. Run the following command to show the classification results with the live camera feed on your browser like shown [here](#live). This command will give you a web url which you can open to see the live calssification results.

         edge-impulse-run-impulse --debug
         
# Table of Contents
* [Getting Started](#GS)
   * [Required Dependencies](#RD)
   * [Installing Edge Impulse CLI](#ECLI)
   * [Installing Arduino CLI](#ACLI)
   * [Troubleshooting Edge Impulse CLI installation](#Troubleshoot)
* [Connecting Nicla Vision to Edge Impulse (Windows)](#Connect)
* [Collecting Data](#Collect)
* [Building Machine Learning Model](#Model)
* [Model Selection through EON Tuner](#EON)
* [Deploying Model to Nicla Vision](#Deploy)
   * [Issues while deployement](#deploy-issue)
* [Running Live Classification on Arduino Nicla Vision](#live)
* [SSS](#steps)
