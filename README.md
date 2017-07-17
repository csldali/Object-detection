# bject detection use linemod 


## -----------------------------------------First--------------------------------------------

   github Object-detection repository.




## ----------------------------------------Second--------------------------------------------

   If you install ros by sudo apt-get install ros-indigo-desktop-full, it will be easily .  
       
	catkin_make object_recognition_render
        catkin_make linemod_pose_estimation (you need install "opencv candidate" dependence)



## ----------------------------------------Third---------------------------------------------

    install openni2 package (we use ASUS xtion)
    If you meet ERROR:Failed to open the USB device! you need to go to /lib/udev/rules.d/40-libopenni2-0.rules file,and add the following to a file:
SUBSYSTEM=="usb", ATTR{idProduct}=="0609", ATTR{idVendor}=="1d27", MODE:="0666", OWNER:="root", GROUP:="video"




## ---------------------------------------Finally--------------------------------------------

    Operation!!!
    
         roslaunch openni2_launch openni2.launch depth_registration:=true
         roslaunch linemod_pose_estimation linemod_carmine_detect_node "/home/usename/youworkspace/src/linemod_pose_est/config/data/boxNew_longDistance_linemod_xtion_templates.yml" "/home/usename/youworkspace/src/linemod_pose_est/config/data/boxNew_longDistance_linemod_xtion_renderer_params.yml" "/home/usename/youworkspace/src/linemod_pose_est/config/stl/boxNew.stl" 92 35 1e-5 0.02 0.05 20 10 4
         rostopic echo /object_pose  (you can get object pose w.r.t camera frame)	



Note:: "boxNew_longDistance_linemod_xtion_templates.yml" and "/home/usename/youworkspace/src/linemod_pose_est/config/data/boxNew_longDistance_linemod_xtion_renderer_params.yml" means trained template ,
       this is box template , if you want to get other template , you can use renderer.cpp to train new template , but you need to change some argument in renderer.cpp .
       
