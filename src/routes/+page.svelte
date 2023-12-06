<script lang="ts">
    class Button {
        buttonNum: number;
        buttonClicked: boolean;

        constructor(num: number){
            this.buttonNum=num;
            this.buttonClicked=false;
        }
        
    }
    let gridButtons: Button[] = [];

    for (let i = 0; i < 64; i++) {
        gridButtons[i] = new Button(i);
    }

    let bombClicked = false;

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
    console.log(bombNumbers);

    let disabledButtons: number[] = [];
    function leftSide() {

    } 
    function Top() {

    }

    function handleClick(button: Button) {
        gridButtons[button.buttonNum].buttonClicked = true;
        if (bombNumbers.includes(button.buttonNum)) {
            bombClicked = true;
            disabledButtons = bombNumbers.slice();
        }
        switch (button.buttonNum) {
            case 16:
            case 8:
            case 24:
            case 32:
            case 40:
            case 48:

                leftSide()
                break;
            
            case 1:
            case 2:
            case 3:
            case 4:
            case 5:
            case 6:

                Top()
                break;
                
            default:
                break;
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
                <button class="bg-slate-900 text-blue-600 w-16 h-16"
                    on:click={() => handleClick(num)}> 
                    {num.buttonClicked}
                </button>
            {:else}
                <button class="bg-orange-500 text-red-600 w-16 h-16"
                    on:click={() => handleClick(num)}> 
                    {num.buttonClicked}
                </button>
            {/if}
        {/each}
    </div>
</div>

{#if bombClicked}
    <p class="message-overlay">You Lost</p>
{/if}

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
        font-size: 1.5rem;
        z-index: 999;
    }
</style>
<!-- //let num = new B(num); -->