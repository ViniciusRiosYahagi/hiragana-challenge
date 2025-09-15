<script lang="ts">
  import { start } from "$lib/stores/vars.svelte";
  import { onDestroy } from "svelte";

  let time = $state(60);

  function startTime() {
    const seconds = setInterval(() => {
      time--;
      if (time === 0) {
        time = 60;
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

<p class="text-success text-6xl">{time}</p>
