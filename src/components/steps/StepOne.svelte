<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let step: number
  export let bothAreOfAge: number
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>
      <legend>{step}.) Are you and the recipient both adults?<sup>*</sup></legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={bothAreOfAge} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={1}>
          <label for="yes">
            <strong>Yes</strong>
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={bothAreOfAge} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={0}>
          <label for="no">
            <strong>No</strong>
          </label>
        </div>
      </fieldset>

      <div>
        <button type="button" on:click={() => goToStep(0)}>
          &lsaquo; Back
        </button>

        <button
          disabled={typeof bothAreOfAge === 'undefined'}
          on:click={() => goToStep(2)}
        >
          Next &rsaquo;
        </button>
      </div>

      <aside class="footnotes">
        <p>
          *<i>In the legal sense, that is; not necessarily the maturity sense.</i>
        </p>
      </aside>
  </form>
</TransitionContainer>
