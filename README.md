# Extended-Kalman-Filter


### Theory
When a variable of interest cannot be measured directly but an indirect measurement is available, Kalman filters are used to estimate it as accurately as possible. They are also used to combine information from numerous sensors in the presence of noise to determine the best estimate of states.<br />

The Kalman filter has two steps are:
1. Prediction Step
2. Correction Step <br />


Using the specified motion model to define the prediction stage of the EKF, we create the main filter loop in the prediction step. For each landmark measurement obtained at a specific timestep (k), there is a corrective step. In this case, the measurement model Jacobians at xk are initially computed, followed by the Kalman Gain, the predicted state, and the covariance corrections.
![image](https://user-images.githubusercontent.com/88196192/175786265-1033cc9a-48f4-4280-aa3b-c9e1f83a45dd.png)
![image](https://user-images.githubusercontent.com/88196192/175786254-18b3d471-7580-4cc0-8553-f9263340e76a.png)



### Results
![image](https://user-images.githubusercontent.com/88196192/175785204-50dedb44-da91-46ba-af55-e19584b36416.png)
![image](https://user-images.githubusercontent.com/88196192/175785219-d269f704-ed04-4a7d-9b43-d9afb517ebb2.png)
