<script lang="ts">
  const hiraganaData = [
    {
      category: "Vogais",
      characters: [
        { jp: "あ", en: "A" },
        { jp: "い", en: "I" },
        { jp: "う", en: "U" },
        { jp: "え", en: "E" },
        { jp: "お", en: "O" },
      ],
    },

    {
      category: "Linha K",
      characters: [
        { jp: "か", en: "KA" },
        { jp: "き", en: "KI" },
        { jp: "く", en: "KU" },
        { jp: "け", en: "KE" },
        { jp: "こ", en: "KO" },
      ],
    },

    {
      category: "Linha S",
      characters: [
        { jp: "さ", en: "SA" },
        { jp: "し", en: "SHI" },
        { jp: "す", en: "SU" },
        { jp: "せ", en: "SE" },
        { jp: "そ", en: "SO" },
      ],
    },

    {
      category: "Linha T",
      characters: [
        { jp: "た", en: "TA" },
        { jp: "ち", en: "CHI" },
        { jp: "つ", en: "TSU" },
        { jp: "て", en: "TE" },
        { jp: "と", en: "TO" },
      ],
    },

    {
      category: "Linha N",
      characters: [
        { jp: "な", en: "NA" },
        { jp: "に", en: "NI" },
        { jp: "ぬ", en: "NU" },
        { jp: "ね", en: "NE" },
        { jp: "の", en: "NO" },
      ],
    },

    {
      category: "Linha H",
      characters: [
        { jp: "は", en: "HA" },
        { jp: "ひ", en: "HI" },
        { jp: "ふ", en: "FU" },
        { jp: "へ", en: "HE" },
        { jp: "ほ", en: "HO" },
      ],
    },

    {
      category: "Linha M",
      characters: [
        { jp: "ま", en: "MA" },
        { jp: "み", en: "MI" },
        { jp: "む", en: "MU" },
        { jp: "め", en: "ME" },
        { jp: "も", en: "MO" },
      ],
    },

    {
      category: "Linha Y",
      characters: [
        { jp: "や", en: "YA" },
        { jp: "ゆ", en: "YU" },
        { jp: "よ", en: "YO" },
      ],
    },

    {
      category: "Linha R",
      characters: [
        { jp: "ら", en: "RA" },
        { jp: "り", en: "RI" },
        { jp: "る", en: "RU" },
        { jp: "れ", en: "RE" },
        { jp: "ろ", en: "RO" },
      ],
    },

    {
      category: "Linha W",
      characters: [
        { jp: "わ", en: "WA" },
        { jp: "を", en: "WO" },
      ],
    },

    {
      category: "Especiais",
      characters: [{ jp: "ん", en: "N" }],
    },
  ];
</script>

<div class="flex justify-center gap-3 mx-3">
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
