# SD/FAST 

## 1. Introduction
SD/FAST is used to analysis and design of mechanical systems which can be modeled as a set of rigid bodies interconnected by the joints. In general, the system can be influenced by forces, driven by prescibed motions and restricted by constraints.Also, the mechanical system can be fee-flying (like a satellite) or grounded. In addition, different topologies, open loop (tree) or closed-lopp, can be modeled. This package is able to derive the full non-linear equations of motion of the mechanical system (iCub in our case). It would be usefull to implement the result in other studies like stability analysis, trajectory optimization and etc.  

## 2. Requirments and Installation
You will need a windows xp 32 bit machine to run SDFAST. So, first install a virtual machine and then download the .zip file from [here](http://support.ptc.com/support/sdfast/index.html). Then, go through the unziped file to copy the windows version of the application (sdfast_install/install/release/x86_win32/B_2_8/sdfast) and paste it in your own directory. Also, copy the "KEY File" (sdfast_install/install/release/sdfast) in the same directory and replace your lisence code inside the KEY File. The software is ready to use! Go to the next step to prepare the "Description File".

## 3. Description File
A user-written System Description File is used by SD/FAST to generate the dynamic equations of motion. Generally, "Description File" is started with a comment section describing the system. Any line beginning with "#" is treated as a comment and is not processed. The rest of file is a sequence of "paragraphs": a preamble of gllobally applied commands (like vector of gravity or your desired programming language for output files) followed by a paragraph for each body. Fllowing list of parameters should be specified for each link:
   
   * mass
   * Moment of Inertia Matrix
   * Joint type
   * Parent link
   * Vector from center of gravity of the current link toward its upper joint (bodytojoint)
   * Vector from center of gravity of the parent link toward the same joint as above (Inbtojoint)
   * Rotation axis of the joint

An example of body paragraph is like follows:

    body = left_shoulder_1 inb = chest joint = pin
    mass = 0.189000?
    inertia = 0.010000? 0.000000? 0.000000?
    0.000000? 0.010000? 0.000000?
    0.000000? 0.000000? 0.010000?
    bodytojoint = 0.005864?	0.017787? 0.000596?
    inbtojoint = 0.003197? 0.110256? 0.068300?
    pin =  0.000000? 1.000000? 0.000000?
    prescribed = 0? 

**Important Note**: Please note that "bodytojoint" and "Inboardtojoint" should be defined in the referencae frame of "current link" and "parent link", respectively. However, it is assumed that inital orientation of all links frames are alligned with the "World Reference Frame". So, there is no need to use rotation matrix between frames. 

## 4. iCub Description File
In the case of iCub, "Waist" is selected as the "Root Link". Then, six different series of links have been defined as follows:

  * Root to chest (4 links)
  * Chest to left end effector (left palm) (8 links)
  * Chest to right end effector (right palm) (8 links)
  * Chest to left foot (8 links)
  * Chest to right foot (8 links)
  * Chest to head (3 links)
 
Totally, we have 39 bodies(links) and 38 DOF for iCub. Regarding the required information, sdf file of icub is used to get the mass, moment of inertia matrix and joint type. Also, in order to calculate "bodytojoint" and "Inbtojoint" we have used Gazebo functions to get the position of joint and links center of gravity in world referenc frame([see this plugin](https://github.com/epfl-lasa/Icub_Gazebo/tree/master/plugins/sdfastcomputation)). To be more clear about the calculation, please see this [file](). The complete Description File of iCub, named "sdfast_model.sd" is provided [here](). 

In order to write a specific "Description File" for your mechanical system, please refer to the software manual [here](). 

## 5. Run SDFAST
After preparing the Description File, please copy it in the same directory as you copied the executable file of SDFAST and its KEY File. Simply run the executable file and write the name of Description File, with its extention (.sd), in the opened terminal and press Enter and then confirm the name of output files (including "Dynamic File", "Information File" and "Simplified Analysis File"). If there is no error, three output files should be generated successfully.   




