<script lang="ts">
import TransitionContainer from './TransitionContainer.svelte'

export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <h1>
    <span aria-hidden="true">🍆 📸</span>
    Should I send a&nbsp;dick&nbsp;pic?
  </h1>

  <p>Considering sending a dick pic, but not sure whether it's ok?</p>

  <p><b>You’re in the right place!</b></p>

  <div>
    <button on:click={() => goToStep(1)}>
      Click here to take the survey
    </button>
  </div>
</TransitionContainer>
