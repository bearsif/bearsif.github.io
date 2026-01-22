---
layout: post
title:  "Simple lap time comparison tool"
---
This is the first tool I have made. It works by taking the values of 3 sector times for 2 laps, it then compares the values entered and outputs 3 arrays. One is the first lap sector times, one is the second lap sector times and the last one is the delta between the sector times. Then it outputs an overall delta between the lap times.

I made this in order to build a better of understanding of how small mistakes across a lap can accumulate to a dramatic loss of time.
However, one drawback of this is it assumes that the conditions of the car (tyre deg, fuel load) remain unchanged. Despite this it is still useful to isolate where most of the time is lost

```python

lap_a = []
lap_b = []

print("Lap 1: ")
for x in range(0,3):
    valid = False
    while valid == False:
        sector_time = input("Time for sector " + str(x+1) + ": ")
        if sector_time != "":
            valid = True
            sector_time = round(float(sector_time),3)
            lap_a.append(float(sector_time))


print("Lap 2: ")
for x in range(0,3):
    valid = False
    while valid == False:
        sector_time = input("Time for sector " + str(x+1 + ": "))
        if sector_time != "":
            valid = True
            sector_time = round(float(sector_time),3)
            lap_b.append(str(sector_time))


deltas = []
for a, b in zip(lap_b, lap_a):
    sector_delta = (float(a) - float(b))
    sector_delta = round(float(sector_delta),3)
    deltas.append(sector_delta)


total_delta = 0
for x, delta in enumerate(deltas):
    total_delta += delta
total_delta = round(float(total_delta),3)
    
print("lap A: ") 
print(lap_a)
print("Lap B: ") 
print(lap_b)
print("Deltas: ")  
print(deltas)
print("The delta between lap A and lap B is " + str(total_delta))

```
![image](/images/exampleresult.png)
