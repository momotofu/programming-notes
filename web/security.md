### Kinds of attacks
- SQL Injection: https://www.owasp.org/index.php/SQL_Injection
  This becomes a risk when using string interpolation or formating in an SQL query.
  ```
    '); delete from posts; --
  ```
- Cross-site Scripting: https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)
  ```
  <script>
  setTimeout(function() {
      var tt = document.getElementById('content');
      tt.value = "<h2 style='color: #FF6699; font-family: Comic Sans MS'>Spam, spam, spam, spam,<br>Wonderful spam, glorious  spam!</h2>";
      tt.form.submit();
  }, 2500);
  </script>
  ```
  
### TSL in HTTPS
https://en.wikipedia.org/wiki/Transport_Layer_Security
- It keeps the connection private by encrypting everything sent over it. Only the server and browser should be able to read what's being sent.
- It lets the browser authenticate the server. For instance, when a user accesses https://www.udacity.com/, they can be sure that the response they're seeing is really from Udacity's servers and not from an impostor.
- It helps protect the integrity of the data sent over that connection — checking that it has not been (accidentally or deliberately) modified or replaced.
