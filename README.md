# Final Year Project: Human Computer Interface HCI using EEG signals.
Brain Computer Interface (BCI) is one type of Human Computer Interface, and it basically means a type of channel which allows the users to control the user interface or external devices, by the means of using embedding (invasive) or wearing (non-invasive) devices to detect brainwave signals or electroencephalogram (EEG) signal.

### Controlling cursors by using Emotiv INSIGHT headgear ###
Author: Eric Siow, <ericsiowkersiang@gmail.com>

Interface for testing: https://siowketan.github.io/

### Explanation of application
By merely looking at or watching the signals in software, it could be challenging to comprehend the meaning of each signal. In order to process the data, a Python application has been created. By wearing the headset beforehand, the mental commands were calibrated and established. The mental commands were saved in each person's training profile and updated on a server that stores the data associated with each command, called "WebSocket server". On Windows, Cortex Service could be regarded as a WebSocket server that uses the JSON-RPC protocol which is a means of communication between the Python program and the WebSocket Server. The Python application that has imported PyAutoGUI controls and manages the cursor, and executes the instructions on monitor. The WebSocket server transmits the commands in response to the data back to the Python program. Figure 1 also includes a conceptual diagram.

### Explanation of Repository

* **cortex.py** contains a set of pre-defined functions provided by cortex developer guide, besides cortex credential.
* **cursor_control.py** contains the executable program, besides cortex credential
* **Figure 1.png** contains a graphical explanation of how the program works.
* **pyautogui_test.py** is a testing script for author to understand how to use pyautogui library.
* **Figure 2.png** contains screen shot of the training profile and the Python program.

### Solution of some of the potential errors may occur:
1. Error: Did not find expected keys in client_id file D:\User\Desktop\cortex_creds.txt  or  OSError: no such file: D:\User\Desktop\cortex_creds.txt
   Solution: Parse a client_id file for client_id and client secret. We expect the client_id file to have the format:
            
            # optional comments start with hash
            client_id Jj2R3827GyABCxyz......
            client_secret abcdefghijJKLMNABCxyz......

2. Error: Modulenotfounderror: "No module named websockets" 
   Solution: Install the websockets package in python. Google it if not familar with python install package process.

3. Error: Invalid Profile Name
   Solution: This is due to that I changed the predefined function "load_profile" in cortex.py. To fix the error, open cortex.py and find where the function is declared, change '1stTry' in params to your own profile name. Your profile name can be found in the EmotivBCI app.
	
### Note from Author
This project idea is inspired by the work from https://github.com/kevinjycui/EEG-Cursor-Control and https://github.com/SiwenW/EMOTIV-INSIGHT-EEG-CURSOR-CONTROL
I got lots of help by looking at their codes and explanation: https://medium.com/@kevinjycui/of-mice-and-mind-creating-a-simple-eeg-cursor-control-application-7fcdad703d2f
