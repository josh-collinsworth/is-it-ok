<script type="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let bothAreOfAge: boolean
  export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <form on:submit|preventDefault>
    <fieldset>
      <legend>1.) Are you and the recipient both adults?<sup>*</sup></legend>

      <div class="choices">
        <div class="wrapper">
          <input bind:group={bothAreOfAge} class="sr" type="radio" id="yes" name="has-requested-dick-pic" value={true}>
          <label for="yes">
            <strong>Yes</strong>
          </label>
        </div>
        <div class="wrapper">
          <input bind:group={bothAreOfAge} class="sr" type="radio" id="no" name="has-requested-dick-pic" value={false}>
          <label for="no">
            <strong>No</strong>
          </label>
        </div>
      </fieldset>

      <div>
        <button
          disabled={typeof bothAreOfAge === 'undefined'}
          on:click={() => goToStep(2)}
        >
          Next
        </button>
      </div>

      <aside class="footnotes">
        <p>
          *<i>In the legal sense, if not the maturity sense.</i>
        </p>
      </aside>
  </form>
</TransitionContainer>
