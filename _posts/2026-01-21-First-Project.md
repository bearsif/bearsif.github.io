---
layout: post
title:  "Simple lap time comparison tool"
---
This is the first thing

```python
lap_a = []
lap_b = []

print("Lap 1: ")
for x in range(0,3):
    valid = False
    while valid == False:
        sector_time = input("Time for sector: " + str(x+1))
        if sector_time != "":
            valid = True
            lap_a.append(str(sector_time))


print("Lap 2: ")
for x in range(0,3):
    valid = False
    while valid == False:
        sector_time = input("Time for sector: " + str(x+1))
        if sector_time != "":
            valid = True
            lap_b.append(str(sector_time))


deltas = []
for a, b in zip(lap_a, lap_b):
    deltas.append(float(a) - float(b))


total_delta = 0
for x, delta in enumerate(deltas):
    total_delta += delta
    
print("lap A: ") 
print(lap_a)
print("Lap B: ") 
print(lap_b)
print("Deltas: ")  
print(deltas)
print("The delta between lap A and lap B is " + str(total_delta))
```

