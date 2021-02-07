<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let hasReallyRequested: boolean
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>

      <legend>3.) …Really? They asked? Explicitly? Like, you're <em>sure</em> they want one? There's no possible way this is a misunderstanding or something?</legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={hasReallyRequested} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={true}>
          <label for="yes">
            <strong>Yes</strong>, they really asked
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={hasReallyRequested} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={false}>
          <label for="no">
            <strong>No</strong>, maybe they don't want it
          </label>
        </div>
      </fieldset>

      <div>
        <button
          disabled={typeof hasReallyRequested === 'undefined'}
          on:click={() => goToStep(4)}
        >
          Next
        </button>
      </div>
  </form>
</TransitionContainer>
