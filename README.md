# Punched Cards 

Punched Cards problem from the Google Code Jam 2021 competition.

## OVERVIEW

The problem involves drawing a punched card (like the ones used in computers from some decades ago) using dots, bars, dashes and crosses. The input received contains, first, a parameter T, which indicates the number of punched cards that the program will generate. Then, it contains values for the lengths in rows and columns for each card to be drawn. The cards must all have the top left corner “cut” by drawing it different with only dots. 


## CONTEXT: 

The program first receives a parameter T, indicating the number of times the program must run, drawing a different card in each iteration. After T, the input has T lines containing pairs of numbers that indicate the number of rows R and columns C that a particular card must have.
   

## SOLUTION: 

In general, we can make a loop that creates row by row. The loop would run a number of times equal to the number of rows that we need. Inside the creation of a row, there could be another loop adding sections a number of times equal to the number of columns. However, the first row has to be different in its first block, since the top left corner needs to be “cut”. 

To do this, we initiate a string that contains “. . +” as its value. Then, we add to that string the text “- +” a number of times equal to the number of columns we want minus one. That subtraction is because we already manually created the first column. 

After that, to create every following two rows. We can initiate a primary row (or row_1) string as “. . |”, and another secondary row (or row_2) string as “+ - +”. Then, we iterate a number of columns minus one (as with the first row). Each iteration we add “. |” to row_1 and “- +” to row_2. Then, we just add row_1 first, then row_2. That way we completed that row of the card. 

This process has to be repeated a number of times equal to the number of rows we need. On each of those repetitions, row_1 and row_2 must reset their values to “| . |” for row_1 and “+ - +” respectively, now that the top left corner is no longer an issue. 

It is important to remember that after every row there needs to be a “\n” added to jump to the next line. Otherwise, all rows would just keep writing themselves on the same line. 


## ALTERNATIVE SOLUTIONS: 

Another solution would have been to create the whole initial block on the top left corner, having an initial loop with three rows and then having all following additions with the two-rows method we used. However, that would imply complicating ourselves to use a special function that generates three rows at the same time. The method used here is much less complicated. 
