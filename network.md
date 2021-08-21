## TCP/UDP Package:
int -> data Length   
byte -> client/server ID  
byte -> Package Id  
bytes data

min length 6 bytes   
server Id = 1;

## ids:

// 1 - 3 Base  
debugMessage = 1, 
serverSettings = 2,  
clientSettings = 3,

// 4 - 9 UDP   
serverStartUDP = 4,  
clientUDPConnection = 5,   
serverUDPConnection = 6,   
clientUDPConnectionStatus = 7,

// 10 - 29 Movement
clientControllMode = 10, // int: 1 = no control, 2 = Joystick, 3 = AI   

clientJoystickMove = 11, // dir norm Vec2, speed float   
clientJoystickRotate = 12, // speed float, pos = right, neg = left   
clientJoystickStop = 13, 

clientMoveAI = 21,

// 30 - 39 Cam 
serverCamMode = 31, // int  1 = on 2 = off

// 40 - 49 Chat   
chatMessage = 40,


// 50 - 59 Lidar  
clientLidarMode = 50,  // Client requset to start or stop Lidar sensor int 1 = off, 2 = off  
serverLidarStatus = 51, // Status of the Lidar 1 = on, 2 = off

// Lidar Sim 60 - 69
serverGetimulatedLidarData = 60,
clientSimulatedLidarData = 61,

// LedStripe 70 - 79


## StartUp Procedure
0. Awake  
   clientState = notConnected  
   serverState = notConnected

1. Server Start  
   serverState = Connected  
   server TCP Connection opened  
   server UDP Connection opened

--- Server Online ---

2. ClientConnect (TCP)  
   clientState = Connecting

3. TCP Connected  
   clientState = Connected

4. Server -> Client ServerSettings (TCP)  
   clientId send from server to client
   settings

5.  Server <- Client ClientSettings (TCP)
    settings

## Settings
- string Version

### 1.1:
- UDP Support
- Cam Support
- Joystick Support
- Chat Support
- Lidar Support
