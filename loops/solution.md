index.html

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

    body {
      color: #ffffff;
      weight: 600;
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
      
      for(position = 1; position <= number_of_blocks; position++) {
        type = getTypeNumber(position);
        block = getHtmlBlock(position, type);
        body += content;
      }
      
      return body;
    }
    
    function openCurrentParagraphAllert(position) {
      paragraph_content = document.getElementById("p-" + position);
      alert(paragraph_content);
    }
    
    function init() {
      number_of_blocks = 5;
      body = getHtmlBody(number_of_blocks);

      document.body.innerHTML = body;
    }
