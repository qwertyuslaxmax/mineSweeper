<script lang="ts">
    class Button {
        buttonNum: number;
        buttonClicked: boolean;
        constructor(num: number, clicked: boolean){
            this.buttonNum=num;
            this.buttonClicked=clicked;
        }
        
    }
    let gridButtons: Button[] = [];

    for (let i = 0; i < 64; i++) {
        gridButtons[i] = new Button(i, false);
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
    
    function handleClick(button: Button) {
        button.buttonClicked=true;
        bombClicked=false;
        if (bombNumbers.includes(button.buttonNum)) {
            bombClicked = true;
            disabledButtons = bombNumbers.slice();
        }
    }
    
    
</script>

<div class="flex justify-center align-items: center">
    <div class="grid grid-cols-8 gap-2 w-fit">
        {#each gridButtons as num}
            {#if bombClicked}
                <button
                    class="text-blue-600 bg-orange-500 w-16 h-16"
                    on:click={() => handleClick(num)}  
                    disabled={disabledButtons.includes(num.buttonNum)}
                >
                </button>
            {:else}
                {#if num.buttonClicked == true}
                    <button
                        class="text-blue-600 bg-slate-900 w-16 h-16 focus:bg-blue-400"
                        on:click={() => handleClick(num)}
                    >
                    </button>
                {:else}
                    <button
                        class="text-blue-600 bg-orange-500 w-16 h-16 focus:bg-blue-400"
                        on:click={() => handleClick(num)}
                    >
                    </button>
                {/if}
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
//let num = new B(num);