# Simultaneous Localization and Mapping (SLAM)

## Background

SLAM is a relatively new set of algorithms that attempt to define a space while navigating it. This approach typically uses technology like LiDAR in practice.

The concept behind SLAM is surprisingly simple; given a set of measurements and a guess about where the observer is located, form a system of linear constraints and solve them identify least-cost estimates of each unknown parameter for the observer and its landmarks. While a real or correct solution may not exist due to noise, matrix inversion may be used to solve the equation `positions = measurements * landmarks` as `landmarks = measurements^-1 * positions`. 

## Task
In this assignment, a drone was dropped into a forest of trees and tasked with finding and navigating to a target. Measurement and movement both accrued noise over time, but the drone was permitted to "cycle" back to prior positions to reinforce it's positional guesses. Also, the drone's sensor was limited to a certain distance, so trees could appear and disappear from view as the drone moved.

In part 1, the drone moved according to a preset policy and only localization was tested:

![localization](localization.gif)

Then, in part 2, I implemented an iterative path-finding algorithm using a simple search heuristic to navigate towards the target. Scoring criteria included path distance and total number of movements:

![navigation](navigation.gif)
