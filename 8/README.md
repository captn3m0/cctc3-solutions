>Mr. Dex (400)
>After sufficiently thrashing the developer who made it possible to hijack 
>Mr. X's session in level-4, we have invited Mr. deX to develop a more secure
>application. However, you know how to crack this one too.. Don't you? :)

>Hint: We need an evidence that someone can successfully hijack 
>Mr. X's session by entering a search term. Please don't submit the solution 
>unless you see at-least an "alert"!!

This was a modification to the earlier XSS problem. But this time there was a
function hello(). Inside the function was a line where the 
server echoed search term after a series of escaping and urlencoding and
commenting off. Their were two instances of such echo by the server.
And it was vulnerable to newline character. So we exploited it by appending 
new character to the required commands to be executed

Input ex: `%0D%0A`

This meant that the input is no longer behind comments and can run as normal JS.
Finally wwe realized that we should somehow stop the JS to execute after the injected 
code, since there was a part below which triggered an error and didn't allow our injection
to run.

Final Injected code that worked - `%0D%0Aalert(1);%0D%0Aalert(1);{%20%0A/*///`

The last few characters commented out the rest of code and did not allow it to trigger errors.