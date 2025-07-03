import java.io.*;
import java.net.*;
import java.util.*;

public class Server {
    private static final int PORT = 12345;
    private static Set<ClientHandler> clientHandlers = new HashSet<>();

    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(PORT);
        System.out.println("Server started.");

        while (true) {
            Socket socket = serverSocket.accept();
            ClientHandler clientHandler = new ClientHandler(socket);
            clientHandlers.add(clientHandler);
            new Thread(clientHandler).start();
        }
    }

    static void broadcast(String message, ClientHandler excludeUser) {
        for (ClientHandler aClient : clientHandlers) {
            if (aClient != excludeUser) {
                aClient.sendMessage(message);
            }
        }
    }

    static void removeClient(ClientHandler clientHandler) {
        clientHandlers.remove(clientHandler);
    }
}

class ClientHandler implements Runnable {
    private Socket socket;
    private PrintWriter out;
    private String userName;

    public ClientHandler(Socket socket) {
        this.socket = socket;
    }

    public void run() {
        try {
            BufferedReader in = new BufferedReader(
                    new InputStreamReader(socket.getInputStream()));
            out = new PrintWriter(socket.getOutputStream(), true);

            out.println("Enter your username:");
            userName = in.readLine();
            System.out.println(userName + " connected.");
            Server.broadcast(userName + " connected.", this);

            String clientMessage;
            while ((clientMessage = in.readLine()) != null) {
                if (clientMessage.equalsIgnoreCase("exit")) {
                    break;
                }
                String formattedMessage = userName + ": " + clientMessage;
                System.out.println(formattedMessage);
                Server.broadcast(formattedMessage, this);
            }

            System.out.println(userName + " disconnected.");
            Server.broadcast(userName + " disconnected.", this);
            Server.removeClient(this);
            socket.close();

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    void sendMessage(String message) {
        out.println(message);
    }
}
