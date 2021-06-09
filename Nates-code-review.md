# Review of books.js

## General points ##
> Any Points brought out relating to spacing, formatting or indentation is done so to help prevent linting errors that count crop up later.

> Use of var - The use of var is deprigated and can cause scope problems, keeping to the common practices of ES6 means we should try use const and let in its place.

## Line by Line ##

### 10 - 18 ###

> Line 10
- During line 10, `process.argv` could be assigned to a variable. This will make the code more readable. 

- At the end of this line we also have some logic to confirm that we are not getting undefined, as this is a falsy value we would we could make the use of typeof's boolean output. If `!== 'undefined'` was removed we would get true or false returned, just another way to shorted our code, but if you wanted to be explicit the functionality is not hindered by adding it.

- With the use of the previous points we would be able to shorten the code by changing these two if and else statements on lines 10 - 18 into two ternary statements.

```javascript
if (typeof process.argv[2] !== 'undefined') {
    var search = process.argv[2]
}
else var search = "frog"

if (typeof process.argv[3] !== 'undefined') {
    var human_readable = process.argv[3]
}
    else var human_readable = "y"
```

> Line 13 and 18
- On this line there is an else statement that has no curly braces, for consistancy, moving else onto the end of line 12 and making use of the curly braces again will keep everything structured the same way throughout.


> Line 18
- There is alot of indentation on this line, we could remove this to make sure the formatting is consistent, we have a similar line on line 13 which is different and matching them up with structure things nicely and match up.

```javascript
else var search = "frog"
    else var human_readable = "y"
```
### 20 - 38 ###

> Line 20, 21 and 33
- `"cache." + search + ".json"` is used multiple times, to shorten the code a variable can be used to take its place. Doing this will help our code be 'dry', if we wanted to go further we could also use string interpolation to make this section be more readable and remove the + signs from our code.

```javascript
if (fs.existsSync("cache." + search + ".json")) {
    fs.readFile("cache." + search + ".json", 'utf8' , (err, data) => {
        process_data(data)
    })
}
```

> Line 25
- This is another opportunity to keep our consistency, the else and curly brace can be moved up to line 24 to keep our structure. Following our lint rules we can also add a space between the else and curly to avoid errors.

```javascript
}
else{
```

> Line 20 - 38
- For the sake of readability, a way of refactoring this section could be that we take lines 21 - 23, then we take lines 25 - 37 and put these in their own functions. We could then look to add a ternery statement with the condition of line 20 and use our function names as the two outputs from the ternery, with proper naming this would be a good way to show what the code does in just one line of code (perfect for if someone else is reading your code).

```javascript
if (fs.existsSync("cache." + search + ".json")) {
    fs.readFile("cache." + search + ".json", 'utf8' , (err, data) => {
        process_data(data)
    })
}
else{
    https.get('https://openlibrary.org/search.json?q=' + search, (res) => {
        var data = ''
        res.on('data', function (chunk) {
            data += chunk
        })

        res.on('end', function () {
            fs.writeFile("cache." + search + ".json", data, (err,data) => {
            });
                    process_data(data)
        })
    }) 
}
```

> Line 21 and 33
- On this line you have a callback function that takes an argument of err but there is no error handling being done, it is good practive to use error handling and will go along way if unexpected errors come up later. On line 33 there is no space after err,data and this is also something linting will throw errors for.

```javascript
fs.writeFile("cache." + search + ".json", data, (err,data) => {
            });
```

### 40 - 64 ###

> Line 40
- Another way of declaring a function could be to use an arrow function, ES6 common practice would be to use this. The functionality is there without a doubt never the less.

```javascript
process_data = function(res){}
```

> Line 43
- The variable of t doesnt show what it relates to, perfect opportunity to be more descriptive.

```javascript 
var t = 0, total_ebook = 0, results = {}
```

> Line 45
- Using `++t` instead of `t++` isnt exactly the same thing so make sure its fulfilling its intended purpose, unless it needs to be this way there could be a abit of a clash with ES6 common practices.

```javascript
t = ++t
```

> Line 46
- At the end of this line we could substitute this for total_ebook++ to save some time and make our code shorter.

```javascript
total_ebook = ++total_ebook
```

> Line 49 - 52
- If result.books was assigned on line 43 and everything after the if condition on line 51 was moved to line 45, lines 49 - 52 could be removed.

```javascript
results.books = []
    data.docs.forEach(function(book) {
        if(book.ebook_count_i > 0) results.books.push(book.title + " " + book.key + ": " + book.ebook_count_i)
    });
```

> Line 54
- The use of == could be changed for a `===` strictly equals, this would be the best practice to make sure it 100% equals what you want it to.

```javascript
if(human_readable == "n")
```

> Line 55
- On this line you declare a few things, you have already taken the time to declare results on line 43, you could declare what is on this line also in line 43 to save you having to do it later, this is best prectice to declare what you need in one place if it can be declared in one place.

- Another little hint is that, if the key and value are the same such as t: t you can actually just declare t and it will assign the value of t: t when in an object.

```javascript
results.summary = {total_ebooks: total_ebook, t: t, num_found: data.num_found}
```

> Line 58
- We could move the else up a line and also leave a space after else, again just for abit of consistency and structure.

> Line 62
- This would be a great opportunity for some string interpolation to give the output more structure and stop you having to use alot of quotations.

```javascript
console.log("Total records: " + total_ebook + "/" + t + " out of " + data.num_found)
```

> Line 44, 50 and 59
- When using `data.docs` to access the information needed we can actually make this into a variable and use something discriptive so its easy to see what data or docs it holds, if we changed this into 'books' we could then say `forEach(book)`, this really helps to give anyone looking at your code a really good sense of what is happening even with a quick scan over your code.

```javascript
data.docs.forEach(function(book)
```

```javascript
results.books.forEach(function(overview)
```







