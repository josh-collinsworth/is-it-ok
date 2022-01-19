<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let absolutelySure: number
  export let step: number
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>

      <legend>{step}.) Look, we just have to check again: you're <em>absolutely sure</em> they want it, and there's <em>no possible way</em> any of this communication could've been misinterpred or misrepresented <em>at all</em>?</legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={absolutelySure} class="sr" type="radio" id="yes" name="you-really-really-sure" value={1}>
          <label for="yes">
            <strong>Yes</strong>, I'm absolutely certain
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={absolutelySure} class="sr" type="radio" id="no" name="you-really-really-sure" value={0}>
          <label for="no">
            <strong>Well…</strong> I might have misunderstood
          </label>
        </div>
      </fieldset>

      <div>
        <button type="button" on:click={() => goToStep(4)}>
          &lsaquo; Back
        </button>

        <button
          disabled={typeof absolutelySure === 'undefined'}
          on:click={() => goToStep(6)}
        >
          Next &rsaquo;
        </button>
      </div>
  </form>
</TransitionContainer>
