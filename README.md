# ROS2 Wheel Odometry

Couldn't find any wheel odometry packages for ROS2, so this is a simple one to get you going and expand upon if needed.

# Instructions

Follow this step by step guide to get going, should be fairly straightforward, similar to the Sparkfun Razor IMU 9DOF for ROS2.

1. Buy a rotary encoder of this model:
`600P/R DC 5-24V Photoelectric Incremental Rotary Encoder AB 2-Phases`
Available on eBay for around 10 - 20 USD. 
here for instance: 
https://www.ebay.com/itm/AB-2-Phase-Photoelectric-Incremental-Rotary-Encoder-600p-r-DC-5-24v-Shaft-6mm/352846312078?_trkparms=aid%3D555018%26algo%3DPL.SIM%26ao%3D1%26asc%3D20131003132420%26meid%3Dea062fb2a34143f4981857b03e8fcc0b%26pid%3D100005%26rk%3D1%26rkt%3D12%26mehot%3Dco%26sd%3D371842303935%26itm%3D352846312078%26pmt%3D1%26noa%3D0%26pg%3D2047675&_trksid=p2047675.c100005.m1851

2. You will also need an Arduino to be able to connect to it.

Use this guide for instance to connect it https://www.youtube.com/watch?v=QE4IQlwOgiA
<schematics>

3. After correct connections, you will need to connect to your Arduino and upload the firmware `encoder.ino` from the `firmware` folder. 

4. Looking at the serial monitor in arduino you should now see it working, and while spinning the encoder your numbers will go up and down.

5. Make sure to take the correct measurements of the diameter of your robots wheels to get the correct odometry, this is crucial to get a good reading as the radius times the revolutions is what gives odometry. 
`config/config.yaml` contains a field called `wheel_diameter` change it to your wheel diameter in meters. So if your wheels are 10cm in diameter put in, `0.1`

6. Start ROS2 wheel encoder node
`ros2 run wheel_encoder wheel_encoder _params:=config.yaml`

7. Start rviz and checkout the odometry visualized.
