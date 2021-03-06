﻿# Network Analyzer

This little tool can be used to analyze the network traffic between a server and client, when they use the mu online protocol.
It acts as a proxy, which means it waits for incoming connections and connects to the actual server when a connection arrives. It then forwards all the traffic between server and client.
It also decrypts incoming and encrypts outgoing traffic to allow to take a closer look at the messages.
In the future it might also be possible to send custom data packets to server and client - to test their reactions.

By default the analyzer contains packet definitions for packets which are sent between game client and game server, defined by two separate XML files. However, it's not limited to that. For example, you could basically write other packet definitions and use it to analyze the communication between connect server and game client, too. You can also edit these xml files on the fly - as soon as they change, the analyzer reloads them automatically.

## Usage
First, enter your local port, on which the tcp/ip listener should run at. For example, I run it at port 55900.

Next, enter the ip and port of the (game) server you want to connect. For example, I run a game server at 55901 on my local machine (127.x.x.x).

Finally, click on 'Start Proxy' - then the application will listen on port 55900 and is waiting for client connections.

As soon as a client connects, it will be listed in the 'Connection' list and the data packets are shown in the grid. When you click on one packet, it extracts the included information based on the configured packet definition (xml files).
It supports multiple concurrent connections, so when you click on one, you'll see its traffic.
If you want, you can also disconnect a client by the context menu.

## Known limitations

### Encryption
This tool just uses the standard encryption algorithms and keys of Season 6 Episode 3.
If you need a configuration to support algorithm and/or keys of other versions, feel free to create an Issue.

### Complex packet structures
Currently it's not possible to define some more complex packet structures (e.g. arrays of sub-structures) by the xml configuration.
I didn't have the time yet, but I don't think this is hard to extend. If you want to work on it, feel free to create an Issue and send me a pull request.

### Incomplete packet definitions
As it's very time consuming to write the definition for every single packet structure,
I only did it for the most common ones between game server and game client. Feel free to submit pull requests to make them complete :)

## Future Ideas
  * Usage of the packet definitions as reference for packet parsing/sending in the game server - instead of hard coding the packet construction and parsing.