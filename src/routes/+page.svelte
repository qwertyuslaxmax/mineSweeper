<script lang="ts">
    
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

        while (randomNumbers.length < 12) {
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
                    bombClicked = true;
                    disabledButtons = bombNumbers.slice();
                    throw "exit";
                }
                buttonsClicked++
                if(buttonsClicked == 52){
                    gameWon = true;
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
        
</script>
<h1>​</h1>
<h1>​</h1>
<h1>​</h1>
<h1>​</h1>

<div class="flex justify-center align-items: center">
    <div class="grid grid-cols-8 gap-2 w-fit">
        {#each gridButtons as num}
            {#if num.buttonClicked}
                <button class="bg-slate-900 text-blue-600 w-16 h-16 max-sm:w-8 max-sm:h-8"
                    on:click={() => handleClick(num)}> 
                    {num.borderBombs}
                </button>
            {:else}
                <button class="bg-orange-500 text-red-600 w-16 h-16 max-sm:w-8 max-sm:h-8"
                    on:click={() => handleClick(num)}> 
                </button>
            {/if}
        {/each}
    </div>
</div>

{#if bombClicked}
    <p class="message-overlay">You Lost</p>
{/if}

{#if gameWon}
    <p class="message-overlayWin">You Won</p>
{/if}

<h1>​</h1>
<h1>​</h1>
<h1>​</h1>
<h1>​</h1>

<style>
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
        z-index: 999;
    }
    .message-overlayWin {
        opacity: 0.6;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: aliceblue;
        display: flex;
        justify-content: center;
        align-items: center;
        color: darkorange;
        font-size: 3rem;
        z-index: 999;
    }
</style>