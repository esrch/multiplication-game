<script>
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

  export let value = 0;

  function addNumber(e) {
    const number = e.target.innerHTML.toString()
    value = Number(value.toString() + number)
  }

  function clear() {
    value = 0;
  }

  function submit() {
    dispatch('submit', {
      value
    })
  }
</script>
<div class="fixed bottom-0 inset-x-0 p-2">
  <div class="w-full h-12 border-2 mb-2 rounded-xl grid place-content-center text-xl">{value}</div>
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
  @apply grid place-content-center h-16 bg-gray-100 active:bg-gray-200 rounded-xl text-xl;
}
</style>