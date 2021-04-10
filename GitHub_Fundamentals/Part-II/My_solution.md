# Solution to the command line murder in Terminal City

## The investigation carried out by TCPD - Terminal City Police Department led to some clues which was handled by Detective Wasiu

### Below are the steps taken during the investigation. Kindly Note if you aren't familiar with some commands used, check the `clmystery` folder and go through either the `cheatsheet.md` file or `cheatsheet.pdf` file. Good luck

1. Go through the content of the `instructions` file using the `cat` command i.e `cat instructions`. You'd see something like this

   ````````bash
   OOOOOOOOOoooooo,                                            |OOoooooOOOOOS
   OOOOOOOOOOOOOOOOo,                                          |OOOOOOOOOOOOC
   OOOOOOOOOOOOOOOOOO                                         ,|OOOOOOOOOOOOI
   OOOOOOOOOOOOOOOOOO @          THE                          |OOOOOOOOOOOOOI
   OOOOOOOOOOOOOOOOO'@           COMMAND                      OOOOOOOOOOOOOOb
   OOOOOOOOOOOOOOO'a'            LINE                         |OOOOOOOOOOOOOy
   OOOOOOOOOOOOOO''              MURDERS                      aa`OOOOOOOOOOOP
   OOOOOOOOOOOOOOb,..                                          `@aa``OOOOOOOh
   OOOOOOOOOOOOOOOOOOo                                           `@@@aa OOOOo
   OOOOOOOOOOOOOOOOOOO|                                             @@@ OOOOe
   OOOOOOOOOOOOOOOOOOO@                               

   There's been a murder in Terminal City, and TCPD needs your help.

   To figure out whodunit, go to the 'mystery' subdirectory and start working from there.

   You'll want to start by collecting all the clues at the crime scene (the 'crimescene' file).

   ````````

2. To figure out whodunit, go to `mystery` subdirectory
3. The crimescene is the first file to check for first class info. If you want to see inside, there are two ways to do that but I'd recommend the second option

   - Using the cat command: `cat crimescene`, this would display thousands of lines of report and it would be cumbersome going through all to sieve out clues. You'd see something like this

     ```bash
     *******
     Crime Scene Report #689448343843
     ********

     'Of course not,' Alice replied very readily: 'but that's because it
     stays the same year for such a long time together.'

     'Which is just the case with MINE,' said the Hatter.

     Alice felt dreadfully puzzled. The Hatter's remark seemed to have no
     sort of meaning in it, and yet it was certainly English. 'I don't quite
     understand you,' she said, as politely as she could.

     'The Dormouse is asleep again,' said the Hatter, and he poured a little
     ```

   - Using any of the hint files, for example when you run the command `cat hint2` (be sure to reference its path using absolute or relative path) it will show some info on how to use the `grep` command for finding characters in a file, that is, `grep "CLUE" crimescene`. You'd see something like this:

     ```bash
     Try using grep to search for the clues in the crimescene file:

             grep "CLUE" crimescene
     ```

     and this when you run the `grep` command:

     ```bash
     CLUE: Footage from an ATM security camera is blurry but shows that the perpetrator is a tall male, at least 6'.
     CLUE: Found a wallet believed to belong to the killer: no ID, just loose change, and membership cards for AAA, Delta SkyMiles, the local library, and the Museum of Bash History. The cards are totally untraceable and have no name, for some reason.
     CLUE: Questioned the barista at the local coffee shop. He said a woman left right before they heard the shots. The name on her latte was Annabel, she had blond spiky hair and a New Zealand accent.
     ```

4. From the clues, it would be easier starting off with the last clue displayed in the terminal. We need to search for a woman named "Annabel" in the `people` file inside `mystery` folder. Type the command `grep "Annabel" people`
5. You should see four results displayed as a result of step 4. From the clues in step 3, it turns out that the witness is a woman. Something like this:

   ```bash
   Annabel Sun     F       26      Hart Place, line 40
   Oluwasegun Annabel      M       37      Mattapan Street, line 173
   Annabel Church  F       38      Buckingham Place, line 179
   Annabel Fuglsang        M       40      Haley Street, line 176
   ```

6. You now have two potential witnesses and to know who gave the interview, run a command to track the real witness using the street and line number. For `Annabel Sun`, run `head -n 40 streets/Hart_Place | tail -n 1`. It looks at the first 40 lines (head makes it possible) and then print the last line of the 40 lines to the terminal (tail makes it possible). You'd see something like this:

    ```bash
    SEE INTERVIEW #47246024
    ```

    While for `Annabel Church`, run `head -n 179 mystery/streets/Buckingham_Place | tail -n 1`. You'd see something like this:

    ```bash
    SEE INTERVIEW #699607
    ```

7. This is getting interesting as you are getting closer to the killer. Now, `cd` into the `interviews` folder and run the command for both witnesses using their interview ID. For `Annabel Sun`, type `cat interview-47246024`. You should the output below:

    ```bash
    Ms. Sun has brown hair and is not from New Zealand.  Not the witness from the cafe.
    ```

    For `Annabel Church`, type `cat interview-699607`. You should the output below:

   ```bash
    Interviewed Ms. Church at 2:04 pm.  Witness stated that she did not see anyone she could identify as the shooter, that she ran away as soon as the shots were fired.

    However, she reports seeing the car that fled the scene.  Describes it as a blue Honda, with a license plate that starts with "L337" and ends with "9"
    ```
  
8. As you can see, `Annabel Church` is our witness. The only way to apprehend the killer is by searching for the license plate in vehicles file inside the `mystery` subfolder. So, `cd` into `mystery` and run the command `grep -A 5 "L337" vehicles`. This will look for all license plate that has `"L337"` in it and print 5 lines after the first line. The result should look like this:

    ```bash
    License Plate L337QE9
    Make: Honda
    Color: Blue
    Owner: Erika Owens
    Height: 6'5"
    Weight: 220 lbs
    --
    License Plate L337GB9
    Make: Toyota
    Color: Blue
    Owner: Matt Waite
    Height: 6'1"
    Weight: 190 lbs
    --
    ```

    Note that we are looking for the suspect with Blue Honda vehicle whose height is at least 6'. This narrows the name to four persons namely: `Erika Owens`, `Joe Germuska`, `Jeremy Bowers` and `Jacqui Maher`.

9. Recall that the killer is a male from the clue gotten from the ATM security camera, we can search for this names in the people file and filter out the female. Run the command `grep "Erika" people`. You should see the gender specified like this:

    ```bash
    Erika Owens     F       56      Trapelo Street, line 98
    ```

    Repeat the commands for the rest of the suspects and you should be left with two people: `Joe Germuska` and `Jeremy Bowers`

10. So, who is the killer?! Joe or Jeremy? To find out we need to use our last clue which is, you guess it,....the membership cards. It happens that the killer has four membership, let's run the command for Joe to see if he's the one. First `cd` into the `memberships` subfolder and run `cat AAA Delta_SkyMiles Terminal_City_Library Museum_of_Bash_History | grep "Joe Germuska"`. You'd see something like this:

    ```bash
    Joe Germuska
    Joe Germuska
    ```

    Joe has two results printed out which means he has only two of the four memberships. So, he is likely not the killer, Let's run the same command for Jeremy, `cat AAA Delta_SkyMiles Terminal_City_Library Museum_of_Bash_History | grep "Jeremy Bowers"`. You'd see something like this:

    ```bash
    Jeremy Bowers
    Jeremy Bowers
    Jeremy Bowers
    Jeremy Bowers
    ```

    Note that `grep` won't output anything to the terminal if it doesn't find a match. Are you pondering what I'm pondering? Hey Lil Detective, don't jump into conclusion yet, one last check for you.

11. Now, you need to run the following command, `cd` into the `clmystery` folder. Run `cat solution` and you should see an instruction on how to check your answer, like this:

    ```bash
    Checking Your Answer on Mac/Linux:

    Copy and paste the following command, replace John Doe with the suspect's name you want to check, and execute it from inside the main clmystery directory:

    echo "John Doe" | $(command -v md5 || command -v md5sum) | grep -qif /dev/stdin encoded && echo CORRECT\! GREAT WORK, GUMSHOE. || echo SORRY, TRY AGAIN.

    Checking Your Answer on Windows:

    Copy and paste the following command, replace John Doe with the suspect's name you want to check, and execute it from inside the main clmystery directory:

    echo "John Doe" | $(command -v md5 || command -v md5sum)

    This will give you a long code of numbers and letters. Copy and paste the following command, replace My Code with the code you got, and execute it:

    grep -qi "My Code" encoded && echo CORRECT\! GREAT WORK, GUMSHOE. || echo SORRY, TRY AGAIN.
    ```

    Let's run the following command to check if we are worthy to be called a detective. Run `echo "Jeremy Bowers" | $(command -v md5 || command -v md5sum) | grep -qif /dev/stdin encoded && echo CORRECT\! GREAT WORK, GUMSHOE. || echo SORRY, TRY AGAIN.` You see something like this:

    ```bash
    CORRECT! GREAT WORK, GUMSHOE.
    ```

Yay! You just solve the Terminal City Murder Mystery. Congratulations on earning a new badge Detective!.
