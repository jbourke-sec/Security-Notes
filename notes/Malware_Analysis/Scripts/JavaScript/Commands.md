**Execution**
eval: Execute a script block provided as an argument

**Redirects**
window.location = '\<new_url\>'; (variation is location =
'\<new_url\>';)
window.location.href = '\<new_url\>';
window.location.assign('<new_url>');
window.location.replace('<new_url>'); (overwrites
current page in the browser history)
self.location = '\<new_ur\l>';
top.location = '\<new_url\>';
document.location = '\<new_url\>'; (also has its derivatives,
but it is considered obsolete and shouldn't actually be used
nowadays)
There is also another way to redirect the user without using
JS: \<meta http-equiv="refresh"
content="\<num_of_seconds\>;url=\<new_url\>"\>;
\
**External script loading:**
\<script src="\<name\>.js"\>
var script = document.createElement('script');
script.src = something

**Web requests to remote machines:**
The XMLHttpRequest object:
open: A method to create a request
send: A method to send a request
responseText: A property to access the server response fetch method: A relatively new way to send and process HTTP requests standardized in ES6