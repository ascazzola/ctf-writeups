# Awesome Note Keeping 
### 100 Points

## Information

      Challenge link : http://206.189.236.145:9000

      N.B: There is no need to bruteforce anything.

      Flag Format : BDSEC{fl4g_h3r3}


## Steps done

 1. We visited the URL and inspected the HTML, we found the comment: "<!-- Hi Seli, I have created this awesome note keeping web app today. I have saved a backup file index.php.bak for you. Download it and check it out.  →"
 2. We Downloaded the referenced file ``index.php.bak`` simply going to the link
 3. The file contains all the ``index`` code. The page allows the user to create notes and reads note. If the user tries to create a note and already exists. The content it's displayed with a message, and has the intent to does not allow the users to read a note called ``flag`` filtering that word in this way ``str_replace("flag", "", $_POST["note_title"]);``. two times:
    - The first one before check if the note already exists
    - The second one before open the file
 4. We tried to create a note with title ``flflagag``was sucessfully created
 5. We tried to create a note called ``flfl``flag``agag`` in order to bypass the first  ``str_replace`` after it was bypassed the note ``flflagag``exist because we created it, and after the second ``str_replace``the note called ``flag`` it's opened
 6. We get the note ``BDSEC{tHe_n0t3_K33p1n6_4W350M3_N5}``



