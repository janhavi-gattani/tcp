javac TcpServer.java TcpClient.java
▶️ How to run
1️⃣ Start the server
bash
Copy code
java TcpServer
2️⃣ In a second terminal, start the client
bash
Copy code
java TcpClient
✔ Expected Output
Server terminal
arduino
Copy code
Server listening on port 8080...
Client connected.
Client: Hello from Client!
Hello message sent. Closing server.
Client terminal
pgsql
Copy code
Hello message sent.
Server: Hello from Server!

▶️ How to run
1️⃣ Compile both
javac TcpFileServer.java TcpFileClient.java

2️⃣ Run server
java TcpFileServer

3️⃣ Run client (in another terminal)
java TcpFileClient

📌 Notes

Make sure sample.txt (or any requested file) exists in the server directory.

After transfer, the client will store the file as:

received_sample.txt


If you want, I can also provide:
🔹 README.md
🔹 Multi-client version
🔹 Progress bar for file transfer
🔹 GUI file transfer (Java Swing)

---

## 🚀 Push to GitHub

```bash
# Navigate to project folder
cd /Users/swapnilchidrawar/Desktop/tcp

# Initialize git repository
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit: TCP server/client implementation"

# Create a new repository on GitHub, then add remote
git remote add origin https://github.com/YOUR_USERNAME/tcp.git

# Push to GitHub
git push -u origin main
```

> 💡 Replace `YOUR_USERNAME` with your GitHub username and `tcp` with your repository name.



Think of it as a 4-step story:

✅ STEP 1 — Server starts and waits

You run the server.

It opens port 9090 on your machine.

It says:
"I am waiting for a client who will ask for a file."

It sits there and does nothing until someone connects.

👉 The server is not sending anything yet.
👉 It is simply waiting for a client.

✅ STEP 2 — Client connects and asks for a file

You run the client.

Client connects to the server’s IP (127.0.0.1) on port 9090.

After connecting, the client immediately sends a filename (like "sample.txt").

Client says:
"Hello server, please send me this file: sample.txt"

👉 Client sends filename as a text line.
👉 Server receives that line.

✅ STEP 3 — Server reads the file and sends the file bytes

When server gets the filename:

It checks if that file exists in its folder.

If file exists:

It opens the file.

Reads the file in chunks (1024 bytes each).

Sends those chunks through the network to the client.

Server is now basically saying:
"Here are the bytes of the file you requested…"

👉 This is not text — this is raw bytes of the file.
👉 It keeps sending until the entire file is finished.

✅ STEP 4 — Client receives file bytes and saves them

Once server starts sending file bytes:

Client is reading from the network in chunks.

Every chunk it receives is written into a new file named:

received_sample.txt


Client continues reading until:

server finishes sending and closes connection.

Client is doing:
"I am receiving the bytes… writing them into a new file."

When server closes the socket:

Client knows file transfer is complete.

Client closes its own socket.

Client prints:
"File received successfully."







