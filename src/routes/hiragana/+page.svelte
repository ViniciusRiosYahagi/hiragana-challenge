<script lang="ts">
  const hiraganaData = [
    {
      characters: [
        { jp: "あ", en: "A" },
        { jp: "い", en: "I" },
        { jp: "う", en: "U" },
        { jp: "え", en: "E" },
        { jp: "お", en: "O" },
      ],
    },

    {
      characters: [
        { jp: "か", en: "KA" },
        { jp: "き", en: "KI" },
        { jp: "く", en: "KU" },
        { jp: "け", en: "KE" },
        { jp: "こ", en: "KO" },
      ],
    },

    {
      characters: [
        { jp: "さ", en: "SA" },
        { jp: "し", en: "SHI" },
        { jp: "す", en: "SU" },
        { jp: "せ", en: "SE" },
        { jp: "そ", en: "SO" },
      ],
    },

    {
      characters: [
        { jp: "た", en: "TA" },
        { jp: "ち", en: "CHI" },
        { jp: "つ", en: "TSU" },
        { jp: "て", en: "TE" },
        { jp: "と", en: "TO" },
      ],
    },

    {
      characters: [
        { jp: "な", en: "NA" },
        { jp: "に", en: "NI" },
        { jp: "ぬ", en: "NU" },
        { jp: "ね", en: "NE" },
        { jp: "の", en: "NO" },
      ],
    },

    {
      characters: [
        { jp: "は", en: "HA" },
        { jp: "ひ", en: "HI" },
        { jp: "ふ", en: "FU" },
        { jp: "へ", en: "HE" },
        { jp: "ほ", en: "HO" },
      ],
    },

    {
      characters: [
        { jp: "ま", en: "MA" },
        { jp: "み", en: "MI" },
        { jp: "む", en: "MU" },
        { jp: "め", en: "ME" },
        { jp: "も", en: "MO" },
      ],
    },

    {
      characters: [
        { jp: "や", en: "YA" },
        { jp: "ゆ", en: "YU" },
        { jp: "よ", en: "YO" },
      ],
    },

    {
      characters: [
        { jp: "ら", en: "RA" },
        { jp: "り", en: "RI" },
        { jp: "る", en: "RU" },
        { jp: "れ", en: "RE" },
        { jp: "ろ", en: "RO" },
      ],
    },

    {
      characters: [
        { jp: "わ", en: "WA" },
        { jp: "を", en: "WO" },
      ],
    },

    {
      characters: [{ jp: "ん", en: "N" }],
    },
  ];
</script>

<div class="flex flex-col justify-center gap-3 mt-40 lg:flex-row">
  {#each hiraganaData.reverse() as { characters }}
    <div>
      {#each characters as { jp, en }}
        <div class="p-5 border-2 border-success text-center mb-3">
          <p class="text-5xl text-success">{jp}</p>
          <p class="text-xl text-success mt-3">{en}</p>
        </div>
      {/each}
    </div>
  {/each}
</div>
