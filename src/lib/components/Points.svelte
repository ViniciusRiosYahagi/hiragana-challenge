<script lang="ts">
  let points = $state(0);
  let max = $state(0);
  let miss = $state(0);
</script>

<div class="flex gap-3 text-success text-2xl">
  <p class="text-error">Miss: {miss}</p>
  <p>Match: {points}</p>
  <p>Max: {max}</p>
</div>
