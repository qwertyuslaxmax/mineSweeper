<script lang="ts">

    const steps = [
        [
            "Welcome to Minesweeper! Click the buttons below to navigate the tutorial.",
        ],
        [
            "To start, choose your difficulty level. Easy or Normal is recommended to start.",
        ],
        [
            "Once you have chosen a difficulty level, proceed to click on an uncovered tile(any of them).",
            "The results will be as follows:",
            "   The tile changes colors to dark blue (in the original theme).",
            "   The tile is not uncovered",
            "We will go over both scenarios in the next steps!",
        ],
        [
            "Tile Uncovered (scenario 1)",
            "This is the likeliest thing to happen when playing in easier modes.",
            "The tile will have a number ranging from 0-8 on it",
            "   This number represents the number of bombs touching this tile",
            "   (Above, Below, Left, Right, and all of the diagonals",
            "If the number is 0, then it has no bombs touching it and you should reveal all the tiles by it",
        ],
        [
            "Tile not uncovered (scenario 2)",
            "This happens when you click on a bomb within the first 4 clicks",
            "The game grants you another chance to redeem youself since it probably was just luck",
            "We will go over why in later sections.",
        ],
        [
            "As you continue to reveal tiles, you may end up clicking on a bomb (after 4th click).",
            "This results in a loss and the game will prompt yo to retry",
        ],
        [
            "If you uncover all of the tiles without bombs, you will have won the round",
            "Next, we will discuss details. If this is your first time playing, we recommend you get better without advancing (i.e. get a win in normal)",
        ],

        [
            "How to beat the game",
            "If you win, you get a win. If you lose after 4 clicks, you get a loss(that's why)",
            "You can beat the game in any mode but you should do it at least in normal (if you beat it in cakewalk, you will have wasted your time)",
            "   Your win count must be more than twice your loss count",
            "   You must have played at least 8 games",
            "Beware: You will lose progress if you click on change dificulty button",
        ],
        [
            "Mode details",
            "   cakewalk has 5 bombs",
            "   easy has 8 bombs",
            "   normal has 12 bombs",
            "   hard has 18 bombs",
            "   very hard, otherwise known as impossible, has 25 bombs",
        ],
        [
            "Strategy Tips:",
            " ",
            "Starting on the corners, especially in easier modes, is the recommended way to start",
            "Use nomber of bombs to your advantage (i.e. if there may be bomb/s on three squares, look at the number of bombs to determine which 1 or 2 are bombs)",
        ],
        [
            "You completed the tutorial!",
            "Thanks for playing!",
        ],
    ];

    let currentStep = 0;

    function nextStep() {
        if (currentStep < steps.length - 1) {
            currentStep++;
        }
    }

    function previousStep() {
        if (currentStep > 0) {
            currentStep--;
        }
    }
</script>

<div>
    {#each steps[currentStep] as step}
        <h2>{step}</h2>
    {/each}
    <button on:click={previousStep} disabled={currentStep === 0}>Previous</button>
    <button on:click={nextStep} disabled={currentStep === steps.length - 1}>Next</button>
    <button on:click={() => console.log("Start Game!")}>Start Game</button> <!-- Change this to start the game -->
</div>