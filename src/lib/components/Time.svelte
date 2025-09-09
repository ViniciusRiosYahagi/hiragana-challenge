<script lang="ts">
  let time = $state(60);

  $effect(() => {
    const seconds = setInterval(() => {
      if (time === 0) return;
      time--;
    }, 1000);

    return () => {
      clearInterval(seconds);
    };
  });
</script>

<p class="text-success text-6xl">{time}</p>
