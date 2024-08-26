# Kalman

The Kalman Filter is an algorithm that provides estimates of some unknown variables given the measurements observed over time. It's used in systems where you want to track or predict the state of a system (e.g., position and velocity of a moving object) based on noisy sensor data.


The Kalman Filter works in two main steps:
1) Prediction: Estimates the current state and its uncertainty.
2) Update: Corrects the estimate using the new measurement.
The algorithm assumes that the system is linear and that the noise in the system and measurements is Gaussian.

Let:
x_k be the state vector at time k.
u_k be the control input vector at time k.
z_k be the measurement vector at time k.
A be the state transition matrix.
B be the control input matrix.
H be the measurement matrix.
P_k be the error covariance matrix at time k.
Q be the process noise covariance matrix.
R be the measurement noise covariance matrix.
I be the identity matrix.
K_k be the Kalman Gain at time k.

Prediction Step:
1) State Prediction:
x_k|k-1 = A * x_(k-1|k-1) + B * u_k
2) Covariance Prediction:
P_k|k-1 = A * P_(k-1|k-1) * A^T + Q

Update Step:
1) Kalman Gain Calculation:
K_k = P_k|k-1 * H^T * (H * P_k|k-1 * H^T + R)^-1
2) State Update:
x_k|k = x_k|k-1 + K_k * (z_k - H * x_k|k-1)
3) Covariance Update:
P_k|k = (I - K_k * H) * P_k|k-1


Process Overview
1) Initialization: Start with an initial estimate of the state x_0 and covariance P_0.
2) Predict: Use the current state estimate and control input to predict the state at the next time step.
3) Update: Incorporate the new measurement to refine the state estimate.
4) Repeat: Iterate through prediction and update steps for each time step.
