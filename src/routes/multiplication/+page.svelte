<script>
import { page } from '$app/stores';
import NumberInput from '$lib/NumberInput.svelte';

let value;
</script>

<h1>Multiplication</h1>
<button on:click={() => value = 0}>Reset</button>
<p>{value}</p>
<p>{$page.url.searchParams.get('number')}</p>
<NumberInput bind:value={value} />