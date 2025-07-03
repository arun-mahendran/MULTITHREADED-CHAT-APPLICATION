# MULTITHREADED-CHAT-APPLICATION

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: ARUN MAHENDRAN B

*INTERN ID*: CT06DH657

*DOMAIN*: JAVA PROGRAMMING

*DURATION*: 4 WEEKS

*MENTOR*: NEELA SANTHOSH KUMAR

*DESCRIPTION*:

*Objective*:

The objective of this task is to design and implement a basic Client-Server Chat Application in Java that allows multiple clients to communicate with each other in real-time. The goal is to demonstrate core skills in Java network programming, socket handling, and multithreading.


*Project Overview*:

This project consists of two core components:

Server Program (Server.java)

Client Program (Client.java)

The server listens for incoming client connections using Java’s ServerSocket. For every client that connects, the server spawns a new thread to handle its communication. This ensures multiple clients can send and receive messages concurrently—an essential use case of Java multithreading.

Each client, when started, connects to the server using a Socket, enters a username, and then can send messages to all other connected users. The server broadcasts every message to all active clients using output streams.


Key Features:

Console-based, real-time group chat system

Multiple client handling using Java Threads


*Technologies Used*:

Java 

Socket Programming: ServerSocket, Socket

Multithreading: Thread class

I/O Streams: BufferedReader, PrintWriter, InputStreamReader


*Development Environment*:

IDE: Visual Studio Code

Java Version: Java 8+

Executed in terminal via Command Prompt using:

javac to compile,
java to run server/client programs


# OUTPUT

*SERVER*


*CLIENT*
