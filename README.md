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

Upon successful installation of Edge Impulse CLI and Arduino CLI, we are ready to proceed. However, prior to advancing, I would like to share some troubleshooting techniques that have helped me in resolving certain errors encountered during the installation of Edge Impulse CLI.
### Troubleshooting Edge Impulse CLI installation
<p align = "center">
<img src="https://user-images.githubusercontent.com/118956460/235285637-8f734415-4e3a-4503-a5ac-c70a246b538b.png" />
</p>
