### Post-Redirect-Get or PRG
A client POSTs to a server to create or update a resource; on success, the server replies not with a 200 OK but with a 303 redirect. The redirect causes the client to GET the created or updated resource. One big advantage of Post-Redirect-Get is that as a user, every page you actually see is the result of a GET request, which means you can bookmark it, reload it, and so forth — without ever accidentally resubmitting a form.

For the messageboard server, Post-Redirect-Get means:

1. You go to http://localhost:8000/ in your browser. Your browser sends a GET request to the server, which replies with a 200 OK and a piece of HTML. You see a form for posting comments, and a list of the existing comments. (But at the beginning, there are no comments posted yet.)
2. You write a comment in the form and submit it. Your browser sends it via POST to the server.
3. The server updates the list of comments, adding your comment to the list. Then it replies with a 303 redirect, setting the Location: / header to tell the browser to request the main page via GET.
4. The redirect response causes your browser to go back to the same page you started with, sending a GET request, which replies with a 200 OK and a piece of HTML …
