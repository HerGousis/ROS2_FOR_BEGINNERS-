# ROS2 για Αρχάριους

1.Αρχικα θα πρεπει να εχουμε Ubuntu 22.04 και την εκδοση ROS2 22.04 κατεβασμενα και συνιστω να κατεβασετε και το Visual Studio Code. 

## 1o Παραδειγμα 
Χειρισμος της χελωνας μεσω του πληκτρολογιου.
 Ανοιγουμε δυο terminal και στο γραφουμε τις εντολες :

1. ros2 run turtlesim turtlesim_node 

2. ros2 run turtlesim turtle_teleop_key

 αντιστοιχα.
 
 Σημειωση: Με  Ctrl+C σταματουν να εκτελουνται οι εντολες 

  <div style="text-align:center;">
    <img src="/1.png" alt="1" width="800">
</div>

## Install colcon

Ανοιγουμε Terminal 

1. sudo apt update

2. sudo apt install python3-colcon-common-extensions

## Autocompletion

1. cd /usr/share/colcon_argcomplete/hook/

2. ls

3. gedit ~/.bashrc  (Ανοιγει το αρχειο bashrc)

και συμπληρωνω αυτο :

4. source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash

και το καλω με 

5. source .bashrc

## Create ROS2 Workspace

1. source ~/.bashrc
2. ls
3. mkdir ros2_ws
4. cd ros2_ws
5. ls
6. mkdir src
7. ls 
8. colcon build
9. ls

(και θα εμφανιστουν 4 φακελοι build install log src)

10. cd install
11. ls

(και βλεπω το setup.bash)

12. cd
13. source ~/ros2_ws/install/setup.bash 

14. gedit ~/.bashrc  

(Ανοιγει το αρχειο bashrc)

και συμπληρωνω αυτο :

15 .source ~/ros2_ws/install/setup.bash

και γραφω στο terminal :

16. source .bashrc

##   Create ROS2 package
1. cd ros2_ws/
2. cd src
3. ls
4. ros2 pkg create my_robot_controller --build-type ament_python --dependencies rclpy

5. ls

(και πρεπει να βγαζει my_robot_conroller)
εμεις εχουμε το Visual Studio  Code

6. code .  (και ανοιγει το περιβαλλον του Visual code με τα αχρεια)

7. my_robot_controller
8. __init__.py
9. resource
10. my_robot_controller
11. test
12. package.xml
13. setup.cfg
14. setup.py

και  μετα 

15. cd ..

παμε εδω 
hercules@hercules:~/ros2_ws$

16. coclon build ( αν βγαζει θεμα γραφουμε τα εξης σε αλλο τερματικο**)
 
17. ls 
18. cd install
19. ls
20. cd ..
21. cd ..
22. pwd


 ** 1.  sudo apt install python3-pip
2. pip3 list
3. pip3 list | grep setuptools (πρεπει να εχω 58.2.0)

Αν δεν την εχω γραφω :
1. pip3 install setuptools==58.2.0
2. pip3 list | grep setuptools (για να επιβεβαιωσω αν εχω τν 58.2.0)

## my_first_node.py
Σε τερματικο [hercules@hercules:~/ros2_ws$]

1. ros2 run my_robot_controller my_first_node

και βλεπω το αποτελεσμα :

<div style="text-align:center;">
    <img src="/2.png" alt="2" width="800">
</div>

## draw_circle.py
Σε τερματικο και στην θεση [ hercules@hercules:~/ros2_ws$]
γραφω :
1. colcon build --symlink-install

=>  σε αλλο τερματικο γραφω :
(ανοιγω την χελωνα )

2. ros2 run turtlesim turtlesim_node


=> και σε αλλο τερματικο γραφω :

3. source .bashrc

4. ros2 run my_robot_controller draw_circle

<div style="text-align:center;">
    <img src="/3.png" alt="3" width="800">
</div>

## Pose_subscriber.py 
Σε τερματικο και στην θεση (hercules@hercules:~/ros2_ws$ )
1. colcon build --install
2. source ~/.bashrc
3. ros2 run my_robot_controller pose_subscriber 

=> και σε αλλο terminal γραφω : (hercules@hercules:~$)
4. ros2 run turtlesim turtlesim_node
=> και σε αλλο terminal γραφω :
5. ros2 run my_robot_controller draw_circle

και βλεπω στο 1ο terminal (pose_subscriber) τα χ και τα y να αλλαζουν συνεχως 

## turtle_controller.py
Σε τερματικο και στην θεση (hercules@hercules:~/ros2_ws$ )
1. colcon build --symlink-install
2. source ~/.bashrc
3. ros2 run my_robot_controller turtle_controller
4. clear
5. cd
6. source .bashrc (αν κανω καποια αλλαγη στον κωδικα )
7. ros2 run my_robot_controller turtle_controller

=>και σε αλλο terminal 
8. ros2 run turtlesim turtlesim_node

=> και σε αλλο terminal γραφω :
9. ros2 run my_robot_controller pose_subscriber

<div style="text-align:center;">
    <img src="/4.png" alt="4" width="800">
</div>