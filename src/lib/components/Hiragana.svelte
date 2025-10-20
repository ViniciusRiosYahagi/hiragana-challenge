<script lang="ts">
  import { page } from "$app/state";
  import { Button, Input, Points, Time } from "$lib";
  import { hiragna } from "$lib/data/hiragana";
  import { points, start } from "$lib/stores/vars.svelte";

  let hiragana = $state(hiragna)
  let jp = $state("");
  let en = $state("");
  let chars = $state([]);
  let randomIndex = $state(0);
  let KeyboardKey = $state("");

  $effect(() => {
    generate();
  });

  // function randomGenerator(array: object[]) {
  //   for (let i = array.length -1; i > 0; i--) {
  //     let randomID = Math.floor(Math.random() * (i + 1)) as number
  //     [array[i], array[randomID]] = [array[randomID], array[i]]
  //   }

  //   return array
  // }

  // randomGenerator(hiragana)

  // Function that set an new index
  function generate() {
    let newNumber;
    let random;

    // While the generated random number is equal to the last random number, generate a new number.
    do {
      newNumber = Math.floor(Math.random() * hiragana.length);
    } while (random === newNumber);

    random = newNumber;
    randomIndex = random;

    console.log(newNumber, random);

    jp = hiragana[randomIndex].jp;
    en = hiragana[randomIndex].en;

    chars.length = 0;
    document.getElementById("input-0")?.focus();
  }

  function check() {
    if (chars.join("").toUpperCase() === en.toUpperCase()) {
      const time = setTimeout(() => {
        chars.length = 0;
        generate();

        if (page.url.pathname !== "/") {
          points.value++;
        }
      }, 300);
      return () => clearInterval(time);
    }
  }

  function checkInput(i: number) {
    if (KeyboardKey === "Backspace") {
      if (i < 0) i = 0;
      document.getElementById(`input-${i - 1}`)?.focus();
    } else {
      document.getElementById(`input-${i + 1}`)?.focus();
      check();
    }
  }

  function play() {
    start.value = !start.value;
    points.value = 0;
    generate();
  }
</script>

<section class="h-screen flex justify-center items-center">
  <div class="flex flex-col gap-10 items-center pointer-events-auto">
    {#if page.url.pathname === "/game"}
      <Time />
      <Points />
    {/if}
    <!-- Hiragana Character display -->
    <p class="text-9xl text-success border-4 p-20">{jp}</p>

    <div class="flex gap-3">
      {#each hiragana[randomIndex].en as word, i}
        {#key word}
          {#if page.url.pathname === "/"}
            <Input
              id={`input-${i}`}
              bind:value={chars[i]}
              onkeydown={(e) => (KeyboardKey = e.key)}
              oninput={() => checkInput(i)}
            />
          {:else}
            <Input
              id={`input-${i}`}
              bind:value={chars[i]}
              onkeydown={(e) => (KeyboardKey = e.key)}
              oninput={() => checkInput(i)}
              disabled={!start.value}
            />
          {/if}
        {/key}
      {/each}
    </div>
    {#if page.url.pathname === "/game"}
      <Button onclick={() => play()} disabled={start.value}>Play</Button>
    {:else}
      <Button onclick={generate}>Skip</Button>
    {/if}
  </div>
</section>
