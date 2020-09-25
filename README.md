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

# Starting the proccess

1. Start up a Deepstream application that produces a RTSP stream.

2.Open up a second terminal and run.

 $sudo ffserver
 
3. Open up another terminal and run this:

 $ffmpeg -rtsp_transport tcp -i 'rtsp://<youre IP or Localhost>:8554/ds-test' http://<youre IP or   Localhost:8080/camera1.ffm
                                                                                            
 4.Open up VLC or youre favorite player. Choose the play streaming option.
 
   http://<youre IP or Localhost>:8080/camera1.mjpeg
   
  HTTP Stream should start playing

                                                                                            
                                                                                            
                                                                                            

