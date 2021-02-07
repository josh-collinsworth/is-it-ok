<script lang="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let resetForm: () => void
</script>

<TransitionContainer>
  <h2><span>🛑</span> Don't do it.</h2>

  <p>If they did not specifically, in no uncertain terms ask for it, <em>never</em> send a dick pic.</p>

  <p>If you're not 100% sure they want one, you can at least ask. (But maybe just assume they don't, because there's no going back from that question.)</p>


  <button on:click={resetForm}>Take again</button>
</TransitionContainer>
