# Lab Report 8 - There's an App for That: App Development
Eli Barrow & Isaac Stevens

March 7, 2024

## Summary of Lab ##

There were two main goals of this lab with them being to learn how to use the MIT App Inventor to control our robot using the Arduino cable and to control our robot using a Bluetooth device. Secondary goals for the lab included properly uploading code to the Arduino for MIT App Inventor to utilize and properly implement an HC-05 Bluetooth UART Module into a circuit to allow for connection by Bluetooth. To achieve these goals, we created a program to allow the user to control the movements of the robot through both wired and Bluetooth connections while using the same robot we created in Lab 6 of BAE 310.

For Part 1 of the lab, we used the same robot we assembled in Lab 6 and verified our robot could be moved forward, backward, left, and right according to commands sent via serial communications. We also found the minimum user input or speed that would move the car which was 40 input units. For Part 2 of the lab, we logged into the App Inventor 2 Web-based tool and created an app that would connect an Android phone to the Arduino through a wired connection by pressing a button. Once connected to the Arduino, there were 4 different buttons for 4 directions (forward, backward, left, right) as well as a slider to adjust the speed of the robot. For Part 3 of the lab, we included the HC-05 Bluetooth UART Module into the circuit to allow for Bluetooth connections. By modifying the code that was being uploaded into the Arduino through IDE and adding a Bluetooth connection section in our App Inventor 2 app, we can allow an Android phone to connect wirelessly to the Arduino through Bluetooth. To connect through Bluetooth, a button needs to be pressed on the app which will ask the Android phone for permission to use Bluetooth and what device they would like to connect to. Once the Android phone is connected wirelessly to the Arduino, both direction and speed can be controlled in the same way as Part 2.


### Lab Objectives: ###

1. To learn to use MIT App Inventor to control our robot using the Arduino cable

2. To learn to use MIT App Inventor to control our robot using a Bluetooth device

## Lab Assignment Specific Items ##

* A Computer running Arduino IDE, and a Browser
* A smartphone running Android OS with the MIT AI2 Companion app installed
* SparkFun Inventor's Kit
  - RedBoard
  - Ultrasonic Sensor
  - Two motors
  - Motor Driver
  - Battery Pack
* A cable/adapter to connect the smartphone to the RedBoard
* An HC-05 Bluetooth UART Module


## Methods and Testing ##
### Part 1 - Assemble and test your robot ###
For this part of the lab, we began by assembling the robot that we used in the lab last week. You can find the schematics and steps to build this robot in Lab 6 on my GitHub page. We assembled our robot and added the wheels onto the bottom of the main black support board, we were especially careful to make sure the alignment was perfect so the robot would drive straight. After that, we then moved into the Arduino IDE software to run our code from Lab 6 to ensure the robot would move forward, backward, left, and right when given the proper input in the serial communications. After assuring the code was still properly working we assembled the battery pack that is in our SparkFun kit and attached it to the belly of the car, assuring that it would not drag the ground when the car would drive.     
Below is an image of what the car should look like upon assembly. 

<p align="center">
  <img src= https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/15631-SparkFun_Inventor_s_Kit_for_Arduino_Uno_-_v4.1-02_600x600.jpg width = 50%> 
</p> 

