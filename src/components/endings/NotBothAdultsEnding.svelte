<script lang="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let resetForm: () => void
</script>

<TransitionContainer>
  <h2><span>🛑</span><br/>ABSOLUTELY NOT.</h2>

  <p>Dude. What the <em>fuck</em>?</p>

  <p>We don't even need to ask any more questions. 100% not ok, ever.</p>

  <button on:click={resetForm}>Take again</button>
</TransitionContainer>
