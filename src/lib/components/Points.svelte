<script lang="ts">
  import { points } from "$lib/stores/vars.svelte";

  let max = $state(0);
</script>

<div class="flex gap-3 text-success text-2xl">
  <p>Match: {points.value}</p>
  <p>Max: {max}</p>
</div>
