<script lang="ts">
  import type { HTMLInputAttributes } from "svelte/elements";

  let {
    id,
    disabled = false,
    oninput,
    value = $bindable(),
    onkeydown,
  }: HTMLInputAttributes = $props();
</script>

<input
  class="border-b-4 min-w-10 max-w-10 text-center outline-0 text-5xl"
  type="text"
  minlength="1"
  {id}
  {disabled}
  {oninput}
  {onkeydown}
  bind:value
/>


