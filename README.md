# PID-controller
C++ implementation of the PID controller for both steering and throttle inputs
---
## Effects of P, I and D
### P (Proportional or Gain)
The main component of the PID controller. Responsible for the car's ability to correct itself based on its error, or how far away it is from the center of the road. A high P results in a more violent correction. Too large a value meant the vehicle tended to oscillate wildly around the center, never able to behave properly damped. Too small a value, and the vehicle would find itself unable to course correct sufficiently in corners.
### I (Integral or Reset
Responsible for accounting of inherent errors in the model. As the vehicle tested did not have any steering bias, the I value was left largely untouched. I did increase this value slightly for the throttle PID controller, to account for the natural slowing of the car over time and in corners.
### D (Derivative or Preact)
Dampens and reduces oscillation caused by P. A balanced parameter tune between P and D would result in a perfectly damped system. This isn't exactly possible, due to twists in the track, but one can get quite close. This, in conjunction with a consistent throttle controller, allowed the vehicle to stay relatively stable during motion.

## Parameter Tuning
The steps I took were as follows:
1. Start with a moderate P value. In this case, I lifted the P value from my previous work in Term 1.
2. The vehicle's behaviour was to oscillate about the center - this was expected. Reduce P until vehicle is able to stay within track confines despite oscillation
3. Increase D (VERY) gradually until oscillation becomes manageable, and vehicle's path becomes smoother.
4. At this point, if vehicle is able to navigate corners effectively, good! If vehicle oveshoots (unable to course correct), increase P and try again.
5. If oscillation becomes more violent as a result, increase D SLOWLY to match.
---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)