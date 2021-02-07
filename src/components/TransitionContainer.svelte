<script lang="ts">
  import { fly } from 'svelte/transition'
  import { quadIn, quadOut } from 'svelte/easing'

  let duration: number = 400
</script>

<div
  class="container"
  in:fly={{ y: 30, duration, delay: duration, easing: quadOut }}
  out:fly={{ y: -30, duration, easing: quadIn }}
>
  <slot />
</div>
