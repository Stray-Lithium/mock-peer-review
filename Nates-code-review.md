# Review of books.js

## General points ##
> Any Points brought out relating to spacing, formatting or indentation is done so to help prevent linting errors that count crop up later.

> Use of var - The use of var is deprigated and can cause scope problems, keeping to the common practices of ES6 means we should try use const and let in its place.

## Line by Line ##

### 10 - 18 ###

> Line 10
- During line 10, process.argv[2] could be changed to have a variable to replace the number. This would mean shortening the code as we could use the variable to replace the if and else statement on line 15 to 18.

- At the end of this line we also have some logic to confirm that we are not getting undefined, as this is a falsy value we would we could make the use of typeof's boolean output. If !== 'undefined' was removed we would get true or false returned, just another way to shorted our code, but if you wanted to be explicit the functionality is not hindered by adding it.

- With the use of the previous points we would be able to shorted the code by changing these two if and else statements on lines 10 - 18 into a turnery statement.

> Line 13 and 18
- On this line there is an else statement that has no curly braces, for consistancy, moving else onto the end of line 12 and making use of the curly braces again will keep everything structured the same way throughout.

> Line 18
- There is alot of indentation on this line, we could remove this to make sure the formatting is consistant, we have a similar line on line 13 which is different and matching them up with structure things nicely and match up.

### 20 - 38 ###

> Line 20, 21 and 33
- "cache." + search + ".json" is used multiple times, to shorten the code a variable can be use to take its place. Doing this will help our code be 'dry', if we wanted to go further we could also use string interpilation to make this section be more readable and remove the + signs from our code.

> Line 25
- This is another oppertunity to keep our consistancy, the else and curly brace can be moved up to line 24 to keep our structure. Following our lint rules we can also add a space between the else and curly to avoid errors.

> Line 20 - 38
- For the sake of readability, a way of refactoring this section could be that we take lines 21 - 23, then we take lines 25 - 37 and put these in their own functions. We could then look to add a turnery statement with the condition of line 20 and use our function names as the two outputs from the turnery, with proper naming this would be a good way to show what the code does in just one line of code (perfect for if someone else is reading your code).

> Line 21 and 33
- On this line you have a callback function that takes an argument of err, this is a perfect oppertunity to add in some error handling, anything you use that has an arguement that you have to use (usually errors or extra conditions) it was made to be utilised and will go along way if unexpected erros some up later. On line 33 there is no space after err,data and this is also something linting will throw errors for.

### 40 - 64 ###

> Line 40
- Another way of declaring a function could be to use an arrow function, ES6 common practice would be to use this. the functionality is there without a doubt never the less.

> Line 43
- The variable of t doesnt show what it relates to, perfect oppertunity to be more discriptive.

> Line 45
- Using ++t instead of t++ isnt exactly the same thing so make sure its fulfilling its intended purpose, unless it needs to be this way there could be a abit of a clash with ES6 common practices.

> Line 46
- At the end of this line we could substitute this for total_ebook++ to save some time and make our code shorter. 

> Line 54
- The use off == could be changed for a === strictly equals, this would be the best practice to make sure it 100% equals what you want it to.

> Line 55
- On this line you declare a few things, you have already taken the time to declare results on line 43, you could declare what is on this line also in line 43 to save you having to do it later as a little time saver.

- Another little hint is that, if the key and value are the same such as t: t you can actually just declare t and it will equal t: t when in an object.

> Line 58
- We could move the else up a line and also leave a space after else, again just for abit of consistancy and structure.

> Line 62
- This would be a great oppertunity for some string interpilation to give the output more structure and stop you having to use alot of quotations.

> Line 44, 50 and 59
- When using data.docs to access the information needed we can actually make this into a variable and use something discriptive so its easy to see what data or docs it holds, if we changed this into 'books' we could then say forEach(book), this really helps to give anyone looking at your code a really good sense of what is happening even with a quick scan over your code.









