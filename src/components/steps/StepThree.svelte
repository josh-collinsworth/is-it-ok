<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let hasReallyRequested: number
  export let step: number
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>

      <legend>{step}.) …Really? They asked? Explicitly? Like, you're <em>sure</em> they want one, right now? There's no possible way this is a misunderstanding or something?</legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={hasReallyRequested} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={1}>
          <label for="yes">
            <strong>Yes</strong>, I'm sure they really want it
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={hasReallyRequested} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={0}>
          <label for="no">
            <strong>No</strong>, I'm not positive
          </label>
        </div>
      </fieldset>

      <div>
        <button type="button" on:click={() => goToStep(2)}>
          &lsaquo; Back
        </button>

        <button
          disabled={typeof hasReallyRequested === 'undefined'}
          on:click={() => goToStep(4)}
        >
          Next &rsaquo;
        </button>
      </div>
  </form>
</TransitionContainer>