* Figure 1 - This shows what the fully assembled robot should look like (This image was used from https://www.sparkfun.com/products/15631?gad_source=1&gclid=CjwKCAiA_5WvBhBAEiwAZtCU73IZjn6Ygoc5OvfVjj_N7WFA117QzH89FSEs2ahVhp6rlmaCpV1koxoCShYQAvD_BwE )

Below is how our robot car looked once assembled

<p align="center">
  <img src= https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Setup%20of%20Car.jpg width = 50%> 
</p> 

* Figure 2 - In-class example of our robot
  

### Part 2 - Develop the App ###
We started this part of the lab by creating an account and logging into the App Inventor Web-based tool, you can log into your account using the following link. https://login.appinventor.mit.edu/logout  

We then created a new project after signing in and gave it a descriptive name that was unique to our group. We then moved into the designer environment and inserted a button to initialize the serial communications when we would connect to the Arduino. We then found the Connectivity screen and added a Serial component. Then we found the Blocks section to add the blocks shown below to establish the communications after pressing the serial communications button. Button1 is the name of the button used to establish communications, and Open_Button is the name of the serial connectivity component. 

<p align="center">
  <img src=  https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%209.18.10%20AM.png width = 50%> 
</p> 

* Figure 3 - App inventor blocks needed to control the serial communications

<p align="center">
  <img src= https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Creating%20Program.jpg width = 50%> 
</p> 

* Figure 4 - Eli using App Inventor 2 in the lab

The next step was to use the block "call serialObject.WriteSerial" and a regular "text" block to send the commands to the RedBoard. This is the way we are replacing the serial command box on the Arduino IDE software with buttons. Each button will send the text that we would normally type into the serial command box to control the car.

An image of our user interface and another image with all of the code blocks is shown below.

<p align="center">
  <img src=  https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%202.14.17%20PM.png width = 50%> 
</p> 

* Figure 5 - User interface setup for our app


<p align="center">
  <img src=  https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%202.51.06%20PM.png width = 50%> 
</p> 

* Figure 6 - A behind-the-scenes look at the code blocks behind the user interface

  
After this was finished we then built our app by selecting the build dropdown bar and then selecting the .apk file type. We had Dr. Jarro download it on his phone since our group only had Apple devices. We then connected the Arduino cable that was connected to our car to Dr. Jarro's phone so he could use the app to control our car.


### Part 3 - Wireless Remote ###
In this section of the lab, we focused on trying to connect the phone to a Bluetooth device that would control our car. The first step of this part of the lab was to attach the Bluetooth HC-05 device to our circuit. 
The schematic for the addition of the HC-05 is shown below.

<p align="center">
  <img src= https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%202.18.37%20PM.png  width = 50%> 
</p> 

* Figure 7 - Schematic for HC-05 (Accessed from Lab 8 Document on Canvas)


After correctly adding the HC-05 into our circuit we then open Arduino IDE code that had previously been written to control our robot. We then added the code botDirection (char type, 'f' for forward,'b' for backward,'r' for right,'l' for left) and botSpeed(int type). Those variables will receive the data and save it.

We were then given the following code to insert before the setup function.
```c++

#include <SoftwareSerial.h>

//Create software serial object to communicate with HC-08
SoftwareSerial mySerial(3, 2); //HC-05 Tx & Rx is connected to Arduino #3 & #2

const byte numChars = 6;
char receivedChars[numChars];   // an array to store the received data
char tempChars[numChars];

char botDirection[1] = {0};


int botSpeed = 0;
int motorSpeed = 0;

boolean newData = false;

```
* Cody Display 1: This code was provided in the Lab 8 Document through Canvas    


We were then given the following code to insert inside the setup function

```c++
void setup()
{
mySerial.begin(9600);
}
```
* Cody Display 2: This code was provided in the Lab 8 Document through Canvas     
  
We were then given the following code to insert inside the loop function.

```c++

recWithEndMarker ();
if (newData == true)
{
  strcpy(tempChars, receivedChars);
  parseData();
  motorSpeed = botSpeed;
  newData = false;
}

```
* Cody Display 3: This code was provided in the Lab 8 Document through Canvas

We then added the following functions

```c++

void recWithEndMarker() {

  static byte ndx = 0;
  char endMarker = '\n';
  char rc;

  while (mySerial.available() > 0 && newData == false) {

    rc = mySerial.read();

    if (rc != endMarker){

        receivedChars[ndx] = rc;
        ndx++;
        if (ndx>= numChars){

          ndx = numChars -1;
        }

    }
    else {

        receivedChars[ndx] = '\0';
        ndx =0;
        newData = true;

    }


  }


}

void parseData() {      // split the data into its parts

    char * strtokIndx; // this is used by strtok() as an index

    strtokIndx = strtok(tempChars," ");      // get the first part - the string
    strcpy(botDirection, strtokIndx); // copy it to messageFromPC
 
    strtokIndx = strtok(NULL, " "); // this continues where the previous call left off
    botSpeed = atoi(strtokIndx);     // convert this part to an integer
}

```

* Cody Display 4: This code was provided in the Lab 8 Document through Canvas



After copying those lines of code and inserting them in the previously made car driving file, we then opened the App Inventor 2 and saved a copy to our computer. Next from the connectivity section, we added the object BluetoothClient which would allow us to send data through Bluetooth. Then from the User Interface, we added a ListPicker object that will let us select the Bluetooth device we are using. Next under the user interface section, we added a Label object that will show us the status of the Bluetooth connection. After that, we then moved over to the Blocks environment and added the blocks that are shown below.

<p align="center">
  <img src=  https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%202.34.00%20PM.png width = 50%> 
</p> 

* Figure 8 - Setup blocks for moving into Bluetooth control

After creating those blocks, for each of the buttons replace the "call serialObject.WriteSerial" block with a "call BluetoothClient.SendText" block as shown in the image below. Be sure to include the new line command "/n" because this is used by the Arduino code the identify the end of the sent command. 

<p align="center">
  <img src= https://github.com/elibarrow/BAE305-SP24-LAB8/blob/main/Screenshot%202024-03-04%20at%202.50.10%20PM.png width = 50%> 
</p> 

* Figure 9 - Example after converting original blocks to Bluetooth-capable blocks
  
When it came to testing our system we were unable to get it to properly run. We had Dr. Jarro take a look at it and we tried to get it to run properly but we never could come up with a solution.


## Results ##


**Part 1**

Successfully assembled the robot and verified the robot could be moved forward, backward, left, and right according to commands sent via serial communications.

**Part 2**

Created an app through App Inventor 2 which allowed for the robot to be controlled by an Android phone through a wired connection. This app allowed the user to connect and choose a direction (forward, backward, left, and right) for the robot to drive while also being able to adjust the speed with a slider.

**Part 3**

By integrating an HC-05 Bluetooth UART Module into the circuit and modifying the code that was being uploaded in the Arduino through IDE, Bluetooth was able to be used by the Arduino. By adding a Bluetooth connection section in the App Inventor 2 app, the Android phone will click a button in the app to ask for Bluetooth permission and to allow the app to connect to the Arduino from a list of devices. Once the Android phone is connected wirelessly to the Arduino, both the direction and speed can be controlled in the same way as Part 2.


## Discussion Questions ##

**Part 1**

**1. What is the minimum speed that will move the complete car?**

The minimum speed that will move the complete car is a user input of 40.


## Conclusion of Lab 8 ##

As stated in the summary of the lab, there were three parts to Lab 8. For Part 1 of the lab, we used the same robot we assembled in Lab 6 and verified our robot could be moved forward, backward, left, and right according to commands sent via serial communications. For Part 2 of the lab, we logged into the App Inventor 2 Web-based tool and created an app that would connect an Android phone to the Arduino through a wired connection by pressing a button. Once connected to the Arduino, there were 4 different buttons for 4 directions (forward, backward, left, right) as well as a slider to adjust the speed of the robot. For Part 3 of the lab, we included the HC-05 Bluetooth UART Module into the circuit to allow for Bluetooth connections. By modifying the code that was being uploaded into the Arduino through Arduino IDE and adding a Bluetooth connection section in our App Inventor 2 app, an Android phone can connect wirelessly to the Arduino through Bluetooth. By pressing a button in the app, the Android phone is asked for permission to use Bluetooth and what device they would like to connect to. Once the Android phone is connected wirelessly to the Arduino, both direction and speed can be controlled in the same way as Part 2. For the conclusions reached in the lab, we learned how to use App Inventor 2 to create an app that would allow an Android phone to connect physically and wirelessly to the Arduino. Once connected, the app could be used to change the direction and speed of the car through the app. To allow Bluetooth connection to the Arduino, we learned how to properly connect an HC-05 Bluetooth UART Module to the circuit as well as implement code into Arduino IDE which would utilize the HC-05 Bluetooth UART Module and allow Bluetooth connections.
