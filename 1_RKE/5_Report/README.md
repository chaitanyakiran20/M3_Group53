# REMOTE KEYLESS SYSTEM




# Abstract:

Remote keyless entry (RKE) has captivated automobile buyers, as evidenced by the popularity of RKE on new automobiles and as an after-market item. This application note provides an overview of RKE systems and discusses how they meet requirements such as range, battery life, reliability, cost, and regulatory compliance. It shows some circuits and design approaches and offers some predictions for future systems, which will include two-way communications.

## Introduction 

Remote keyless entry (RKE) is an electronic access system that can be controlled from a distance. RKEs, which are typically used to remotely lock or unlock doors, require the end user to initiate an action that will cause a physical or software key fob to transmit a radio signal to a receiver that controls an electronic lock. Typically, the action is to press a button on a physical fob.Remote keyless entry, which is commonly used to protect vehicles from theft, can be contrasted with passive keyless entry (PKE), which does not require any action on the part of the end user. 

## Identifying Features

* It should lock the door when blue switch is ON that is when switch is pressed.
* It should be unlock when switch presses two times.
* It should activate/deactivate alarm when switch presses three times.
* It should approach when switch is pressed four times.

## High Level Requirements


| ID | High Level Requirement |
|----|------------------------|
|HLR1|  It should lock the car|
|HLR2| It should unlock the car|
|HLR3|It should activate/deactivate the alarm|
|HLE4| It should probvide light when pressed four times|

## Low Level Requirements
| ID | Low  Level Requirement |
|----|------------------------|
|LLR1|When locked,all the leds ON at same time|
|LLR2| When unlocked,all the leds OFF at same time|
|LLR3|When alarm activates/deactivates, all led on in clockwise manner|
|LLR4|When approaches light,all the leds ONin anti-clockwise manner|

## SWOT ANALYSIS

![image](https://user-images.githubusercontent.com/87614111/157808397-f4098f3f-7219-4400-b5c3-8add00c4ad96.png)


# Strength
* Less human interaction.
* Control the car remotely.
* Avoiding the chance of thefts.

# Weakness
* Next command will be in processes after completion of previous command.
* There may be problem with locking and unlocking when the distance is beyond threshold.

# Oppurnities
* This type of systems are mainly used for the cars.


# Threats
* The key fob doesnot work consistently.
* There may be chance of hacking.


# 4W's And 1H

![image](https://user-images.githubusercontent.com/87614111/157808679-4d4b7b7f-e078-4ef9-a8d4-a9117bcc981f.png)

# WHAT
 A Remote keyless system controls the vehicle without using a traditional mechanical key.We can remotely access a car.
 # WHY
 RKE Systems are used for locking and unlocking a vehicle's doors by controlling the remote.
 # WHERE
 It is used for car owners where they can make the task self without unecesserly inserting the key.
 # WHEN
 It is used for cars as there is a chance of thefts.This can be used for locking and locking of doors of a car.
 # WHO
 RKE Systems are used by car users which are developed by automative engineers.So they must offer low cost and high reliability.
 # HOW
 There are functions on a key knob which are used for automatic door locking and unlocking for a car.


# Architecture

## High Level Behavioral Diagram

![mod3](https://user-images.githubusercontent.com/87614111/157728056-a079e066-1df3-4f4f-92f5-74ae15b7fe2d.jpg)

## Low Level Behavioral Diagram


![mod 32 (1)](https://user-images.githubusercontent.com/87614111/157812013-8c2524c5-1053-46e1-8a2f-f3e8db2c9939.jpg)


# Circuit Diagram

* Future Reference
![RKE Circuit](https://user-images.githubusercontent.com/34639178/157867292-89d8ce60-b6b3-456e-8457-b472fe4129df.png)




# High Level Test Plan
 
  |  Test  ID	   |  Description	    | Expected I/P	  |   Expected O/P      |	   Type of Test  |
  |----------|------------------|-----------------|---------------------|----------------|
  |          |                  |                 |                     |                |                |
  |  HP01    |  lock            |  Switch is pressed once  |   locks the door  |  Requirement   |
  |  HP02    |  Unlock            |  Switch is pressed twice  |   unlocks the door  |   Requirement   |
  |  HP03    | activates/deactivates alarm            |  Switch is pressed three times  |   buzes the alarm  |   Requirement   |
  |  HP04    | approaches light           |  Switch is pressed four times  |  ONs the light |   Requirement   |
  
  
# Low Level Test Plan
   
 | Test ID	   |  Description	    | Expected I/P	  |   Expected O/P      |	   Type of Test  |
  |----------|------------------|-----------------|---------------------|----------------|
  |          |                  |                 |                     |                |                |
  |  LP01    |  lock            |  Switch is pressed once  |   All leds on at same time  |  Requirement   |
  |  LP02    |  unlock            |  Switch is pressed ontwicw  |   All leds off at same time  |  Requirement   |
  |  LP03    | activates/deactivates alarm            |  Switch is pressed three times  |   All leds on in clockwise manner  |  Requirement   |
  |  LP04    | approaches light           |  Switch is pressed four times  |   All leds on in Aanti-clockwise mannert |   Requirement   |
  
  





