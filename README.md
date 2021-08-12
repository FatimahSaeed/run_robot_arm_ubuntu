# run_robot_arm_ubuntu

 <div dir="rtl">
خطوات تشغيل ذراع الروبوت https://github.com/smart-methods/arduino_robot_arm على نظام ubuntu
 
 هناك عدة خطوات قبل تجربة تشغيل الذراع لتهيئة بيئة العمل المناسبة لعمل الذراع. في هذه الخطوات تم تجربة الذراع على Gazebo & RViz.
 
 الخطوة الأولى:
 
 أولاً، يجب تجهيز بيئة العمل عن طريق تثبيت Oracle VM VirtualBox على نظام ويندوز 10.

 ثانيًا، يتم تثبيت نظام ubuntu 18.04 داخل virtualBox.

 ثالثًا، تثبيت ROS Melodic على نظام ubuntu.

 
 بعد تنفيذ هذه الخطوات سيكون لدينا نظام ROS مثبت على نظام ubuntu بداخل VirtualBox.

 الأمر التالي سيقوم بتشغيل نظام ROS في Terminal:
 
 `$ roscore`
 
 
الخطوة الثانية: 
 
 * تجهيز بيئة عمل Catkin عبر الأوامر التالية على Terminal:
 
`$ source /opt/ros/melodic/setup.bash
 
$ mkdir -p ~/catkin_ws/src
	
$ cd ~/catkin_ws/
	
$ catkin_make`
 
 ملاحظة قد تحتاج لجلب ملف bash عبر الأمر التالي:

`$ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
	
$ source ~/.bashrc`
 
 الآن لدينا ملف بإسم catkin_ws يمكننا بداخله جلب الملفات اللازمة لذراع الروبوت 
 
 الخطوة الثالثة:
 
 تحميل ملفات ذراع الروبوت على Github:
 
 للقيام بتحميل الملفات يجب تثبيت GitHub  `$ sudo apt install git`
 
 نفتح ملف catkin `$ cd ~/catkin_ws/src` 
 
 لتحميل الملفات داخل الملف  `$ git clone https://github.com/smart-methods/arduino_robot_arm` 
 
 تثبيت الملحقات المطلوبة لتشغيل ذراع الروبوت:
 
` $ cd ~/catkin_ws
	
	$ rosdep install --from-paths src --ignore-src -r -y
	
	$ sudo apt-get install ros-melodic-moveit
	
	$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
	
	$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
	
	$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control`

لتفعيل حزمة الذراع: `$ catkin_make` 
 </div>
