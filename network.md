## TCP/UDP Package:
int -> data Length   
byte -> client/server ID  
byte -> Package Id  
bytes data

min length 6 bytes   
server Id = 1;

## ids:

// 1 - 3 Base  
debugMessage = 1, // Message (string)
serverSettings = 2, // Client Id (byte), Versions (string) devided by ',', Settings (data)
clientSettings = 3, // Versions (string) devided by ',', Settings (data)

// 4 - 9 UDP   
serverStartUDP = 4, // Empty
clientUDPConnection = 5, // Empty
serverUDPConnection = 6, // recived (bool)
clientUDPConnectionStatus = 7, // updConnected (bool)

// 10 - 29 Movement
clientControllMode = 10, // 1 = no control, 2 = Joystick, 3 = AI (int)

clientJoystickMove = 11, // dir norm (Vec2), speed (float)
clientJoystickRotate = 12, // speed (float) pos = right, neg = left   
clientJoystickStop = 13, // Empty

clientMoveAI = 21, // Not defined

// 30 - 39 Cam 
serverCamMode = 31, // int  1 = on 2 = off

// 40 - 49 Chat   
chatMessage = 40, // Not defined


// 50 - 59 Lidar    
clientLidarMode = 50,  // Client requset to start or stop Lidar sensor (int) 1 = on,  2 = off
serverLidarStatus = 51, // Status of the Lidar 1 = on, 2 = off
clientGetSLAMMap = 52, // Empty
servertSLAMMap = 53, // length (int), data (bytes)

clientGetPosition = 54, // Empty
serverPosition = 55, // 

// Lidar Sim 60 - 69  
serverGetSimulatedLidarData = 60,  
clientSimulatedLidarData = 61, // length (int), polarData (float[])

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

### 1.2:
- UDP Support
- Cam Support
- Joystick Support
- Chat Support
- Lidar Support
- LidarSim Support

### 1.3 Client:
- UDP Support
- Cam Support
- Joystick Support
- Chat Support
- Lidar Support
- LidarSim Support
- SLAMMap Support

### 1.3 Server:
- UDP Support
- Cam Support
- Joystick Support
- Chat Support
- Lidar Support
- LidarSim Support
- SLAMMap Support
- SLAMMapSize
- SLAMMapIntervall
