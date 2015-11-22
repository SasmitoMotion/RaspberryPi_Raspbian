# RaspberryPi_Raspbian
Install Motion Webcam Raspberry Pi


# This Raspberry Pi Webcam Server tutorial will take you through on how to have your very own Webcam that is visible on a webpage.

sudo apt-get update

sudo apt get-upgrade

sudo rpi-update

sudo apt-get install motion

sudo apt-get install libv4l-0

sudo apt-get install uvccapture

dmesg | tail, you should see you camera attached in the output message, if it is connected to your HW

edit /etc/default/motion and set "start_motion_daemon" to yes

edit /etc/motion/motion.conf with the following settings (these are just examples, which work for me. You will need to do optimizations yourself)


note : if you can setting the configuration motion.conf and set up your calibration on your webcam

set "daemon on"

set "minimum_frame_time 5", this can be modified, depending how often you want to take picture

set "pre_capture 2"

set "post_capture 2"

set "output_normal on"

set "quality 100" 

set "ffmpeg_cap_new on"

set "ffmpeg_timelapse 30"

set "ffmpeg_variable_bitrate 2"

set "get_dir /media/webcam/motion"

set "webcam_port 8080"

set "control_port 8081", this matters!!!

set "webcam_localhost off"

set "width 320", this matters!!!

set "height 240", this matters!!!

note that webcam_port, control_port, width, height do matter. Wrong settings can cause the camera not to work.

give /media dir access rights: sudo chmod 777 /media
start motion with sudo /etc/init.d/motion start
check if all is ok with tail -f /var/log/syslog
if you want to stop motion: sudo /etc/init.d/motion stop
check you browser if picture is displayed: http://xx.xx.xx.xx:8080/
controls can be also set here: http://xx.xx.xx.xx:8081/

note : you can see ip webcam motion on the GUI on raspberry pi or in your pc with the google chrome or Internet Explorer


Referrence :
https://www.raspberrypi.org/forums/viewtopic.php?t=18314
http://www.instructables.com/id/Raspberry-Pi-remote-webcam/
http://pimylifeup.com/raspberry-pi-webcam-server/
