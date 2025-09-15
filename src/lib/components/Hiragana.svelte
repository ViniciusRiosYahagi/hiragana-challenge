<script lang="ts">
  import { page } from "$app/state";
  import { Button, Input, Points, Time } from "$lib";
  import { start, time } from "$lib/stores/vars.svelte";

  $effect(() => {
    generate();
  });

  let hiragana = $state([
    { jp: "あ", en: "A" },
    { jp: "い", en: "I" },
    { jp: "う", en: "U" },
    { jp: "え", en: "E" },
    { jp: "お", en: "O" },
    { jp: "か", en: "KA" },
    { jp: "き", en: "KI" },
    { jp: "く", en: "KU" },
    { jp: "け", en: "KE" },
    { jp: "こ", en: "KO" },
    { jp: "さ", en: "SA" },
    { jp: "し", en: "SHI" },
    { jp: "す", en: "SU" },
    { jp: "せ", en: "SE" },
    { jp: "そ", en: "SO" },
    { jp: "た", en: "TA" },
    { jp: "ち", en: "CHI" },
    { jp: "つ", en: "TSU" },
    { jp: "て", en: "TE" },
    { jp: "と", en: "TO" },
    { jp: "な", en: "NA" },
    { jp: "に", en: "NI" },
    { jp: "ぬ", en: "NU" },
    { jp: "ね", en: "NE" },
    { jp: "の", en: "NO" },
    { jp: "は", en: "HA" },
    { jp: "ひ", en: "HI" },
    { jp: "ふ", en: "FU" },
    { jp: "へ", en: "HE" },
    { jp: "ほ", en: "HO" },
    { jp: "ま", en: "MA" },
    { jp: "み", en: "MI" },
    { jp: "む", en: "MU" },
    { jp: "め", en: "ME" },
    { jp: "も", en: "MO" },
    { jp: "や", en: "YA" },
    { jp: "ゆ", en: "YU" },
    { jp: "よ", en: "YO" },
    { jp: "ら", en: "RA" },
    { jp: "り", en: "RI" },
    { jp: "る", en: "RU" },
    { jp: "れ", en: "RE" },
    { jp: "ろ", en: "RO" },
    { jp: "わ", en: "WA" },
    { jp: "を", en: "WO" },
    { jp: "ん", en: "N" },
  ]);
  let jp = $state("");
  let en = $state("");
  let chars = $state([]);
  let randomIndex = $state(0);
  let KeyboardKey = $state("");

  function generate() {
    let random = Math.floor(Math.random() * hiragana.length);
    jp = hiragana[randomIndex].jp;
    en = hiragana[randomIndex].en;
    randomIndex = random;
    chars.length = 0;
    document.getElementById("input-0")?.focus();
  }

  function check() {
    if (chars.join("").toUpperCase() === en.toUpperCase()) {
      const time = setTimeout(() => {
        chars.length = 0;
        generate();
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
  $inspect(start.value);
</script>

<section class="h-screen flex justify-center items-center">
  <div class="flex flex-col gap-10 items-center pointer-events-auto">
    {#if page.url.pathname === "/game"}
      <Time />
      <Points />
    {/if}
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
      <Button
        onclick={() => (start.value = !start.value)}
        disabled={start.value}>Play</Button
      >
    {:else}
      <Button onclick={generate}>Skip</Button>
    {/if}
  </div>
</section>
