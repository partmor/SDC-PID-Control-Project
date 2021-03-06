# **CarND: PID Controller**  [![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)
[//]: # (Image References)
[sample_gif]: ./img/pid_sample.gif

The goal of this project is to implement a simple PID controller for the steering actuator of an autonomous vehicle, to safely drive around the circuit in Udacity's [Self-Driving Car simulator](https://github.com/udacity/self-driving-car-sim).

![sample_gif]

## The PID components

+ Proportional gain: it yields a control output that is directly proportional to the ctross track error (CTE). It tends to produce large magnitude corrections that overshoot, causing oscillations around the desired position.

+ Derivative gain: it helps mitigate the overshooting by introducing a control term that is proportional to the temporal derivative of CTE. This means that, when CTE is decreasing, the D term reduces the magnitude of the correction generated by the P term, and viceversa.

+ Integral gain: it deals with the steady-state error, that could be due to systematic bias, for instance. This is accomplished by introducing a factor that is proportional to the sum of CTE over time.

## Hyperparameter Tuning

In this project, the hyperparameters of the controller have been tuned manually in the following order (starting with all parameters set to zero):
+ Increase P parameter until car starts to move rapidly to the cener of the lane (in this situation the vehicle will constantly overshoot and oscilate around the desired trajectory).
+ Increase D parameter until oscilations become very small.
+ Increase I parameter slightly, to correct small parallel shifts.

Finally, the `kp`, `ki`, and `kd` parameters were set to 0.1, 1e-5 and 1.0 respectively. In these conditions, the car managed to drive safely around the whole track. The replay can be seen in this [YouTube link](https://www.youtube.com/watch?v=gRZMi77mv0Q).
