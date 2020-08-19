# TCP_general_framework_linux

			INSTALLATION INSTRUCTIONS
===============================================================================

  Linux Installation Instructions
  ------------------------------------------------------------------------------
  1. Unpack the archive that you downloaded to where you wish to install the program. 
  
  2. Under the folder /accuenergy_tcp and type:
     
     make
     
     to compile and install the software.
  
  3. Chang direction to the build folder by typing " cd build"
     the executable files tcp_server and tcp_client are under this build folder.
  
  4. Run ./tcp_server first and Run ./tcp_client under the build folder.
  
 [Tips]: A demo video of using this program is packed with source code named Demo.mp4
 
 
 
 
 
 
 			SOURCE CODE EXPLAINATION
===============================================================================
After installation the file tree under  /accuenergy_tcp will be like following:

├── build
│   ├── tcp_client
│   └── tcp_server
├── Demo.mp4
├── Makefile
├── msg_frame.h
├── Readme.txt
├── tcp_client.c
└── tcp_server.c

 1. tcp_client.c :
	The source code used for compiling tcp client program.

 2. tcp_server.c:
	The source code used for compiling tcp server program.

 3. msg_frame.h:
	The header used for definding the message frame	
	#define READ_REQ 1
	#define WRTTO_SERV 2
	#define WRTTO_CLIT 3
	#define CHECKTO_CLIT 4
	 
	#define MSG_SIZE 10


	struct msg_frame
	{   
	    uint8_t msg_type;
	    uint8_t client_id;
	    float msg_info[MSG_SIZE];
	};
	
  3.1. msg_type:
	msg_type indicate the purpose of current message, the value can be chosen
  in { READ_REQ = 1, WRTTO_SERV = 2, WRTTO_CLIT = 3, CHECKTO_CLIT = 4}.  
 
  #define READ_REQ 1   :
	This message is sent from client to server, requesting for a array.
	
  #define WRTTO_SERV 2 : 
	This message is sent from client to server, sending back the modified array.
	
  #define WRTTO_CLIT 3 : 
	This message is sent from server to client, answering the READ_REQ of client. 
	
  #define CHECKTO_CLIT 4
 	This message is sent from server to client, sending the array modified back to
  client itself for  confirmation checking.



  3.2. client_id:
	client_id indicate the identity of one client which need entered manually in client.
	
  3.3. msg_info:
	msg_info contain the 10 float numbers array used for communicating between server and client 
	
 4. Makefile :
 	Makefile used for generating the executabe file tcp_server and tcp_client.
