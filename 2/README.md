The level title was:

>What the rubbish! (200)

The huge key.txt file they gave us was utterly rubbish. I checked the charset of the file:

``^<=>|_-,;:!?/.'"()@$*\&#%+012345689abdefkpy`

It seems like a hex string but with 3 extra characters: `p, y, k`. Running a script to remove
all special characters (clean.php):

```php
<?php
function clean($string) {
   $string = str_replace(' ', '', $string); // Replaces all spaces with hyphens.
   return preg_replace('/[^A-Za-z0-9]/', '', $string); // Removes special chars.
}
echo clean(file_get_contents('key.txt'));
```

Running

`php clean.php > clean.txt`

Gives us:

`PKey2030115bd38485e8b352f60f2b90f8a932ad0e95`

with the key being the hex portion of the string.