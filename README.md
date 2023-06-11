# dice-casino-game
How to create a Dice Casino Game using python code in a Flask frame

Follow this 3 steps:
1 - Make sure you have the flask frame installed
2 - Create a directory to save the app.py + templates
3 - Running

============================HOW TO CHECK IF YOU HAVE THE FLASK FRAME==============================

write pip list and check in your cmd
Example:

Package      Version
------------ -------
blinker      1.6.2
click        8.1.3
colorama     0.4.6
Flask        2.3.2 ✔️
itsdangerous 2.1.2
Jinja2       3.1.2
MarkupSafe   2.1.3
Werkzeug     2.3.6

===================================================================================================

ABOUT THE CODE LOGIC:

- The player needs to take a total of 7 or 11 with the sum of dices to WIN
- If the player takes a total of 2, 3 or 12 = LOSE.
===================================================================================================

The code inside of the App.py:

 from flask import Flask, render_template, request
 import random

 app = Flask(__name__)

 def roll_dice():
    return random.randint(1, 6)

 @app.route('/')
 def index():
    return render_template('index.html')

 @app.route('/play', methods=['POST'])
 def play():
    player_name = request.form['player_name']
    dice_1 = roll_dice()
    dice_2 = roll_dice()
    total = dice_1 + dice_2
    
    if total == 7 or total == 11:
        result = "Congratulations! You Win!"
    elif total == 2 or total == 3 or total == 12:
        result = "Ohh! You lose!"
    else:
        result = "You need to try again!"
    
    return render_template('result.html', player_name=player_name, dice_1=dice_1, dice_2=dice_2, total=total, result=result)

 if __name__ == '__main__':
    app.run(debug=True)

===================================================================================================

Save in a folder in your desktop
Now, you need to create two folders: 
1 named: "Templates" for the html files
2 named: "Static" for the CSS files
===================================================================================================

In templates we gonna have the follows: Index.html and Result.html
In Static we gonna have: Styles.css and Stylesz.css

===================================================================================================

INDEX:

<!DOCTYPE html>
<html>
<head>
    <title>Prototype Casino</title>
    <link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='styles.css') }}">
</head>
<body>
    <h1>Welcome to the Prototype Dices Casino!</h1>
    <form action="/play" method="post">
        <label for="player_name">Write your name, please:</label>
        <input type="text" id="player_name" name="player_name" required>
        <button type="submit">PLAY</button>
    </form>
</body>
</html>


===================================================================================================

RESULT:

<!DOCTYPE html>
<html>
<head>
    <title>Game Result</title>
    <link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='stylesz.css') }}">
</head>
<body>
    <h1>Game Result</h1>
    <p>Hello, <span class="player-name">{{ player_name }}</span>!</p>
    <p>You got <span class="dice">{{ dice_1 }}</span> and <span class="dice">{{ dice_2 }}</span>, resulting in <span class="points">{{ total }}</span> points!</p>
    <p class="result">{{ result }}</p>
</body>
</html>

===================================================================================================

STYLES:

body {
    background-color: #222;
    color: #fff;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

h1 {
    text-align: center;
    margin-top: 50px;
    font-size: 32px;
}

form {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 50px;
}

label {
    font-size: 18px;
    margin-bottom: 10px;
}

input[type="text"] {
    padding: 10px;
    width: 200px;
    border-radius: 5px;
    border: none;
    margin-bottom: 10px;
}

button[type="submit"] {
    padding: 10px 20px;
    background-color: rgb(14, 174, 0);
    color: #fff;
    border: none;
    border-radius: 5px;
    font-size: 18px;
    cursor: pointer;
}

button[type="submit"]:hover {
    background-color: rgb(250, 189, 5);
}

===================================================================================================
STYLESZ:

body {
    background-color: #222;
    color: #fff;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

h1 {
    text-align: center;
    margin-top: 50px;
    font-size: 32px;
}

.player-name {
    color: #f00;
    font-weight: bold;
}

.dice {
    color: rgb(225, 240, 15);
    font-weight: bold;
}

.points {
    color: #0f0;
    font-weight: bold;
}

.result {
    text-align: center;
    font-size: 24px;
    margin-top: 50px;
}

===================================================================================================


NOW you just need to execute inside of your folder as Open in Terminal

Write Python app.py

Acess  your local host and Voilà!!

Enjoy and share to  help others :)
    
    

