# interactive-sound-board-frontend

## Group members

- Tristan De Lil
- Jonas De Rous
- Aaron Delplancq
- Rayan Azzi

## Link to all the modules

[ESP explenation](https://github.com/vives-project-xp/interactive-sound-board-ESP)

[Synthesizer explenation](https://github.com/vives-project-xp/interactive-sound-board-synthesizer)

[Front end explenation](https://github.com/vives-project-xp/interactive-sound-board-frontend)

[PCB design explenation](https://www.youtube.com/watch?v=xvFZjo5PgG0)

## Abstract

The original aim was to project a soundboard onto the ground.
This idea was transformed to create music via sensors by an object
changing height from the sensor.

## Project info

Below is a diagram of our structure
PHOTO SCHEDULE:

![sheme](./img/schema)

To keep this project as compact as possible, it contains two raspberry pi's 4 and 5 modules. Modules contain a PCB where an ESP and an ultrasonic sensors are mounted,
These are fed by 4 batteries connected to the esp at the bottom of the pcb.

The first rapsberry pi is responsible for communication between the other components and behaves as an access point. This ensures that the project is not dependent on internet networks and runs on its own local network.

The second raspberry pi is where the mosquitto broker runs and the synthesiser code.
The broker allows the components to communicate via MQTT and starts up automatically when the PI is connected. The synthesiser is the part that takes care of playing and adjusting the notes.

The modules communicate via MQTT with a synthesiser via specific topics, most notably that they will only measure and forward only when the synthesiser requests it.
This ensures that no heavy interference is measured.

The vue frontend size it possible to receive and modify the current configuration of the synthesiser:

- The type of wave can be changed to a sine , triangle , sawtooth and square wave.
- Adjust the volume, octave and frequency of the synthesiser.
- Also gives the user an overview of which devices are active.

The synthesiser program includes an MQTT client class that allows the values of the ultrasonic sensors to be read in and says when the sensors start and stop measuring and averages the value to reduce interference.
With then also the task of handling communication with the frontend.
The synthesiser program also contains a synthesiser class that averages the values to and value between 0 and 12.
It uses this value to extract the correct frequency from an octave.
The frequency is then put into the correct place in a list so that the index matches the module.
That list of notes are then played back on an audio device via bluetooth.

Link repos:

Link Youtube video: https://www.youtube.com/watch?v=GlRSXiBb0Xk

## Objective

The Main Objective was to mix ICT and music in a fun way.

| Objectives | sub-objectives
| :----- | :---------------------------------------------------------------------------------------|
| 1 | Have sensors record values |
| 2 | Let music play by making a link from a Raspberry Pi and a bluetooth device.|
| 3 | Create a frontend to adjust all kinds of factors via Vue and Vuetify.|
| 4 | Create a digital synthesiser with MQTT connection.|
| 5 | A Raspberry PI working as an access point.|
| 6 | Making a broker work on a second Raspberry PI.
| 7 | Create a PCB and connect the ESP to it.|

## Analysis

We had to do a lot of research on which way and how to undertake the project. We started with a possible structure after brainstorming so we could visualise what needed to be done and how we could do it.
We got the ESPs and sensors very quickly, so the research behind that could start quickly. Later came the idea for the frontend, so work on that started quickly. Also, the modules had to have a shell, so 3d models had to be made as well. Then came the idea of having a bluetooth box, so research into that began as well. A PCB was also needed to make, so that was started in time for it to be printed out.

## Result

As a result, we have 5 modules, each with a PCB, ESP, ultrasonic sensors and 4 batteries to power it. Those modules are connected to a Raspberry PI to connect to Vue and the bluetooth box to produce sound. There is also a second PI connected as Access Point. There is sound and the Front end interface works.

## Conclusion

Ur goal was from week one to realise an project with sound and differant modules. We got there on the end, was a challenge, but we learned a lot from it. The front end is user friendly and the final projects works. It is also scalabel and you can add many other feautres as possible extenssions.

## Possible extensions

Each note a unique frequency. Add LEDs and make them react to the music. For example we coud add an Led strip to the ESP module and it changes with the normalized value of the ultrasonic sensor. Fully Docker running project.
