# Network File System (NFS) - Course Project (CS3.301)

This repository contains the implementation of a **Network File System (NFS)** as part of the **CS3.301 Operating Systems** course project at IIIT Hyderabad. The project demonstrates the design and development of a simplified NFS, focusing on key components and operations to simulate real-world networked file systems.

---

## Overview

The Network File System (NFS) is a distributed system that allows multiple clients to access and manipulate files stored on remote servers. This project simulates the core components and functionalities of an NFS, enabling seamless interaction between clients, naming servers, and storage servers.

### Components

1. **Clients**
   - Act as the interface for users or systems to interact with the NFS.
   - Handle file-related operations such as reading, writing, deleting, and streaming.

2. **Naming Server**
   - Serves as the central directory service, coordinating communication between clients and storage servers.
   - Maps requested files or folders to the appropriate storage server, ensuring efficient access.

3. **Storage Servers**
   - Manage physical storage and retrieval of files and folders.
   - Handle data persistence, ensuring secure and efficient storage.

### Supported Operations

The following operations are implemented in the NFS:

1. **Writing a File/Folder**
   - Supports both synchronous and asynchronous writes.
   - Asynchronous writes optimize client response time for large files.

2. **Reading a File**
   - Allows clients to retrieve file contents from the storage servers.

3. **Deleting a File/Folder**
   - Enables efficient space management by removing unneeded files and folders.

4. **Creating a File/Folder**
   - Supports the creation of new files and directories with proper metadata initialization.

5. **Listing All Files and Folders in a Folder**
   - Provides directory navigation by listing all files and subfolders within a specified directory.

6. **Getting Additional Information**
   - Retrieves metadata such as file size, access rights, and timestamps for files.

7. **Streaming Audio Files**
   - Enables clients to stream audio files directly over the network.
     
8. **Copy a File/Folder**
   - Enables clients to copy any file/folder within the directory.
     
9. **Backing Up Files**
   - The files and folders stored by the client are backed up at multiple storage servers, so that in case one of the storage servers go down the data is preserved and accessible.

---

## Project Specifications

This implementation adheres to the following specifications provided during the course:

1. **Client Interaction**: Clients serve as the primary interface for users to perform file operations.
2. **Centralized Naming Server**: The naming server facilitates directory services by mapping requests to the appropriate storage server.
3. **Data Storage**: Storage servers are responsible for the secure and efficient storage and retrieval of data.
4. **Operations**: All supported operations are designed to simulate real-world NFS functionalities.

### Example Scenarios

- A client writes a large file asynchronously to optimize response time.
- Users navigate directory structures and list contents using the client interface.
- Audio files are streamed directly from the NFS.

---


## 🚀 HOW TO RUN
1. **Run the Naming Server:**  
   ```bash
   make ns
   ```  
2. **Run the Client:**  
   For local server:  
   ```bash
   make cl
   ```  
   For any other setup, just replace `./client <IPOFSERVER>` with your custom command.
3. **Run the SS:**  
   For local server:  
   ```bash
   make ss
   ```  
   For any other setup, just replace `./storage_server <IP OF SERVER> <ROOT_PATH>` with your custom command.
4. **NB:**`rm -rf ./backupfolerforss` to remove the backfolders in each maching in SS 

---

## ✨ BASIC OVERVIEW OF COMMANDS

1. **File Operations (`ls`, `write`, `cat`)**:  
   These commands query the Naming Server (NM) for the IP of the Storage Server (SS), then communicate directly with the SS.

2. **Write Async (`write` command)**:  
   The client specifies a port where it will listen for asynchronous command acknowledgments (ACKs).

3. **Directory and File Management (`mkdir`, `touch`, `rmdir`, `rm`)**:  
   These commands are sent to the NM, which processes them, communicates with the appropriate SS, and sends the output back to the client.

4. **Streaming (`stream` command)**:  
   This command uses `ffplay` to work. Please ensure it is installed on your system.
5. **Backup and Redundancy**: Backup and redundancy mechanisms work in conjunction with caching.

---

## 🛠️ ASSUMPTIONS

1. **Maximum Storage Servers**: Up to 10 servers.  
2. **Maximum Clients**: Unlimited.  
3. **Path Restriction**: All accessible paths must be within the directory where the code is running.  
4. **Buffer Size**: Default buffer size is 2048 bytes; maximum file size is 4096 bytes (can be adjusted in `helper.h`).  
5. **Ports**: Storage Server and Client ports are assigned automatically, allowing multiple instances to run on the same machine.  
6. **Unique Paths**: No SS should have the same root folder as the base accessible directory.  
7. **Backups**: All backups are stored in the `backupforss` folder. This folder should not be used as an accessible path.
8. **Root Folder Protection**: Do not copy or remove root folders.
9. **User Assumptions**: We trust that users will treat the code with love and care. ❤️  

---

## 🤝 Contributors

- Rudra Choudhary
- George Rahul
- Aditya Chandramouli Vadali
- Manoj
