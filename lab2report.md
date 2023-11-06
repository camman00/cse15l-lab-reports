# Lab Report 2
##### Author: Cameron Black
## Part 1 - String Server:
### String Server Source Code:

``` Java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
class Handler implements URLHandler {
    private ArrayList<String> elements = new ArrayList<String>();
    public String handleRequest(URI url) {
        if(url.getPath().equals("/add-message")) {
            if(url.getQuery().isEmpty()) {
                return "Invalid Query: Please Try Again!";
            }
            else {
                var splitParams = url.getQuery().split("=");
                if(splitParams[0].intern() != "s") {
                    return "Invalid Query: Please use s to query.";
                }
                else {
                    elements.add("" + splitParams[1]);
                }
            }
        }
        else {
            String build = "";
            int i = 0;
            for(String element : elements) {
                build += (++i) + ". " + element + "\n";
            }
            return build;
        }
        return "";
    }
}
class StringServer {
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
### /add-message Screen Shot #1
<img width="838" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/e9c5c909-358f-4128-ab16-ccbcd9805a3f">

##### Which methods in your code are called?
The code is all wrapped within one function/method named handleRequest which takes a URI as an argument; but I will explain the different sub-routines. Essentially if the query is detected in which the path = s and the query is valid that specific item will be added into an ArrayList using implicit casting (ArrayList is constructed of type String so we will add strings to the arrayList). So the input value will always be of type String which conforms the the ArrayList type. When the user goes back to the other page we iterate over elements and display the correct items. We can do this by deciding / conditional logic on the path which is a URL type. We can use the properties of the path which is a String.
##### How do the values of any relevant fields of the class change from this specific request?
The only value that is mutated upon is the elements ArrayList of type String. We need to append the new String to the list in order to display it / save it later on. We also have to split the URL. To do this we can use basic string operations to obtain are new URL.

### /add-message Screen Shot #2
<img width="691" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/57eae314-101c-46f8-bbbb-fa703cec7053">

##### Which methods in your code are called?
Please reference my answer for screen shot #1. To elaborate even more to display the index effectively we use pre-incrementation or the ++ operator before the int i to increment.
##### How do the values of any relevant fields of the class change from this specific request?
Similar answer to part 1. The string is appended to the ArrayList of type String.

## Part 2 - SSH
SSH Works now for me. Here is the successful login screenshot
* ![image](https://github.com/camman00/cse15l-lab-reports/assets/20690269/cc694161-d81f-4f0a-a0c6-5acf24146796)
* The public key is located here (truncated for security. Did not use ls but I had to cd into the dir and used cat which should be sufficient for this problem): ![image](https://github.com/camman00/cse15l-lab-reports/assets/20690269/6a79b41c-abd3-4852-b9f9-0a3986c6a64f)
* The private key is located here: ![image](https://github.com/camman00/cse15l-lab-reports/assets/20690269/8431ea67-08a3-4799-baeb-a55cbc715d9a)



## Part 3 - What I learned this week
### SSH
I learned that SSH is buggy on my computer. In all seriousness 
I learned a little bit about what SSH is used for. Its a really unique way to remotely access a computer and run a server. I am very excited to see the new applications we will use this in. Hopefully one day we build a full dev box from ground up. More abstract I also learned a neat method String.intern() to compare two strings using binary operators via value.
