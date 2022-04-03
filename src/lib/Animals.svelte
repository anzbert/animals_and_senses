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

  let quiz = [];

  const getCombo = () => {
    let combo = [];

    combo.push(uniqueNamesGenerator({ dictionaries: [senses] }));
    combo.push(uniqueNamesGenerator({ dictionaries: [animals] }));
    combo.push(
      uniqueNamesGenerator({
        dictionaries: [animals.filter((animal) => animal != combo[1])],
      })
    );

    quiz = combo;
  };
</script>

<button on:click={getCombo}>Click Here</button>

<div class="quiz">
  {#if quiz[0]}
    <div>
      Compare the <span class="bold">{quiz[0]}</span> of
      <span class="bold">{quiz[1]}</span>
      and <span class="bold">{quiz[2]}</span>
    </div>
  {/if}
</div>

<style>
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
