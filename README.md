# SD/FAST 

## 1. Introduction
SD/FAST is used to analysis and design of mechanical systems which can be modeled as a set of rigid bodies interconnected by the joints. In general, the system can be influenced by forces, driven by prescibed motions and restricted by constraints.Also, the mechanical system can be fee-flying (like a satellite) or grounded. In addition, different topologies, open loop (tree) or closed-lopp, can be modeled. This package is able to derive the full non-linear equations of motion of the mechanical system (iCub in our case). It would be usefull to implement the result in other studies like stability analysis, trajectory optimization and etc.  

## 2. Requirments
You will need a windows xp 32 bit machine to run SDFAST. So, first install a virtual machine and then download the .zip file from [here](http://support.ptc.com/support/sdfast/index.html). Then, go through the unziped file to copy the windows version of the application (sdfast_install/install/release/x86_win32/B_2_8/sdfast) and paste it in your own directory. Also, copy the "KEY File" (sdfast_install/install/release/sdfast) in the same directory and replace your lisence code inside the KEY File. The software is ready to use! Go to the next step to prepare the "Description File".

## 3. Description File
The user-written System Description File is used by SD/FAST to generate the dynamic equations of motion. In the case of iCub, "Waist" is selected as the "root link". Then, six different series of links have been defined as follows:
  * Root to chest (4 links)
  * Chest to left end effector (left palm) (8 links)
  * Chest to right end effector (right palm) (8 links)
  * Chest to left foot (8 links)
  * Chest to right foot (8 links)
  * Chest to head (3 links)
 
In order to write a specific "Description File" for your mechanical system, please refer to the software manual (here). Following  
