# Katara Turret System
With the newly established dual birdfeeder setup I've just recently added to my yard, I have summoned horrible beasts of gluttony and despair. These horrible monstronsities plague the avian population with their undying and everpresent need to consume. Of course, I am talking about squirrels. Satan's persistant kin shove their whole faces into the feeder for minutes at a time, stealing and departing back to whatever God-forsaken hell hole they crawled out of. Anyone with a single ounce of spritiual knowlegde knows what is now unfortunetly neccessary, a raspberry pi powered turret which uses image recognition to identify the target and then spray these unholy beasts with a cleansing water to deter them from a path of sin.

## Technologies
Camera Control:  
    - OpenCV  
Detector:  
    - YOLOv8n  
Turret  
    - gpiozero, water pump  
Squirrel Library:  
    - https://universe.roboflow.com/warren-wiens-d0d4p/squirrel-detector-1.1?ref=blog.roboflow.com  

## Logic
Camera frame  
     │  
     ▼  
Motion detected? (OpenCV MOG2)  
     │ yes  
     ▼  
YOLOv8n.predict(frame)  
     │  
     ├─ detects "bird" (confidence > 0.6) ──→ save photo, do nothing  
     │  
     └─ detects "squirrel" (confidence > 0.6) ──→ save photo, fire, save photo
     |
     └─ detects nothing, but motion exist , save photo
