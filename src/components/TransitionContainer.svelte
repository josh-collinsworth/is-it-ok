<script lang="ts">
  import { fly } from 'svelte/transition'
  import { quadIn, quadOut } from 'svelte/easing'

  let duration: number = 300
</script>

<div
  class="container"
  in:fly={{ x: 24, duration, delay: duration, easing: quadOut }}
  out:fly={{ x: -24, duration, easing: quadIn }}
>
  <slot />
</div>
