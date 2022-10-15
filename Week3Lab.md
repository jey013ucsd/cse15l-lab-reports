# Search Engine code:

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

![image](https://user-images.githubusercontent.com/114262093/195958392-6272c3e9-7700-469f-ac6e-602a204ca7c2.png)

* By default, the search engine contains no terms
* An if statement checks if nothing is added to the end of the url; if so, the page returns the arraylist of stored terms, which is currently empty, in a String with commas


![image](https://user-images.githubusercontent.com/114262093/195958477-374b7d58-210f-477a-a166-3d09610c7b0f.png)

* When an if statements detects that "/add" is at the end of the url, it takes the isolates the string in the query and adds it to the arraylist of terms to be stored
* "/add?t=apple" adds the word apple to the search engine


![image](https://user-images.githubusercontent.com/114262093/195958736-82ae1098-e7c5-4582-a2e0-0be2ba4d9af5.png)

* After adding several more terms to the searchengine. The arraylist of terms contains the above.


![image](https://user-images.githubusercontent.com/114262093/195959015-c6ec3e0c-a154-499e-9973-05890eda75ce.png)

* An if statement checks if "/search" is at the end of the url. If so, it isolates the String in the query as the term to be searched for
* A for loop goes through each element of the arraylist of stored terms and if they contain the search term, it is added to a new arraylist of "found terms"
* After finishing the loop, the found terms array is returned as a string with commas
* Since apple and pineapple both contain "pple", they are returned as seen above
