<script>
import { page } from '$app/stores';
import NumberInput from '$lib/NumberInput.svelte';

let value;
</script>

<h1 class="mb-8 text-center text-4xl font-bold">Simple Multiplication</h1>

<p class="text-center text-xl">Choose a multiple to test</p>

<div class="grid grid-cols-5 gap-2 mt-8 px-4">
  {#each Array(10).fill(null) as _, i}
    <a
      class="grid place-content-center p-4 bg-gray-100 active:bg-gray-200 hover:bg-gray-200 text-xl" href={"/simple-multiplication/test?multiple="+(i+1)}
    >{i + 1}</a>
  {/each}
</div>