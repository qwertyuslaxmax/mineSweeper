<script lang="ts">
    let gridButtons: number[] = [];

    for (let i = 0; i < 64; i++) {
        gridButtons[i] = i;
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

    function handleClick(num: number) {
        if (bombNumbers.includes(num)) {
            bombClicked = true;
            disabledButtons = bombNumbers.slice(); // Disable all bomb buttons
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
                    disabled={disabledButtons.includes(num)}
                >
                </button>
            {:else}
                <button
                    class="text-blue-600 bg-orange-500 w-16 h-16 focus:bg-blue-400 visited:bg-blue-300"
                    on:click={() => handleClick(num)}
                >
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
        z-index: 999; /* Ensure it's on top of everything */
    }

</style>