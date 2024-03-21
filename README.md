# Gesture prediction for prosthetic hand model

A prosthesis that replaces a limb must have the same functionality as a real arm or leg. To provide the device with the necessary capabilities, data about various gestures must be stored in its memory. This can be done using two components:

- Optomyographic cuff (hereinafter we will refer to it as OMG cuff) with sensors;
- The pilot is the person who will perform the movements.
  
The cuff, worn by the pilot, allows you to collect data on muscle contraction, and based on this information, identify the gesture that occurs when these muscles contract.

The cuff is similar to the one found in a blood pressure monitor. You don't need to make any manipulative settings. The device operates on the basis of a model with training using machine algorithms.

Now the company wants to supplement the prostheses with new models. This will help speed up the setup of devices for the user and reduce the time for recognizing gestures. As a result, patients will be more comfortable using prostheses.

We’re going to build a model that, based on OMG data, would recognize what gesture is being performed at the moment. To create the model, we will use data sets and protocols from healthy and targeted pilots. In machine learning terms, the problem comes down to multi-class classification.

To make the task more understandable, let’s look at the technical components of the project.

## Data Collection Protocol

During the data collection procedure, the OMG cuff records the values received from the OMG sensors at a certain frequency. To unify the data collection procedure, a certain protocol is collected.

The protocol is a sequence of gestures that the pilot performs during the data collection procedure.

Each line of the protocol contains a command that the pilot must carry out. The first 5 columns [Thumb, ..., Pinky] indicate whether the corresponding fingers are flexed, and the second 5 columns [Thumb_stretch, ..., Pinky_stretch] indicate whether the corresponding fingers are stretched.

Let's look at the gestures encoded in the protocol:

Neutral/NOGO (all zeros) - neutral position of the hand, the hand is in a relaxed state;
Thumb (Thumb equals 1) - bend of the thumb;
Grab (Thumb, Index, Middle, Ring, Pinky are equal to 1) - grip, hand clenched into a fist;
Open (Thumb_stretch, Index_stretch, Middle_stretch, Ring_stretch, Pinky_stretch are equal to 1) - open palm, fingers straightened;
OK (Thumb, Index are equal to 1) - “Okay” gesture;
Pistol (Middle, Ring, Pinky are equal to 1) - “Pistol” gesture.
The protocol is cyclical; there is a certain subsequence of gestures that is repeated.

At the current step, we have the necessary equipment for collecting data, a given sequence of gestures to be performed by the pilot. Now you can collect data. To make the pilot's task easier, a protocol can be used to collect data in the Motion Match paradigm.

## Motion Match

Regarding the specifics of the task, Motion Match is used as follows:

someone/something commands the pilot to perform a gesture;
the pilot performs the movement according to the given command.
Motor skills projects use a virtual hand that performs gestures according to a previously defined protocol. The pilot repeats gestures behind the virtual hand with some natural delay. This data collection approach allows the pilot to concentrate more on reproducing gestures.

## Problems
1.	Different distribution of values in different datasets (even for the same pilot).
2.	Gesture fulfilling delay
3.	Mistakes in gestures
4.	Pilot's mistakes and confusions 
5.	Unbalanced classes
6.	Feature importance 


## Solutions
1.	Creating a new model to predict a new pilot’s gestures
2.	Shifting the protocol to reduce pilot's delay
3.	We decided to leave outliers because deleting them didn’t improve final result
4.	Working only with ‘good’ datasets
5.	Using smote
6.	Feature selection based on correlation with target

We created three branches with an individual notebook of each team member.

