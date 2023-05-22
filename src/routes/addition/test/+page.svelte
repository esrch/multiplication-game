<script>
import {page} from '$app/stores';
import {goto} from '$app/navigation'
import NumberInput from '$lib/NumberInput.svelte';

let digits = $page.url.searchParams.get('digits');

const maxQuestions = 10;
let currentQuestion = 1;
let num1;
let num2;
let correct = false;
let incorrect = false;

function generateQuestion() {
  num1 = Math.floor(Math.random() * (10 ** digits))
  num2 = Math.floor(Math.random() * (10 ** digits))
}

generateQuestion()

function onCorrect() {
  if (currentQuestion >= 10) {
    goto('/success');
  }

  correct = true;
  setTimeout(() => correct = false, 700);

  currentQuestion++
  generateQuestion();
}

function onIncorrect() {
  incorrect = true;
  setTimeout(() => incorrect = false, 700)

  currentQuestion = 1;
  generateQuestion();
}
</script>

<div class="h-screen transition duration-700"
  class:bg-green-200={correct}
  class:bg-red-200={incorrect}
>
  <h1 class="mb-16 text-center text-4xl font-bold">Addition</h1>

  <p class="text-center text-4xl">{num1} + {num2}</p>
</div>

<NumberInput
  solution={num1 + num2}
  on:correct={onCorrect}
  on:incorrect={onIncorrect}
>
  <p class="mb-2 text-xl text-center">({currentQuestion} / {maxQuestions})</p>
</NumberInput>