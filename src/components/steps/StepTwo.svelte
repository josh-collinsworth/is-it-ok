<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let hasRequested: boolean
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>
      <legend>2.) Has the recipient specifically <em>asked</em> you for a picture of your dick?<sup>*</sup></legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={hasRequested} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={true}>
          <label for="yes">
            <strong>Yes</strong>
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={hasRequested} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={false}>
          <label for="no">
            <strong>No</strong>
          </label>
        </div>
      </fieldset>

      <div>
        <button
          disabled={typeof hasRequested === 'undefined'}
          on:click={() => goToStep(3)}
        >
          Next
        </button>
      </div>

      <aside class="footnotes">
        <p>*Or at least, <em>a</em> dick</p>
      </aside>
  </form>
</TransitionContainer>
