<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let hasRequested: number
  export let step: number
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>
      <legend>{step}.) Has the recipient specifically <em>asked</em> you for a picture of your dick?<sup>*</sup></legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={hasRequested} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={1}>
          <label for="yes">
            <strong>Yes</strong>
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={hasRequested} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={0}>
          <label for="no">
            <strong>No</strong>
          </label>
        </div>
      </fieldset>

      <div>
        <button type="button" on:click={() => goToStep(1)}>
          &lsaquo; Back
        </button>

        <button
          disabled={typeof hasRequested === 'undefined'}
          on:click={() => goToStep(3)}
        >
          Next &rsaquo;
        </button>
      </div>

      <aside class="footnotes">
        <p>*Or at least, <em>a</em> dick</p>
      </aside>
  </form>
</TransitionContainer>
