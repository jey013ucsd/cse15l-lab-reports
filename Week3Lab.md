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




# Part 2 Bugs

**Reversed:**
 * Failure inducing input: {1, 2, 3}
 * Symptoms: The method would return an array of all 0's: {0, 0, 0}
 * Bug: The code created a new array to house the reversed elements. However, it assigned the elements of the new array to the input array in reversed order rather than the other way around. It then returned the input array instead of the new array. Since the new array is initialized with all 0's, the input array was populated with the same 0's, resulting in the method returning {0, 0, 0}. To fix this, we need to reassign the values of the new array with the reversed elements of the input array and return the new array.

**Filter:**

 * Failure inducing input: {"one", "two", "three"}
 * Symptoms: The method returns the input array in reverse order: {"three", "two", "one"}
 * Bug: The code adds all the elements of the input arraylist that are strings into a new arraylist that is returned. However, when adding the elements to the new arraylist, the method adds them all to the 0th index: it adds the elements to the front rather than the last, resulting in an arraylist in reverse order. To fix this, we need to add the elements to the end by using .add(s) instead of .add(0, s).
