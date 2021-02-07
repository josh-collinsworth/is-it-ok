<script lang="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let resetForm: () => void
</script>

<TransitionContainer>
  <h2><span>🛑</span> Nope, not ok.</h2>

  <p>If there's <em>any</em> chance this person might think this is about something other than a picture of a dick, it's your responsibility to keep that pic (and the dick in it) to yourself.</p>

  <button on:click={resetForm}>Take again</button>
</TransitionContainer>
