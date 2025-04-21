<!-- src/lib/button/Simple.svelte -->
<script>
  // Texte affiché dans le bouton
  export let label = 'Cliquez-moi';

  // Type HTML du bouton (button, submit, reset…)
  export let type = 'button';

  // État disabled
  export let disabled = false;

  // Permet de forwarder les événements (click, focus…) au parent
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  function handleClick(event) {
    // renvoie l’événement pour qu’un parent puisse y réagir
    dispatch('click', event);

  }

</script>

<button
  class="simple-btn"
  {type}
  {disabled}
  on:click={handleClick}
>
  {label}
</button>

<style>
  .simple-btn {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: #1e90ff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s ease;
  }

  .simple-btn:hover {
    background-color: #1c86ee;
  }

  .simple-btn:disabled {
    background-color: #a9a9a9;
    cursor: not-allowed;
  }
</style>

