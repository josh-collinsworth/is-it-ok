<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let hasNoOtherMotives: number
  export let step: number
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>

      <legend>{step}.) ...Wow. Ok. Well then. Are you in any position of power or authority over the recipient, or could they potentially be under the impression this transaction will get them something?<sup>*</sup></legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={hasNoOtherMotives} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={1}>
          <label for="yes">
            <strong>Yes</strong>
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={hasNoOtherMotives} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={0}>
          <label for="no">
            <strong>No</strong>
          </label>
        </div>
      </fieldset>

      <div>
        <button on:click={() => goToStep(3)}>
          &lsaquo; Back
        </button>

        <button
          disabled={typeof hasNoOtherMotives === 'undefined'}
          on:click={() => goToStep(5)}
        >
          Next &rsaquo;
        </button>
      </div>

      <aside class="footnotes">
        <p>*Other than a picture of a dick, of course</p>
      </aside>
  </form>
</TransitionContainer>
