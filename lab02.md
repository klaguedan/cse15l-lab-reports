# Lab Report 2 - Servers and SSH Keys

Oct. 22, 2023

Hello everyone! This time I will explain how part of particular web server works and verify that my SSH keys on my local computer and UCSD server account work.

---

## 1️⃣ The Web Server

The code for my web server StringServer is [here](#my-server-code).

<center>
<table>
    <tr>
        <td>
            <div align="center">
                <p>This is the web server as it first starts and there is no added path.</p>
                <img src="img/lab02_part1-home.png" width="400px"/>
            </div>
            <br>
            <div align="left">
               <b>Methods Used:</b>
                   <ul>
                       <li><code>handleRequest(URI url)</code>: The argument is <code>localhost:5050</code> and even though there is no added path yet, the default behavior is to send us to the "root" as if we had <code>localhost:5050/</code>.</li>
                   </ul>
               <b>Relevant Fields:</b>
                   <ul>
                       <li><code>myString = ""</code>: This is the default empty value. Nothing has changed yet because the user has not made an add-message request.</li>
                       <li><code>myNum = 1</code>: Also at the default value and has not changed since no request has been made. 1 is ready for the first message.</li>
                   </ul>
           </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                <p>After adding one message.</p>
                <img src="img/lab02_part1-add1.png" width="500px"/>
            </div>
            <div align="left">
                <b>Methods Used:</b>
                    <ul>
                        <li><code>handleRequest(URI url)</code>: The argument here is <code>localhost:5050/add-message?s=I am working on this lab</code></li>
                    </ul>
                <b>Relevant Fields:</b>
                    <ul>
                        <li><code>myString = "1. I am working on this lab\n"</code>: This field has changed because my code notices that the url contains <code>add-message</code> and has a valid query. I format the pre-request value of <code>myNum</code> and the user-queried string <code>"I am working on this lab"</code> to look like a list which is then concatenated to <code>myString</code> and returned to show on the web server.</li>
                        <li><code>myNum = 2</code>: This value has changed because it is increased by one after every request. It is now ready to be used by the second string concatenation.</li>
                    </ul>
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div align="center">
                <p>After adding two messages.</p>
                <img src="img/lab02_part1-add2.png" width="600px"/>
            </div>
            <div align="left">
                <b>Methods Used:</b>
                    <ul>
                        <li><code>handleRequest(URI url)</code>: The argument here is <code>localhost:5050/add-message?s=as I watch my boyfriend play the new spiderman game</code></li>
                    </ul>
                <b>Relevant Fields:</b>
                    <ul>
                        <li><code>myString = "1. I am working on this lab\n2. as I watch my boyfriend play the new spiderman game\n"</code>: The field changes once more to account for the second request.</li>
                        <li><code>myNum = 3</code>: Changes again because it is increased by one after every request. It is now ready to be used by the third request.</li>
                    </ul>
            </div>
        </td>
    </tr>
</table>
</center>


### StringServer.java<a name="my-server-code"></a>


```java
/*
**  The template for this server is from https://github.com/ucsd-cse15l-f23/wavelet
**  and the Handler class and handleRequest() method have been altered by me
**  for the purposes of my Lab Report 2.
*/

import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // Keep track of the editable string and how many
    // requests the site has gotten
    String myString = "";
    int myNum = 1;

    public String handleRequest(URI url) {
        // Home
        if (url.getPath().equals("/")) {
            return "Hello welcome to the StringServer!\n\n" +
            "How to use:\nAppend /add-message?s=<string> " +
            "to the URL to add a message!\n" +
            "(with your own message replacing <string>)\n\n" +
            "What to expect:\n" +
            "The website will show all your messages in an ordered list.";

        // User wants to add a message
        } else if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            
            if (parameters[0].equals("s")) {
                // Concatenate myString with whatever the user put after the =
                // and increment myNum to increase the list number for the next add
                myString += String.format("%d. %s\n", myNum++, parameters[1]);      // Ex: 1. user-string here
                return myString;                                                    //     2. second string here etc
            }
            return "That didn't work oh no - double check your query!";
        } else {
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("You forgot the port number, girl! :(");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```

---


## 2️⃣ SSH

<center>
<table>
  <tr>
    <td>
      <b>Private Key:</b> The path to the private key on my personal computer <br>is <code>/c/Users/katri/.ssh/id_rsa</code>
    </td>
    <td>
      <div align="center">
        <img src="img/lab02_part2-priv_key.png" width="300px"/>
      </div>
    </td>
  </tr>
  
  <tr>
    <td>
      <b>Public Key:</b> The path to the public key on my UCSD server account <br>is <code>/home/linux/ieng6/cs15lfa23/cs15lfa23hl/.ssh/id_rsa.pub</code>
    </td>
    <td>
      <div align="center">
        <img src="img/lab02_part2-pub_key.png" width="300px"/>
      </div>
    </td>
  </tr>
  
  <tr>
    <td>
      <b>Logging in without password! Yay!</b>
    </td>
    <td>
      <div align="center">
        <img src="img/lab02_part2-no_password.png" width="300px"/>
      </div>
    </td>
  </tr>
</table>
</center>


---


## 3️⃣ New Things

Labs 2 and 3 have been big learning opportunities for me. It was my first time securely connecting to a remote server such as ieng6. Related to this, I learned that there is a way to connect to a remote server and skip the password login by using SSH keys. I thought it was very cool that the computer can generate a randomart image.
