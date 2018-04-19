# Project 8 - Pentesting Live Targets

Time spent: **8** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection 
- GIF Walkthrough:
  - ![1](/gifs/SQLI.gif?raw=true)
  - Steps taken:
  1. Using sqlmap it give us the vulnerability
    ```
    'AND SLEEP(5)=0--'
    ```
  2. Insert this into the url 
  3. The server will execute the SQLI and sleep for 5 seconds.

Vulnerability #2: Session Hijacking
- GIF Walkthrough:
  - ![2](/gifs/Session_hijacking.gif?raw=true)
  - Steps taken:
  1. Using the provided php tool we get the session id.
  2. Now we navigate to the desire  webpage and manually change the session id
     using the chrome console. 
  3. Then we can bypass the login page by changing the path to index.php     


## Green

Vulnerability #1: User Enumeration
- GIF Walkthrough:
  - ![3](/gifs/user_enumeration.gif?raw=true)
  - Steps taken:
  1. First we use the provided known username __jmoroe99__ with a random
     password to see the output message
  2. Notice that the message on a correct username is response in in **bold**
  3. Inspecting the the source file we see that for a incorrect username the
     class name for the css is different.

Vulnerability #2: Cross-Site Scripting 
- GIF Walkthrough:
  - ![4](/gifs/XSS.gif?raw=true)
  - Steps taken:
  1. Go to the Contact and write a review.
  2. As admin login to the site and check the Feedback.
  3. Once the admin loads the feed back the stored xss will execute.


## Red

Vulnerability #1: Cross-Site Request Forgery
- GIF Walkthrough:
  - ![5](/gifs/CSRF.gif?raw=true)
  - Steps taken:
  1. As admin go to **USERS** to see the current users registered on the site.
  2. Loading the [script](/csrf.html) that contains the code which changes the contend of a
     targeted user we change their values.


Vulnerability #2: Insecure Direct Object Reference 
- GIF Walkthrough:
  - ![6](/gifs/IDOR.gif?raw=true)
  - Steps taken:
  1. First login as admin and check for the salesperson with sensitive
     information.
  2. Remember the two ids for those salesperson
  3. Go to the page and open __Find a Salesperson__ and view anyone in the list
  4. Then we can manually change the **?id=x** to the ids we found previously.


## Notes

Describe any challenges encountered while doing the work

