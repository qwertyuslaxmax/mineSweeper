<script lang="ts">
    
    let mode: number;
    let wins = 0;
    let losses = 0;
    let gameBegin: boolean = true;

    function cakeWalk(){
        mode=5;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function easy(){
        mode=8;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function normal(){
        mode=12;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function hard(){
        mode=18;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function veryHard(){
        mode=25;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    
    class Button {
        buttonNum: number;
        buttonClicked: boolean;
        borderBombs: number;

        constructor(num: number){
            this.buttonNum=num;
            this.buttonClicked=false;
            this.borderBombs=0;
        }
        
    }
    let gridButtons: Button[] = [];

    for (let i = 0; i < 64; i++) {
        gridButtons[i] = new Button(i);
    }

    let bombClicked = false;
    let buttonsClicked = 0;
    let gameWon = false;

    function getRandomNumbers() {
        let randomNumbers: number[] = [];

        while (randomNumbers.length < mode) {
            let randomNumber = Math.floor(Math.random() * 64);

            if (!randomNumbers.includes(randomNumber)) {
                randomNumbers.push(randomNumber);
            }
        }

        return randomNumbers;
    }
    let bombNumbers = getRandomNumbers();
    let disabledButtons: number[] = [];

    function handleClick(button: Button) {
        gridButtons[button.buttonNum].buttonClicked = true;
        if(disabledButtons.includes(button.buttonNum)){
            let nothing = 1;
        } else {
            if (bombNumbers.includes(button.buttonNum)) {
                if (buttonsClicked <= 3) {
                    disabledButtons = bombNumbers.slice();
                    replay();
                    bombNumbers = getRandomNumbers();  // Update bombNumbers after replay
                    return;  // Exit the function to avoid further processing
                } else {
                    bombClicked = true;
                    disabledButtons = bombNumbers.slice();
                    losses++;
                    throw "exit";
                }
            }
                buttonsClicked++
                if(buttonsClicked == 64-mode){
                    wins++;
                    if(wins + losses >= 8){
                        if(losses*2 < wins){
                            gameBeaten();
                        } else {
                            gameWon = true;
                        }
                    } else {
                        gameWon = true;
                    }
                }
                disabledButtons.push(button.buttonNum);
                switch (button.buttonNum) {
                    case 16:
                    case 8:
                    case 24:
                    case 32:
                    case 40:
                    case 48:

                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
            
                    case 1:
                    case 2:
                    case 3:
                    case 4:
                    case 5:
                    case 6:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
                
                    case 57:
                    case 58:
                    case 59:
                    case 60:
                    case 61:
                    case 62:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 15:
                    case 23:
                    case 31:
                    case 39:
                    case 47:
                    case 55:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 0:

                        if(bombNumbers.includes(1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
                    case 7:

                        if(bombNumbers.includes(6)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(15)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(14)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 56:
                
                        if(bombNumbers.includes(49)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(48)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(57)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 63:

                        if(bombNumbers.includes(62)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(54)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(55)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    default:
                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
            }
        }
    }
    let gameBeat1 = false;
    let gameBeat2 = false;
    let gameBeat3 = false;
    let gameBeat4 = false;
    let gameBeat5 = false;
    function gameBeaten() {
        switch(mode){
            case 5:
                gameBeat1 = true;
                break;
            case 8:
                gameBeat2 = true;
                break;
            case 12:
                gameBeat3 = true;
                break;
            case 18:
                gameBeat4 = true;
                break;
            case 25:
                gameBeat5 = true;
                break;
        }
    }
    function changeDifficulty() {
        gameBegin = true;
        gameBeat1 = false;
        gameBeat2 = false;
        gameBeat3 = false;
        gameBeat4 = false;
        gameBeat5 = false;
        losses = 0;
        wins = 0;
    }
    function replay() {
        bombNumbers = getRandomNumbers();
        for(let i: number = 0; i < gridButtons.length; i++) {
            gridButtons[i] = new Button(i);
        }
            disabledButtons = [];
            bombClicked = false;
            buttonsClicked = 0;
            gameWon = false;
    }

    let themes: string[] = ["original-theme", "lightBlue-theme", "dark-theme", "blue-theme"];
    let theme: string = "original-theme";
    let unclicked: string = "original-unclicked";
    let clicked: string = "original-clicked";
    let bomb: string = "original-bomb";
    let background: string = "background-theme-original";
    let buttons: string = "button-original";
    let currentIndex = 0;

    function changeTheme(){
        currentIndex++;
        if(currentIndex == 4){
            currentIndex = 0;
        }
        theme = themes[currentIndex];
        sideTheme();
    }
    function sideTheme(){
        switch(theme){
            case "original-theme":
                unclicked = "original-unclicked"
                clicked = "original-clicked"
                bomb = "original-bomb"
                background = "background-theme-original"
                buttons = "button-original"
                break;
            case "lightBlue-theme":
                unclicked = "lightBlue-unclicked"
                clicked = "lightBlue-clicked"
                bomb = "lightBlue-bomb"
                background = "background-theme-lightBlue"
                buttons = "button-lightBlue"
                break;
            case "dark-theme":
                unclicked = "dark-unclicked"
                clicked = "dark-clicked"
                bomb = "dark-bomb"
                background = "background-theme-dark"
                buttons = "button-dark"
                break;
            case "blue-theme":
                unclicked = "blue-unclicked"
                clicked = "blue-clicked"
                bomb = "blue-bomb"
                background = "background-theme-blue"
                buttons = "button-blue"
                break;
        }
    }
</script>
<div class="{background}"> 
    <h1>​</h1>
    <h1 class="flex justify-center align-items: center text-blue-600">Win Loss Ratio</h1>
    <h1 class="flex justify-center align-items: center text-blue-600"> {wins}:{losses} </h1>
    <h1>​</h1>
    <div class="flex justify-center align-items: center">
        <div class="grid grid-cols-8 gap-2 w-fit">
            {#each gridButtons as num}
                {#if bombClicked || gameWon}
                    {#if bombNumbers.includes(num.buttonNum) || num.buttonNum == bombNumbers[num.buttonNum]}
                        <button class="{theme} {bomb}"> 💣 </button>
                    {:else if num.buttonClicked}
                        <button class="{theme} {clicked}"
                            on:click={() => handleClick(num)}> 
                            {num.borderBombs}
                        </button>
                    {:else}
                        <button class="{theme} {unclicked}"> 
                        </button>
                    {/if}
                {:else if num.buttonClicked}
                    <button class="{theme} {clicked} w-16 h-16 max-sm:w-8 max-sm:h-8"
                        on:click={() => handleClick(num)}> 
                        {num.borderBombs}
                    </button>
                {:else}
                    <button class="{theme} {unclicked} w-16 h-16 max-sm:w-8 max-sm:h-8"
                        on:click={() => handleClick(num)}> 
                    </button>
                {/if}
            {/each}
        </div>
    </div>
    <h1>​</h1>


    <button class = "moretop2 {buttons} " on:click={() => changeDifficulty()}>Change Difficulty</button>
    <p class="{background}">i</p>
    <button class = "moretop2 {buttons} " on:click={() => changeTheme()}>Change Theme</button>

    <p class="{background}">i</p>
    <p class="{background}">i</p>
    <p class="{background}">i</p>
    <p class="{background}">i</p>


    {#if bombClicked}
        <p class="message-overlay">You Lost</p>
        <button class="messageButton" on:click={replay}>Retry</button>
    {/if}

    {#if gameWon}
        <p class="message-overlayWin">You Won</p>
        <button class="messageButton" on:click={replay}>Continue Playing(you have not beaten the game yet)</button>
    {/if}

    {#if gameBeat1}
        <p class="message-overlayWin">You Beat the Game in Cakewalk(no exclamation points)</p>
    {/if}

    {#if gameBeat2}
        <p class="message-overlayWin">You Beat the Game in Easy. wee</p>
    {/if}

    {#if gameBeat3}
        <p class="message-overlayWin">You Beat the Game in Normal!</p>
    {/if}

    {#if gameBeat4}
        <p class="message-overlayWin">You Beat the Game in Hard!!!!!!</p>
    {/if}

    {#if gameBeat5}
        <p class="message-overlayWin">You Beat the Game in Very Hard!!!!!!!!!!!!!!!!!!!!!!!!!!!!!</p>
    {/if}

    {#if gameBegin}
        <button class="moretop" on:click={cakeWalk}>Cakewalk</button>
        <button class="top" on:click={easy}>Easy</button>
        <button class="upMid" on:click={normal}>Normal</button>
        <button class="downMid" on:click={hard}>Hard</button>
        <button class="bottom" on:click={veryHard}>Very Hard</button>
    {/if}

    <h1>​</h1>
    <h1>​</h1>
    <h1>​</h1>
    <h1>​</h1>
</div>
<style>
    .button-original {
        background-color: chocolate;
        color:rgb(146, 9, 80);
    }
    .background-theme-original {
        background-color: antiquewhite;
    }
    .original-theme {
        width: 16;
        height: 16;
        max-width: 8;
        max-height: 8;
        border-width: 0px;
        border-color: blue;
    }
    .original-unclicked {
        background-color: rgb(255, 149, 0);
    }
    .original-clicked {
        background-color: rgb(38, 52, 74);
        color: rgb(63, 101, 255)
    }
    .original-bomb {
        background-color: red;
    }
    .button-lightBlue {
        background-color: rgb(31, 11, 142);
        color: yellowgreen;
    }
    .background-theme-lightBlue {
        background-color:rgb(142, 187, 201);
    }
    .lightBlue-theme {
        width: 16;
        height: 16;
        max-width: 8;
        max-height: 8;
        border-width: 1px;
        border-color: rgb(255, 238, 0);
    }
    .lightBlue-unclicked {
        background-color: rgb(7, 162, 205);
    }
    .lightBlue-clicked {
        background-color: rgb(11, 2, 116);
        color: rgb(0, 234, 102)
    }
    .lightBlue-bomb {
        background-color: rgb(146, 9, 80);
    }
    .button-dark {
        background-color: rgb(170, 136, 14);
        color: rgb(82, 18, 12);
    }
    .background-theme-dark {
        background-color: rgb(0, 63, 83);
    }
    .dark-theme {
        width: 16;
        height: 16;
        max-width: 8;
        max-height: 8;
        border-width: 1px;
        border-color: rgb(2, 2, 34);
    }
    .dark-unclicked {
        background-color: rgb(0, 234, 255);
    }
    .dark-clicked {
        background-color: rgb(255, 234, 0);
        color: rgb(0, 0, 0)
    }
    .dark-bomb {
        background-color: rgb(255, 82, 82);
    }
    .button-blue {
        background-color: rgb(36, 83, 152);
        color: yellowgreen;
    }
    .background-theme-blue {
        background-color: rgb(71, 147, 255);
    }
    .blue-theme {
        width: 16;
        height: 16;
        max-width: 8;
        max-height: 8;
        border-width: 1px;
        border-color: rgb(0, 0, 124);
    }
    .blue-unclicked {
        background-color: rgb(104, 111, 207);
    }
    .blue-clicked {
        background-color: rgb(86, 249, 255);
        color: rgb(0, 4, 105)
    }
    .blue-bomb {
        background-color: rgb(0, 137, 84);
    }
    .message-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 3rem;
        z-index: 998;
    }
    .message-overlayWin {
        opacity: 0.8;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgb(20, 7, 196);
        display: flex;
        justify-content: center;
        align-items: center;
        color: darkorange;
        font-size: 3rem;
        z-index: 998;
    }
    .messageButton {
        opacity: 1;
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 25%;
        background: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .moretop {
        opacity: 0.94;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 20%;
        background: aliceblue;
        display: block;
        justify-content: center;
        align-items: center;
        color: blue;
        font-size: 1.5rem;
        z-index: 999;
    }
    .moretop2 {
        position:relative;
        bottom: 10%;
        left: 25%;
        width: 50%;
        height: 10%;
        display: block;
        justify-content: center;
        align-items: center;
        font-size: 1.5rem;
        z-index: 999;
    }
    .top {
        opacity: 0.94;
        position: fixed;
        top: 20%;
        left: 0;
        width: 100%;
        height: 25%;
        background: greenyellow;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .upMid {
        opacity: 0.94;
        position: fixed;
        top: 40%;
        left: 0;
        width: 100%;
        height: 20%;
        background: darkblue;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .downMid {
        position: fixed;
        top: 60%;
        opacity: 0.94;
        left: 0;
        width: 100%;
        height: 20%;
        background: darkred;
        display: block;
        justify-content: center;
        align-items: center;
        color: darkviolet;
        font-size: 1.5rem;
        z-index: 999;
    }
    .bottom {
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        opacity: 0.94;
        height: 20%;
        background: black;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
</style>