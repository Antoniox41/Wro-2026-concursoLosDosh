Design  
Dimensions  
To determine the dimensions we have taken into account:  
The surface of the wheel is made of rubber so that it has better grip; the dimensions of the wheel are 25 mm wide and about 67 mm long.  
Taking into account that the parking space size is (250 x 200 mm)  
The car dimensions are: (length 199.85 mm, width 162.77 mm, height 30.92 mm, wheelbase 132.73 mm)  
Center of gravity: normally, the center of gravity would be located in the middle of the car, but thanks to the weight of the motor, the center of gravity would be further back than usual.  
Weight: considering that the volume of the car is about 489,353.01 cubic mm, which is 489.35301 cubic centimeters, if we estimate that its density is equal or similar to that of water, we conclude that the car will weigh approximately 500 grams.  
Wheels  
The wheel has dimensions of 2.5 cm wide and 6.7 cm long.  
Materials: the part that will be in contact with the road is made of rubber to increase grip with the ground, and the inner part of the wheel is made of plastic.  
Microcontroller  
We are going to use two Arduino microcontrollers, one for the main program and to control the camera, and the second Arduino will be used to give commands to the sensors.  
Mobility  
Our car will have a column steering system that will help when taking curves and make it easier to avoid obstacles.  
Traction  
We have rear-wheel drive, which has a motor that needs 5 volts; to power the motor we will need a 9-volt battery. The motor has a rear-wheel drive system without a differential, which will make the wheels run at their appropriate speed.  
Apart from all this  
Motor, gearbox, coupling to the axle.   
Steering  
Steering column. This system allows changing the direction of the vehicle in a precise and safe way.  
Power supply  
2 Arduino	Operates internally at 5V
1 microcontroller	Depends on the motor we use
4 distance sensors	5V but can operate at 3.3V
1 motor	5V
1 servo motor	5V
We are going to power all this with a 9-volt battery or a pack of 1.5-volt batteries  
Sensors  
Tachometer: used to measure the rotational speed of the axles  
Accelerometer: a device that measures acceleration  
Gyroscope: used to measure, change, or maintain an object’s orientation in space  
Infrared: used to detect movement and temperature and is used in automation systems  
Ultrasound: uses high-frequency sound waves to detect objects and measure distances  
AI camera: advanced devices that use algorithms to make real-time decisions  
To distinguish blue and orange at high speed you need a color sensor; infrared sensors do not differentiate colors, only contrast. The most reliable option is to use two fast photodiodes with color filters, as it offers low latency and distinguishes blue and orange well even at high speed. In addition, it can be easily implemented with specific components and a clear diagram.  
 
The model we are going to use is VL53L1X: it is a distance sensor based on ToF technology that measures up to ~4 m with high precision, without depending on the color of the object, and communicates via I²C, a serial communication protocol that allows multiple electronic devices to be connected using only two wires: one for data (SDA) and one for clock (SCL).  
 
With a single VL53L1X on each side, the method consists of matching distances L and R using PID. Curves are handled by entering a special “cornering” state when a wall is lost. The Kalman1D smooths the measurements and prevents the PID from oscillating; the car maintains stability at 1 m/s even with walls of 10 cm.  
 
Kalman1D is an algorithmic system used to estimate and predict a system when there is uncertainty about how it will behave.  
 
It predicts the next value based on the previous value and a model (for example, “if it was going at 10 m/s, it should be here now”).  
 
It corrects that prediction using the real measurement (for example, a sensor), but weighs how much it trusts that measurement based on its noise level.  
The final result is a more precise estimate than either of the two separately.  
 
Obstacle management  
 
AI camera with two Arduino boardsQ