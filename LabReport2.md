# StringServer
```
import java.net.URI;
import java.io.IOException;

class Handler implements URLHandler {


    private StringBuilder message = new StringBuilder();
    private int num = 0;

    public String handleRequest(URI url) {
        String query = url.getQuery();
        if (query == null) return "Invalid request";
        
        if (url.getPath().equals("/add-message") && query.startsWith("s=")) {
            num++;
            String string = query.substring(2);
            message.append(num).append(". ").append(string).append("\n");
        }
        return message.toString();
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
# Part 1
![Image](https://i.imgur.com/YRhddNr.png)
> When the server receives a new HTTP request, the ```handle``` method is called in the ```ServerHttpHandler``` class.
> This method then invokes the ```handleRequest``` method from the ```URLHandler``` interface. This method is implemented
> by the ```Handler``` class, which will check the path and query of the URL to determine what to do.

> The argument for the ```handle``` method is ```exchange```. Given this URL, ```https://0-0-0-0-4234-4uum28osdvd6qt5t36be6bpo34.us.
> edusercontent.com/add-message?s=Hello```, the value of ```exchange.getRequestURI()``` is ```/add-message?s=Hello```. This is then
> passed to the ```handleRequest``` method of the Handler instance ```Handler.handleRequest(URI url)``` uses ```url``` as an argument,
> and its value is ```/add-message?s=Hello```. Relevant fields include ```num``` and ```message```. The value of
> message before this url is handled is an empty StringBuilder and the value of ```num``` is 0.

> After the url is handled, the ```message``` field is changed from an empty StringBuilder to ```1. Hello\n```, and ```num```
> is changed from 0 to 1. These values are changed due to how the ```handelRequest``` method is implemented. If the path is
> ```/add-message``` and the query starts with ```s=```, then it appends the message to the message variable, after the num value,
> period, and follows it with a new line. 

![Image](https://i.imgur.com/7GrFhK9.png)
> Similar to before, the ```handle``` method is called in the ```ServerHttpHandler``` class. This method then invokes the
> ```handleRequest``` method from the ```URLHandler``` interface. This method is implemented by the ```Handler``` class,
> which will check the path and query of the URL to determine what to do.

> Similar to above, the argument for the ```handle``` method is ```exchange```. In yhe method ```Handler.handleRequest(URI url)```,
> ```url``` is used as an argument with a value of
> ```https://0-0-0-0-4234-4uum28osdvd6qt5t36be6bpo34.us.edusercontent.com/add-message?s=How%20are%20you```. The ```Handler``` has
> relevant fields of ```num``` and ```message```. The value of the message StringBuilder before this url is handled is ```1. Hello\n```
> and the variable ```num``` has a value of 1.

> After the url is handled, the ```message``` field is changed from ```1. Hello\n``` to ```1. Hello\n 2. How are you ```and ```num```
> is changed from 1 to 2. These values are changed due to how the ```handleRequest``` is implemented. If the path is ```/add-message```
> and the query starts with ```s=```, it appends the num, a period and space, the new message, and a new line to the ```message```
> variable.

# Part 2
## Public and Private Paths
![Image]((https://imgur.com/bhL7o2H.png))
## Logging into Ieng w/o Password
![Image](https://i.imgur.com/do79Vbk.png)

# Part 3
> Before week 2, I didn't know anything about webservers or how they worked. The lab in week 2 taught me how to build and run a simple
> web server that I can interact with.  I also learned about how ports work for servers and why two computers cannot use the same port
> on a server. I also learned about remote connection and how I can connect to a remote machine and run different models that may not
> be as feasible on my computer. 
