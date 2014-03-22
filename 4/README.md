>Mr. X (200)
>                                                            
>Someone wants to hijack Mr. X's session...Can you search and alert how?
>Hint: We need an evidence that someone can successfully hijack Mr. X's session by entering a search term.

This was a basic XSS level, with double encodings being used.
The challenge involved a google custom search engine, with the cse.execute function.
The issue was that the server was truncating all <, >, and single quotes from the
request before displaying. The vulnerable code was 

`cse.execute('<input>');`

So the injecting code had to be `'+alert("cool")+'` so as to terminate the single
quote & execute custom js. After lot of attempts we managed to send a singlke
quote as `%27` (urlencoded). So the injecting input was `%27+alert("cool")+%27`
which made the call 

`cse.execute(''+alert("cool")+'');`

and hence raised an alert.