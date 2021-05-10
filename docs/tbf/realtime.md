# Real Time Sync

> The real time sync feature is still under development. It is a module for forcing the LD to be updated the data passively when another user updates the sane LD in another computer.

Current process: The system had set up to listen the 6001 channel when you initalise the design studio. On the other hand, some of the main action in the Design Studio also broadcast a message to the channel ask the user update the LD automatically. If you have set up the redis and installed the laravel-echo-server, you can listen to 6001 and everythings should be worked fine.

What's coming next: We can use the same technology to ask the LD system lock some of the component/ pattern/ outcomes/ task if someone is co-editting the LD.

