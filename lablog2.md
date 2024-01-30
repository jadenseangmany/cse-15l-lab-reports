# Lab Blog 3
## ChatServer
### ChatServer code:
The following is code for the ChatServer, which takes in a username and a message and outputs and saves the username and message into a webserver.
```
import java.io.IOException;
import java.net.URI;
import java.util.HashMap;
import java.util.Map;

class Handler implements URLHandler {
    // StringBuilder to keep track of chat messages.
    // use instead of int num = 0;
    private StringBuilder chatHistory = new StringBuilder();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return chatHistory.toString().isEmpty() ? "No messages yet!" : chatHistory.toString();
        } else if (url.getPath().equals("/add-message")) {
            // Parse query parameters
            Map<String, String> queryParams = parseQuery(url.getQuery());
            if (queryParams.containsKey("s") && queryParams.containsKey("user")) {
                // Append user, message, and newline to chatHistory
                chatHistory.append(queryParams.get("user"))
                           .append(": ")
                           .append(queryParams.get("s"))
                           .append("\n");
                // Return the entire chat history
                return chatHistory.toString();
            } else {
                return "Invalid query parameters!";
            }
        } else {
            return "404 Not Found!";
        }
    }

    private Map<String, String> parseQuery(String query) {
        Map<String, String> queryParams = new HashMap<>();
        if (query == null || query.isEmpty()) {
            return queryParams;
        }
        // Split the query by '&' and then by '=' to get the key-value pairs.
        for (String param : query.split("&")) {
            String[] pair = param.split("=");
            if (pair.length > 1) {
                queryParams.put(pair[0], pair[1]);
            }
        }
        return queryParams;
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
### Screenshots of /add-message
