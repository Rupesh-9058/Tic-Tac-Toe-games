# Tic-Tac-Toe-games
#this is a general mini project on web developement for practice
#java-script file of this small game
=========================================
let boxes = document.querySelectorAll(".box");
let resetBtn = document.querySelector("#reset-btn");
let newGameBtn = document.querySelector('#new_btn');
let msgContainer = document.querySelector('.msg-container');
let msg = document.querySelector('#msg');

let turnO = true;//playerX, playerY

const winPatterns =[
    [0,1,2],
    [0,3,6],
    [0,4,8],
    [3,4,5],
    [1,4,7],
    [2,4,6],
    [6,7,8],
    [2,5,8]
];

const resetGame = () => {
    turnO = true;
    enableBoxes();
    msgContainer.classList.add("hide");
}

boxes.forEach((box) => {
    box.addEventListener("click", () => {
        console.log("box was clicked");
        if(turnO) { //Player 1
            box.innerText = "O";
            box.style.color = "green";
            turnO = false;
        } else { //Player 2
            box.innerText = "X";
            box.style.color = "red";
            turnO = true;
        }
        box.disabled = true;

        checkWinner();
    });
});

const disableBoxes = () => {
    for(let box of boxes) {
        box.disabled = true;
    }
}
const enableBoxes = () => {
    for(let box of boxes) {
        box.disabled = false;
        box.innerText = "";
    }
}

const showWinner = (winner) => {
    msg.innerText = `Congratulations, winner is ${winner}`;
    msgContainer.classList.remove("hide");
    disableBoxes(); 
};

const checkWinner = () => {
    for(let pattern of winPatterns) {
        let pos1Val = boxes[pattern[0]].innerText;
        let pos2Val = boxes[pattern[1]].innerText;
        let pos3Val = boxes[pattern[2]].innerText;

        if(pos1Val != "" && pos2Val != "" && pos3Val != "") {
            if (pos1Val === pos2Val && pos2Val === pos3Val) {
                console.log("winner",pos1Val);

                showWinner(pos1Val);
            }
        }
    
    }

};

newGameBtn.addEventListener("click", resetGame);
resetBtn.addEventListener("click", resetGame);


//HTML FILE.....................................................//

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic-Tac-Toe Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="msg-container hide">
        <p id="msg">winner</p>
        <button id="new_btn">New Game</button>
    </div>
    <main>
        <h1>Tic Tac Toe</h1>
        <div class="container">
            <div class="game">
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
                <button class="box"></button>
            </div>
        </div>
        <button id="reset-btn">Reset Game</button>
    </main>
    <script src="app.js"></script>
</body>
</html>

//CSS File...........................................................//
\* {
    margin:0;
    padding:0;
}

body {
    background-color: rgb(86, 121, 121);
    text-align: center;

}

.container {
    height: 70vh;
    display: flex;
    justify-content: center;
    align-items: center;

}
    
.game {
    height: 60vmin;
    width: 60vmin;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 1.5vmin;
}

.box {
    height: 18vmin;
    width: 18vmin;
    border-radius: 2rem;
    border: none;
    box-shadow: 0,0 1rem rgba(0,0,0,0.8);
    font-size: 8vmin;
    color: brown;
    background-color: white;
}
#Reset-Game {
    padding: 1rem;
    font-size: 1.25rem;
    background-color: #191913;
    color:white;
    border-radius: 1rem;
    border: none;
}

#new-btn {
    padding: 1rem;
    font-size: 1.25rem;
    background-color:#191913;
    color: white;
    border-radius: 1rem;
    border: none;
}

#msg {
    color: #ffffc7;
    font-size: 5vmin;
}

.msg-container {
    height: 40vmin;
}

.hide {
    display:none;
}

.X{
    color:rgb(27, 153, 27);
}

