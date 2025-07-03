import java.io.*;
import java.net.*;
import java.util.Scanner;

public class Client {
    private static final String SERVER_ADDRESS = "localhost";
    private static final int SERVER_PORT = 12345;

    public static void main(String[] args) {
        try (
            Socket socket = new Socket(SERVER_ADDRESS, SERVER_PORT);
            BufferedReader in = new BufferedReader(
                    new InputStreamReader(socket.getInputStream()));
            PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
            Scanner scanner = new Scanner(System.in);
        ) {

            System.out.println(in.readLine());  // "Enter your username:"
            String userName = scanner.nextLine();
            out.println(userName);
            System.out.println("Welcome " + userName + "! Type 'exit' to quit.");

            Thread readThread = new Thread(() -> {
                try {
                    String serverMessage;
                    while ((serverMessage = in.readLine()) != null) {
                        System.out.println(serverMessage);
                    }
                } catch (IOException e) {
                }
            });
            readThread.start();

            String input;
            while (scanner.hasNextLine()) {
                input = scanner.nextLine();
                out.println(input);
                if ("exit".equalsIgnoreCase(input)) {
                    break;
                }
            }

        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
