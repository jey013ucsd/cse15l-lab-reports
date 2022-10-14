#Search Engine code:

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> terms = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            if(terms.size() == 0) {
                return "No Terms";
            }
            String output = "Terms: " + terms.get(0);
            for(int i = 1; i < terms.size(); i++) {
                output = output + ", " + terms.get(i);
            }
            return output;
        } else if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            terms.add(parameters[1]);
            return parameters[1] + " has been added!";
        } else if (url.getPath().contains("/search")){
            String[] paramters = url.getQuery().split("=");
            String searchterm = paramters[1];
            ArrayList<String> foundterms = new ArrayList<String>();

            for(int i = 0; i < terms.size(); i++) {
                if(terms.get(i).contains(searchterm)) {
                    foundterms.add(terms.get(i));
                }
            }

            if(foundterms.size() > 0) {
                String found = foundterms.get(0);
                for(int i = 1; i < foundterms.size(); i++) {
                    found = found + ", " + foundterms.get(i);
                }
                return found;
            }
            else {
                return "Search Term Not Found";
            }
        }
        else {
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
