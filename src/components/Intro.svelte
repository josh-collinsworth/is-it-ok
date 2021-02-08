<script lang="ts">
import TransitionContainer from './TransitionContainer.svelte'

export let goToStep: (step: number) => void
</script>

<TransitionContainer>
  <h1>
    <span aria-hidden="true">🍆 📸</span>
    Should I send a&nbsp;dick&nbsp;pic?
  </h1>

  <div>
    <button on:click={() => goToStep(1)}>
      Click here to take the survey
    </button>
  </div>
</TransitionContainer>
