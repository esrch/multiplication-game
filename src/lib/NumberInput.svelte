<script>
	import { createEventDispatcher } from 'svelte';

  export let value = 0;
  export let solution;
  let correct = false;
  let incorrect = false;

	const dispatch = createEventDispatcher();

  function addNumber(e) {
    const number = e.target.innerHTML.toString()
    value = Number(value.toString() + number)
  }

  function clear() {
    value = 0;
  }

  function submit() {
    if (value === solution) {
      correct = true;
      setTimeout(() => correct = false, 150);
      dispatch('correct')
    } else {
      incorrect = true;
      setTimeout(() => incorrect = false, 150);
      dispatch('incorrect');
    }

    value = 0;
  }

</script>
<div class="fixed bottom-0 inset-x-0 p-2">
  <slot/>
  <div
    class="w-full h-12 border-2 mb-2 rounded-xl grid place-content-center text-4xl transition duration-150"
    class:bg-green-200={correct}
    class:bg-red-200={incorrect}
  >{value}</div>
  <div class="grid grid-cols-3 gap-2">
    <button on:click={addNumber}>1</button>
    <button on:click={addNumber}>2</button>
    <button on:click={addNumber}>3</button>
    <button on:click={addNumber}>4</button>
    <button on:click={addNumber}>5</button>
    <button on:click={addNumber}>6</button>
    <button on:click={addNumber}>7</button>
    <button on:click={addNumber}>8</button>
    <button on:click={addNumber}>9</button>
    <button on:click={clear}>Clear</button>
    <button on:click={addNumber}>0</button>
    <button on:click={submit}>OK</button>
  </div>
</div>

<style lang="postcss">
button {
  @apply grid place-content-center h-16 bg-gray-100 active:bg-gray-200 rounded-xl text-3xl;
}
</style>