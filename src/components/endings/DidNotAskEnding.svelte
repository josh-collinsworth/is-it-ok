<script lang="ts">
  import TransitionContainer from '../TransitionContainer.svelte'

  export let resetForm: () => void
</script>

<TransitionContainer>
  <h2><span>🛑</span> Don't&nbsp;do&nbsp;it.</h2>

  <p>Unless they specifically asked in no uncertain terms, it's <em>never</em> ok to send a dick pic.</p>

  <p>If you're not 100% sure, you can at least ask first. (<i>But maybe just assume they don't, because there's no going back from that question</i>.)</p>


  <button on:click={resetForm}>Take again</button>
</TransitionContainer>
