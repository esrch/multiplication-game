<script>
  import {page} from '$app/stores';
  import {goto} from '$app/navigation';
  import NumberInput from '$lib/NumberInput.svelte';

  let multiple = $page.url.searchParams.get('multiple')
  let currentMultiplier = 1;
  let correct = false;
  let incorrect = false;
  
  $: solution = multiple * currentMultiplier

  function onCorrect() {
    if (currentMultiplier === 10) {
      return goto('/success')
    }

    correct = true;
    setTimeout(() => correct = false, 700);

    currentMultiplier ++;
  }

  function onIncorrect() {
    incorrect = true;
    setTimeout(() => incorrect = false, 700)

    currentMultiplier = 1;
  }
</script>

<div class="h-screen transition duration-700"
  class:bg-green-200={correct}
  class:bg-red-200={incorrect}
>
  <h1 class="text-center text-4xl font-bold mb-16">Multiples of {multiple}</h1>
  <p class="text-center text-4xl">{multiple} x {currentMultiplier}</p>
</div>

<NumberInput
  solution={solution}
  on:correct={onCorrect}
  on:incorrect={onIncorrect}
/>