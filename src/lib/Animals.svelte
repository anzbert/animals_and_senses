<script lang="ts">
  import { uniqueNamesGenerator } from "unique-names-generator";

  const senses: Array<string> = [
    "Olfactory Sense",
    "Visual Sense",
    "Vocalization",
  ];
  const animals: Array<string> = [
    "Dogs",
    "Cats",
    "Cattle",
    "Sheep",
    "Horses",
    "Pigs",
    "Rabbits",
    "Rats or Mice",
    "Ferrets",
    "Alpacas",
    "Guinea Pigs",
    "Chicken",
    "Parrots",
  ];

  const detail: Array<string> = [
    "time budgeting",
    "senses",
    "social behaviour",
    "reproductive behaviour",
    "typical normal species behaviour",
  ];

  let compareTwoQuiz = [];

  const handleCompareTwo = () => {
    let quizCombo = [];

    quizCombo.push(uniqueNamesGenerator({ dictionaries: [senses] }));
    quizCombo.push(uniqueNamesGenerator({ dictionaries: [animals] }));
    quizCombo.push(
      uniqueNamesGenerator({
        dictionaries: [animals.filter((animal) => animal != quizCombo[1])],
      })
    );

    compareTwoQuiz = quizCombo;
  };

  let detailQuiz = [];

  const handleDetailQuiz = () => {
    let quizCombo = [];

    quizCombo.push(uniqueNamesGenerator({ dictionaries: [detail] }));
    quizCombo.push(uniqueNamesGenerator({ dictionaries: [animals] }));
    detailQuiz = quizCombo;
  };
</script>

<hr />

<button on:click={handleCompareTwo}>Compare Senses</button>

{#if compareTwoQuiz[0]}
  <div class="quiz">
    <div>
      Compare the <span class="bold">{compareTwoQuiz[0]}</span> of
      <span class="bold">{compareTwoQuiz[1]}</span>
      and <span class="bold">{compareTwoQuiz[2]}</span>
    </div>
  </div>
{/if}

<hr />

<button on:click={handleDetailQuiz}>Behavior Details</button>

{#if detailQuiz[0]}
  <div class="quiz">
    <div>
      Describe the <span class="bold">{detailQuiz[0]}</span> of
      <span class="bold">{detailQuiz[1]}</span>
    </div>
  </div>
{/if}

<style>
  hr {
    margin: 4rem 0;
  }
  .bold {
    font-weight: bold;
  }
  .quiz {
    margin-top: 2em;
    display: flex;
    flex-direction: row;
    width: 100%;
    border: 2px solid red;
    justify-content: center;
    gap: 2em;
  }

  button {
    font-family: inherit;
    font-size: inherit;
    padding: 1em 2em;
    color: #ff3e00;
    background-color: rgba(255, 62, 0, 0.1);
    border-radius: 2em;
    border: 2px solid rgba(255, 62, 0, 0);
    outline: none;
    width: 200px;
    font-variant-numeric: tabular-nums;
    cursor: pointer;
  }

  button:focus {
    border: 2px solid #ff3e00;
  }

  button:active {
    background-color: rgba(255, 62, 0, 0.2);
  }
</style>
