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
