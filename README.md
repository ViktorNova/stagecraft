# stagecraft
Realtime web app front-end for Non Session Manager (NSM) made with Aiohttp, NexusUI, and Python-OSC

This is still in the conceptualization stages. Check back later! 

##Need to make these first
  - Write module for basic communication with nsmd using python-osc
  - Write simple web framework tying together Aiohttp & NexusUI
  - 
  
##NSM Server Control API
From [here](http://non.tuxfamily.org/nsm/API.html#n:1.2.7.)

The session manager not only manages clients via OSC, but it is itself controlled via OSC messages. The server responds to the following messages. 


All of the following messages will be responded to, at the sender's address, with one of the two following messages: 


````
/reply s:path s:message
/error s:path i:error_code s:message
````

The first parameter of the reply is the path to the message being replied to. The /error reply includes an integer error code (non-zero indicates error). message will be a description of the error.

The possible errors are:

####Fig. 1.7. Responses
Code	| Meaning
--------|-------
ERR_GENERAL	| General Error
ERR_LAUNCH_FAILED	| Launch failed
ERR_NO_SUCH_FILE	| No such file
ERR_NO_SESSION	| No session is open
ERR_UNSAVED_CHANGES	| Unsaved changes would be lost

    
    /nsm/server/add s:executable_name
Adds a client to the current session.


    /nsm/server/save
Saves the current session.


    /nsm/server/open s:project_name
Saves the current session and loads a new session.


    /nsm/server/new s:project_name
Saves the current session and creates a new session.


    /nsm/server/duplicate s:new_project
Saves and closes the current session, makes a copy, and opens it.


    /nsm/server/close
Saves and closes the current session.


    /nsm/server/abort
Closes the current session WITHOUT SAVING


    /nsm/server/quit
Saves and closes the current session and terminates the server.


    /nsm/server/list
Lists available projects. One /reply message will be sent for each existing project.

