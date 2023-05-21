<script>
  import {page} from '$app/stores';
  import {goto} from '$app/navigation';
  import NumberInput from '$lib/NumberInput.svelte';

  let multiple = $page.url.searchParams.get('multiple')

  let currentMultiplier = 1;
  let solution;

  function submitSolution(event) {
    if (solution !== multiple * currentMultiplier) {
      currentMultiplier = 1;
      solution = 0;
      return
    }

    if (currentMultiplier === 10) {
      return goto('/simple-multiplication/success')
    }

    currentMultiplier ++;
    solution = 0;
  }
</script>

<h1 class="text-center text-4xl font-bold mb-16">Multiples of {multiple}</h1>

<p class="text-center text-4xl">{multiple} x {currentMultiplier}</p>

<NumberInput bind:value={solution} on:submit={submitSolution}>
  <!-- <p class="mb-2 text-center text-red-500">Sorry, that was wrong...</p> -->
</NumberInput>