## pick and place robot project 

[//]: # (Image References)
[image1]: ./img/img1.jpg
[image2]: ./img/img2.jpg
[image4]: ./img/img3.jpg
[image3]: ./img/img4.jpg
[image5]: ./img/img5.jpg
[image6]: ./img/img6.jpg
[image7]: ./img/img7.png

#### Thanks to udacity , slack members , and whole lot of youtube scientist for helping me out with this project . ... :)

![alt text][image7]

#### 1. Run the forward_kinematics demo and evaluate the kr210.urdf.xacro file to perform kinematic analysis of Kuka KR210 robot and derive its DH parameters.

![alt text][image1]

the above image shows how i comeup with axis plotting and DH parameters . following is the steps which i followed to achive this

##### axis labling

* firslty i defined the z axis for all the revolute joint . z axis is the axis of revolution (i.e) the axis about which the joint rotates
* x0 and y0 is free of choice . just follow the right hand rule for axis definition
* x1 just follows the direction of common normal drawn fro z0 . y0 follows right hand rule
* since z1 and z2 are parallel , x2 has many options . in my case , i made x2 to coincide with the orgin of z1 axis . by this way i was able to make d = 0 
* z2 & z3 are special case . z3 coincides with the orgin of z2 . in this case we cant draw a common normal so r = 0 . draw x3 perpendicular to both z2 and z3 . y3 follows right hand rule 
* z4 ,z5 & z6 follows the same methods . as these joints make the sphirical wrist , most of the time they will fall into special case of zi passing throught zi-1 origin . follow the special case rule which we have seen for z2 and z3 .

##### DH - parameter 

![alt text][image2]

* d - the diatance between the zi-1 and zi origin along zi-1 axis . joint 1,4,6 has d value because they have offset in the origin along zi-1 axis 
* theta - just the joint variable . here it is the angle corresponding to the revolute joint 
* a (or) r  - this is the length of the common normal drawn joint 1 and 2 have r values . other joints mstly fall into the spl case of zi passing through zi-1 origin so no common normal can be drawn between zi & zi-1  
* alpha - angle zi-1 has to rotate ablut xi-1 to math zi . spl cases where zi-1 and zi are parallel . joint 2 and 6 are parallel so they have a value of 0 




#### Decouple Inverse Kinematics problem into Inverse Position Kinematics and inverse Orientation Kinematics; doing so derive the equations to calculate all individual joint angles.

following are the formulas and procedure which i used to obtain the joint angle . i followed double revolute joint method for calculating the joint angles


calculation for theta1 is simple . theta1 = atan2(yc,xc) # where xc , yc  = end effector x , y . 

theta 2 , 3 are explined in this images 

![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]



#### Fill in the IK_server.py file with properly commented python code for calculating Inverse Kinematics based on previously performed Kinematic Analysis. Your code must guide the robot to successfully complete 8/10 pick and place cycles. 

