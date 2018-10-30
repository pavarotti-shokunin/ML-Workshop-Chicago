# Vision
Provide the ability to recognize images of ships and then be able to track location and prevent piracy based on known bad routes.

# Datasets
Availabe at https://www.kaggle.com/c/airbus-ship-detection/data
Data set downloaded to S3


# Testing


## needs updating
# Modeling Strategy
- Break up events into types of crime. These are as follows. Each new day will be cross-referenced against a multi-class classification model that predicts each block for it's likelihood of having any of 7 types of criminal activity.
    - Kidnapping
    - Sexual assault 
    - Homocide
    - Motor vehicle theft 
    - Weapons violation
    - Battery
    - Theft
- Link with weather data
- Build a multi-class classifier to predict each type of crime
- Use sequential methods to model the add-on effect; because of what happened earlier in the year, this will happen. Most likely will need to model the sequence in a discrete window of time: One month? One quarter? One year? Will need to experiment here to find the right windo. 

Potentially use multi-class classification to rank blocks in the city based on their likelihood of having a type of crime in the coming day, given the weather forecast and all previously known criminal activity. 


Potentially use LSTM's to capture both the level of complexity and the sequential element. 

Open question: how do we standardize the sequence of both criminal events per block and weather events per block that lead up to the criminal event? Monthly? Yearly? For 2018 maybe just include the sequence of the last month. This means we need to chunk the data into month sequences that go into the LSTM's.

Is it actually better to think about this problem as forecasting? Where we're forecasting the level of crime? Unknown.

# End Goal
The end goal is two-fold. 

Goal 1: Classify the image as SHIP/noSHIP. Print out probability of SHIP once an image is uploaded. 
Goal 2: Recognize the ship in the image if P('SHIP') >= x

