<h1 class="mb-16 text-center text-4xl font-bold">Addition</h1>

<p class="mb-16 text-center text-xl">How many digits?</p>

<div class="grid grid-cols-3 p-2 gap-2">
  {#each Array(3).fill(null) as _, i}
    <a
      class="bg-gray-100 hover:bg-gray-200 p-4 grid place-content-center text-xl"
      href={"/addition/test?digits="+(i+1)}
    >
      {i+1}
    </a>
  {/each}
</div>