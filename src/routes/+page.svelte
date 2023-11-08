<script lang="ts">
    
    let gridButtons:number[] = []
    for(let i=0;i<64;i++){
        gridButtons[i]=i
    }
    function getRandomNumbers() {
        var randomNumbers:number[] = [];
  
        while (randomNumbers.length < 8) {
            var randomNumber = Math.floor(Math.random() * 64); // Generates a random number between 0 and 63 (inclusive).
    
            if (!randomNumbers.includes(randomNumber)) {
            randomNumbers.push(randomNumber);
            }
        }
        

  return randomNumbers;
  
}
var randomNumbers = getRandomNumbers();
console.log(randomNumbers)
</script>
<div class="flex justify-center">
<div class="grid grid-cols-8 gap-2 w-fit">
    {#each gridButtons as num}
    
    {#if randomNumbers.includes(num)} 
    <button class="text-red-600 bg-blue-500 w-16 h-16">
        {num}
    </button>
    {:else}
    
    <button class="text-blue-600 bg-orange-500 w-16 h-16">
        {num}
    </button>
    {/if}
    {/each}
</div>
</div>
<style>

</style>
