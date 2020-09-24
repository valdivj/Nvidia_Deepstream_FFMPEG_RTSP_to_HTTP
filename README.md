# Nvidia_Deepstream_FFMPEG_RTSP_to_HTTP
 Nvidia Deepstream FFMPEG RTSP to HTTP Streaming
 
 These are the steps I used to Convert a RTSP stream
 produced by a Nvidia Deepstream to a HTTP using FFMpeg
 
 1.Install FFMPEG
 
 $sudo apt update
 $sudo apt install ffmpeg

 2, Make changes to the FFMPEG config file
 
  $sudo nano /etc/ffserver.conf
  
  Curser down to bottom of file and add following
  

<Feed camera1.ffm>
ACL allow localhost
ACL allow "your ip address"
#uncomment if you want an IP range to be able to access the stream
#ACL allow 192.168.0.0 192.168.255.255
</Feed>

<Stream camera1.mjpeg>
Feed camera1.ffm
Format mpjpeg
VideoFrameRate 30
VideoSize 640x360
VideoBitRate 4048
VideoIntraOnly
NoAudio
Strict -1
</Stream>

