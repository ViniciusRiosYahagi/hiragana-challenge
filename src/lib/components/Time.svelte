<script lang="ts">
  import { start, time } from "$lib/stores/vars.svelte";
  import { onDestroy } from "svelte";

  function startTime() {
    const seconds = setInterval(() => {
      time.value--;
      if (time.value === 0) {
        time.value = 60;
        start.value = false;
        clearInterval(seconds);
      }
    }, 1000);
  }

  $effect(() => {
    if (start.value) startTime();
  });

  onDestroy(() => {
    start.value = false;
  });
</script>

<p class="text-success text-6xl">{time.value}</p>
