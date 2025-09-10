<script lang="ts">
  import { Button, Points, Time } from "$lib";

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

    { jp: "が", en: "GA" },
    { jp: "ぎ", en: "GI" },
    { jp: "ぐ", en: "GU" },
    { jp: "げ", en: "GE" },
    { jp: "ご", en: "GO" },

    { jp: "ざ", en: "ZA" },
    { jp: "じ", en: "JI" },
    { jp: "ず", en: "ZU" },
    { jp: "ぜ", en: "ZE" },
    { jp: "ぞ", en: "ZO" },

    { jp: "だ", en: "DA" },
    { jp: "ぢ", en: "JI" },
    { jp: "づ", en: "ZU" },
    { jp: "で", en: "DE" },
    { jp: "ど", en: "DO" },

    { jp: "ば", en: "BA" },
    { jp: "び", en: "BI" },
    { jp: "ぶ", en: "BU" },
    { jp: "べ", en: "BE" },
    { jp: "ぼ", en: "BO" },

    { jp: "ぱ", en: "PA" },
    { jp: "ぴ", en: "PI" },
    { jp: "ぷ", en: "PU" },
    { jp: "ぺ", en: "PE" },
    { jp: "ぽ", en: "PO" },

    { jp: "きゃ", en: "KYA" },
    { jp: "きゅ", en: "KYU" },
    { jp: "きょ", en: "KYO" },

    { jp: "しゃ", en: "SHA" },
    { jp: "しゅ", en: "SHU" },
    { jp: "しょ", en: "SHO" },

    { jp: "ちゃ", en: "CHA" },
    { jp: "ちゅ", en: "CHU" },
    { jp: "ちょ", en: "CHO" },

    { jp: "にゃ", en: "NYA" },
    { jp: "にゅ", en: "NYU" },
    { jp: "にょ", en: "NYO" },

    { jp: "ひゃ", en: "HYA" },
    { jp: "ひゅ", en: "HYU" },
    { jp: "ひょ", en: "HYO" },

    { jp: "みゃ", en: "MYA" },
    { jp: "みゅ", en: "MYU" },
    { jp: "みょ", en: "MYO" },

    { jp: "りゃ", en: "RYA" },
    { jp: "りゅ", en: "RYU" },
    { jp: "りょ", en: "RYO" },

    { jp: "ぎゃ", en: "GYA" },
    { jp: "ぎゅ", en: "GYU" },
    { jp: "ぎょ", en: "GYO" },

    { jp: "じゃ", en: "JA" },
    { jp: "じゅ", en: "JU" },
    { jp: "じょ", en: "JO" },

    { jp: "びゃ", en: "BYA" },
    { jp: "びゅ", en: "BYU" },
    { jp: "びょ", en: "BYO" },

    { jp: "ぴゃ", en: "PYA" },
    { jp: "ぴゅ", en: "PYU" },
    { jp: "ぴょ", en: "PYO" },
  ]);
  let jp = $state("");
  let en = $state("");
  let chars = $state([]);
  let randomIndex = $state(0);

  function generate() {
    let random = Math.floor(Math.random() * hiragana.length);
    jp = hiragana[randomIndex].jp;
    en = hiragana[randomIndex].en;
    randomIndex = random;
    chars.length = 0;
  }

  function check() {
    if (chars.join("").toUpperCase() === en.toUpperCase()) {
      const time = setTimeout(() => {
        chars.length = 0;
        generate();
      }, 500);
      return () => clearInterval(time);
    }
  }

  function focusFirstInput() {
    const firstInput = document.getElementById("input-0");
    firstInput?.focus();
  }

  function nextInput(i: number) {
    const input = document.getElementById(`input-${i}`);
    input?.focus();
    check();
  }

  $effect(() => {
    generate();
    focusFirstInput();
  });

  $inspect(chars);
</script>

<section class="flex justify-center items-center mt-20">
  <div class="flex flex-col gap-10 items-center">
    <p class="text-9xl text-success border-4 p-20">{jp}</p>

    <div class="flex gap-3">
      {#each hiragana[randomIndex].en as word, i}
        {#key word}
          <input
            id={`input-${i}`}
            type="text"
            maxlength="1"
            bind:value={chars[i]}
            oninput={() => nextInput(i + 1)}
            class="border-b-4 min-w-10 max-w-10 text-center outline-0 text-5xl"
          />
        {/key}
      {/each}
    </div>
    <Button onclick={generate}>Skip</Button>
  </div>
</section>
