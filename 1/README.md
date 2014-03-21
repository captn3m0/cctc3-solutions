>The Matrix (200)

The source code of the level web page included the key in base64 (at the bottom of the page):

Opening `view-source:https://cctc-3.cloudapp.net/cctc/level-1/index.php` gets us the
key in base64 as `VHJpbml0eSwgdGhlIGtleSBpcyAzMmVlNTkwYTMyY2ZjMDYxNzc3MzM0MjMwMTY2NDg1MzhkYTY2YzU2`

Converting this to text:

`echo VHJpbml0eSwgdGhlIGtleSBpcyAzMmVlNTkwYTMyY2ZjMDYxNzc3MzM0MjMwMTY2NDg1MzhkYTY2YzU2 |base64 -d`

Gives us: 

`Trinity, the key is 32ee590a32cfc06177733423016648538da66c56`

Which is the answer.