AI Desk Robot (Interactive Smart
Companion)
1. Objective
The objective of this project is to design and develop an AI-powered desk robot capable of:
• 🗣 Communicating with users through voice
• Answering queries in real-time
• 🖥 Displaying responses visually
• 👁 Tracking human presence using a camera
• Physically interacting through head movement
This robot acts as a personal AI assistant and smart learning companion.
2. Project Overview
The system integrates multiple technologies:
• Artificial Intelligence (local processing)
• Computer Vision
• Voice Interaction (STT + TTS)
• Embedded Systems (Raspberry Pi)
• Robotics (Servo-based movement)
It creates a human-like interactive robotic system.
3. Working Principle
1. User gives voice input
2. Microphone captures audio
3. Speech-to-Text converts speech → text
4. AI model processes query locally
5. Response is generated
6. Output:
o 🖥 Displayed on screen
o Spoken via speaker
7. Camera detects user
8. Servo motors adjust head direction
Result: Real-time intelligent + physical interaction
4. Complete Components List
Core System
• Raspberry Pi 5 (8GB)
• AI HAT+ (13 TOPS)
• NVMe SSD + PCIe HAT
Vision System
• Raspberry Pi Camera Module 3
🖥 Display System
• 7-inch Touch Display
Audio Input
• INMP441 I2S Microphone
Audio Output
• MAX98357A I2S Amplifier
• Speaker
Motion System
• MG996R Servo Motors (2x or more)
Power System
• Li-ion Battery Pack
• BMS + Charger
Power Regulation
• Buck Converters (3x)
Cooling
• Heat sink + fan
Structure
• 3D Printed Body / Frame
Misc
• Wires
• Connectors
• Mounts
Total Cost
~$387 (within Hack Club limit)
5. Key Features
• 🗣 Voice interaction system
• Local AI processing (offline capable)
• 👁 Face detection & tracking
• 🖥 Real-time display interface
• Servo-based physical response
• Natural speech output
6. Use Cases
• AI learning assistant
• Smart desk companion
• Educational robotics platform
• Human-robot interaction research
• Voice-controlled AI interface
7. Code (Basic Working Modules)
Speech Recognition (Python)
import speech_recognition as sr
r = sr.Recognizer()
with sr.Microphone() as source:
print("Listening...")
audio = r.listen(source)
try:
text = r.recognize_google(audio)
print("You said:", text)
except:
print("Error")
Text-to-Speech
import pyttsx3
engine = pyttsx3.init()
engine.say("Hello, I am your AI robot")
engine.runAndWait()
Servo Control
import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BCM)
servo_pin = 18
GPIO.setup(servo_pin, GPIO.OUT)
pwm = GPIO.PWM(servo_pin, 50)
pwm.start(0)
def set_angle(angle):
duty = 2 + (angle / 18)
pwm.ChangeDutyCycle(duty)
time.sleep(0.5)
set_angle(90)
pwm.stop()
GPIO.cleanup()
👁 Face Tracking (Basic OpenCV)
import cv2
cam = cv2.VideoCapture(0)
while True:
ret, frame = cam.read()
cv2.imshow("Camera", frame)
if cv2.waitKey(1) == 27:
break
cam.release()
cv2.destroyAllWindows()
8. Circuit Diagram (Explanation)
4
Connections Overview:
Raspberry Pi
• Main controller
Microphone (I2S)
• VCC → 3.3V
• GND → GND
• WS → GPIO19
• SCK → GPIO18
• SD → GPIO21
Amplifier (MAX98357A)
• VIN → 5V
• GND → GND
• LRC → GPIO19
• BCLK → GPIO18
• DIN → GPIO21
Servo Motors
• VCC → 5V
• GND → GND
• Signal → GPIO18 / GPIO23
Camera
• CSI port of Raspberry Pi
🖥 Display
• HDMI / DSI connection
Power System
• Battery → Buck converter → 5V → Raspberry Pi
• Separate supply for servos
9. Future Enhancements
• Emotion detection
• Gesture recognition
• Multi-user recognition
• Advanced AI models
• Mobile app integration
10. Conclusion
This project successfully integrates:
• Artificial Intelligence
• Computer Vision
• Voice Processing
• Robotics
to build a smart, interactive AI desk robot capable of:
• Understanding users
• Responding intelligently
• Physically interacting
It represents a next-generation human-robot interaction system.
