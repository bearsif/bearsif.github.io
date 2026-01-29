---
layout: post
title:  "Lap time calculation tool"
---
This is the second project that I made. It functions in a simple way. First it asks the user for the length of the track, then the average speed round the track and whether the track is: dry, slippery or wet. These factors are used in a calculation function which returns a rough estimate for a lap time.
Obviously this is nowhere near a high standard of simulation but it was useful to learn how different factors and attributes of a track can either slightly effect or completely change a lap time. It helped me learn a lot more about different tracks such as the relationship between the speed and the effects of the conditions of the track.
To improve this I would implement a feature which asks the user how many corners are in the track and add this data to the calculation.

```python
grip_factors = {
    "dry" : 1,
    "slippery" : 1.05,
    "wet" : 1.1
}

def lap_time_predictor(track_length, speed, grip_factor):
    lap_time = round(((float(track_length)/float(speed)) * grip_factor * 3600),3)
   
    return(lap_time)

track_length = input("Enter the length of the track in kilometres : ")
speed = input("Enter the average speed of the car on the lap (km/h): ")
grip_factor = input("Is the track: dry, slippery or wet? ")
grip_factor = (grip_factors[str(grip_factor)])

print("The estimated lap time is " + str(lap_time_predictor(track_length, speed, grip_factor)) + "seconds.")
```
![image](/images/lapcalculator.png)
