<script>
  import {page} from '$app/stores';
  import {goto} from '$app/navigation';
  import NumberInput from '$lib/NumberInput.svelte';

  let multiple = $page.url.searchParams.get('multiple')
  let currentMultiplier = 1;
  
  $: solution = multiple * currentMultiplier

  function onCorrect() {
    if (currentMultiplier === 10) {
      return goto('/simple-multiplication/success')
    }

    currentMultiplier ++;
  }

  function onIncorrect() {
    currentMultiplier = 1;
  }
</script>

<h1 class="text-center text-4xl font-bold mb-16">Multiples of {multiple}</h1>

<p class="text-center text-4xl">{multiple} x {currentMultiplier}</p>

<NumberInput
  bind:solution
  on:correct={onCorrect}
  on:incorrect={onIncorrect}
/>