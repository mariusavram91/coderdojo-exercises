index.html

The HTML file will be empty, we only need to import our stylesheet and our javascript file.

You need to call the init() function, which add the generated html to the body, onload. It means: once our website loads in the browser the init function will add the html. Nothing else is needed for this exercise in index.html.

    <!DOCTYPE html>
    <html>
      <head>
        <title>Loops exercise</title>
        <link rel="stylesheet" type="text/css" href="style.css">
        <script type="text/javascript" src="app.js"></script>
      </head>
      <body onload="init()">
      </body>
    </html>

style.css

Our stylesheet has: body (for everything we have) sets color to white and makes our font everywhere bold/strong. Then our divs will have margins and padding in pixels, always clockwise being: top, right, bottom, left. Each div will have a solid border with size 1px and color of the border black.

Class for odd position will have a background color different from our even positions.

    body {
      color: #ffffff;
      font-weight: 600;
    }
    
    div {
      margin: 3px 5px 3px 5px;
      padding: 3px 3px 3px 3px;
      border: solid 1px #000000;
    }
    
    .odd {
      background-color: #ff9900;
    }
    
    .even {
      background-color: #6599ff;
    }

app.js

Our javascript file contains many small functions, so we can use them multiple times. For instance we can check if a number or a position is odd or even with isOdd() function any times we want.

To check if a number is odd or not we can have a conditional which check if the number is divisible by two. If the number is disible by two ( number % 2 == 0) that number is even, if number % 2 != 0 (not divisble by 2) the number is odd.

To concatenate strings and variables you can do it by using the '+' sign. Lets say the variable I use is: number, we can add the value of that number to a string with: "My number is " + number

A for loop repeats an action as many times we tell it to do it. 

   for(time = 0; time <= times, time++) {
     do something you want to repeat...
   }

time = 0 is where we want to start.

time++ is like time = time + 1

This starts at 0, does whatever we tell it to execute inside, then, at the end, it adds 1 to that number so time becomes 1. So we have: time = 0 + 1.
Now time is 1, does again what we want to execute, and adds 1 to time so time becomes 2. We have time = 1 + 1.
Now time is 2, executes the code again and adds 1 to time, time is now 3. We have time = 2 + 1.
etc.

This will be repeated until our time variable is equal to our times variable.

Lets say we start with time=1 and our times=3.
time=1, is time <= 3? if this is true add 1 to time, yes time = 1 + 1
time=2, is time <= 3? if this is true add 1, yes time = 2 + 1
time=3, is time <= 3? if this is true add 1, yes time = 3 + 1
time=4, is time <= 3? if this is true add 1, no: 4 > 3, the loops stops now and executes what we have after it.


    function isOdd(number) {
      if(number % 2 == 0) {
        return false;
      } else {
        return true;
      }
    }
    
    function getTypeNumber(number) {
      if(isOdd(number) == true) {
        return "odd";
      } else {
        return "even";
      }
    }
    
    function getHtmlBlock(position, type) {
      div_id = "div-" + position;
      div_class = type;
      click_action = "openCurrentParagraphAlert(" + position + ")";
      p_id = "p-" + position;
      
      block = "<div id='" + div_id + "' class='" + div_class + "' onclick='" + click_action + "'>" +
        "<h1>Title " + position + "</h1>" +
        "<h2>" + type + "</h2>" +
        "<p id='" + p_id + "'>This block position (" + position + ") is " + type + "</p>" +
        "</div>";
      
      return block;
    }
    
    function getHtmlBody(number_of_blocks) {
      body = "";
      
      if(number_of_blocks > 0) {
      
        for(position = 1; position <= number_of_blocks; position++) {
          type = getTypeNumber(position);
          block = getHtmlBlock(position, type);
          body = body + block;      // the same as: body += block
        }
    
      }
      
      return body;
    }
    
    function openCurrentParagraphAlert(position) {
      paragraph_content = document.getElementById("p-" + position).innerHTML;
      alert(paragraph_content);
    
      is_paragraph_odd = isOdd(position);
      if(is_paragraph_odd) {
        alert("This paragraph is in a odd position!");
      }
    }
    
    function init() {
      number_of_blocks = 5;
      body = getHtmlBody(number_of_blocks);

      document.body.innerHTML = body;
    }
