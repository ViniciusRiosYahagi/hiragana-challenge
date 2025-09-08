<script lang="ts">
let hiragana = $state([
    // Vogais
    {jp: "あ", en: "A"},
    {jp: "い", en: "I"},
    {jp: "う", en: "U"},
    {jp: "え", en: "E"},
    {jp: "お", en: "O"},
    
    // Linha K
    {jp: "か", en: "KA"},
    {jp: "き", en: "KI"},
    {jp: "く", en: "KU"},
    {jp: "け", en: "KE"},
    {jp: "こ", en: "KO"},
    
    // Linha S
    {jp: "さ", en: "SA"},
    {jp: "し", en: "SHI"},
    {jp: "す", en: "SU"},
    {jp: "せ", en: "SE"},
    {jp: "そ", en: "SO"},
    
    // Linha T
    {jp: "た", en: "TA"},
    {jp: "ち", en: "CHI"},
    {jp: "つ", en: "TSU"},
    {jp: "て", en: "TE"},
    {jp: "と", en: "TO"},
    
    // Linha N
    {jp: "な", en: "NA"},
    {jp: "に", en: "NI"},
    {jp: "ぬ", en: "NU"},
    {jp: "ね", en: "NE"},
    {jp: "の", en: "NO"},
    
    // Linha H
    {jp: "は", en: "HA"},
    {jp: "ひ", en: "HI"},
    {jp: "ふ", en: "FU"},
    {jp: "へ", en: "HE"},
    {jp: "ほ", en: "HO"},
    
    // Linha M
    {jp: "ま", en: "MA"},
    {jp: "み", en: "MI"},
    {jp: "む", en: "MU"},
    {jp: "め", en: "ME"},
    {jp: "も", en: "MO"},
    
    // Linha Y
    {jp: "や", en: "YA"},
    {jp: "ゆ", en: "YU"},
    {jp: "よ", en: "YO"},
    
    // Linha R
    {jp: "ら", en: "RA"},
    {jp: "り", en: "RI"},
    {jp: "る", en: "RU"},
    {jp: "れ", en: "RE"},
    {jp: "ろ", en: "RO"},
    
    // Linha W
    {jp: "わ", en: "WA"},
    {jp: "を", en: "WO"},
    
    // N
    {jp: "ん", en: "N"},
    
    // Sokuon (pequeno tsu)
    {jp: "っ", en: "(pausa)"},
    
    // Versões com dakuten (〝) - Linha G
    {jp: "が", en: "GA"},
    {jp: "ぎ", en: "GI"},
    {jp: "ぐ", en: "GU"},
    {jp: "げ", en: "GE"},
    {jp: "ご", en: "GO"},
    
    // Linha Z
    {jp: "ざ", en: "ZA"},
    {jp: "じ", en: "JI"},
    {jp: "ず", en: "ZU"},
    {jp: "ぜ", en: "ZE"},
    {jp: "ぞ", en: "ZO"},
    
    // Linha D
    {jp: "だ", en: "DA"},
    {jp: "ぢ", en: "JI"},
    {jp: "づ", en: "ZU"},
    {jp: "で", en: "DE"},
    {jp: "ど", en: "DO"},
    
    // Linha B
    {jp: "ば", en: "BA"},
    {jp: "び", en: "BI"},
    {jp: "ぶ", en: "BU"},
    {jp: "べ", en: "BE"},
    {jp: "ぼ", en: "BO"},
    
    // Linha P (handakuten ﾟ)
    {jp: "ぱ", en: "PA"},
    {jp: "ぴ", en: "PI"},
    {jp: "ぷ", en: "PU"},
    {jp: "ぺ", en: "PE"},
    {jp: "ぽ", en: "PO"},
    
    // Contrações (Yōon)
    {jp: "きゃ", en: "KYA"},
    {jp: "きゅ", en: "KYU"},
    {jp: "きょ", en: "KYO"},
    
    {jp: "しゃ", en: "SHA"},
    {jp: "しゅ", en: "SHU"},
    {jp: "しょ", en: "SHO"},
    
    {jp: "ちゃ", en: "CHA"},
    {jp: "ちゅ", en: "CHU"},
    {jp: "ちょ", en: "CHO"},
    
    {jp: "にゃ", en: "NYA"},
    {jp: "にゅ", en: "NYU"},
    {jp: "にょ", en: "NYO"},
    
    {jp: "ひゃ", en: "HYA"},
    {jp: "ひゅ", en: "HYU"},
    {jp: "ひょ", en: "HYO"},
    
    {jp: "みゃ", en: "MYA"},
    {jp: "みゅ", en: "MYU"},
    {jp: "みょ", en: "MYO"},
    
    {jp: "りゃ", en: "RYA"},
    {jp: "りゅ", en: "RYU"},
    {jp: "りょ", en: "RYO"},
    
    {jp: "ぎゃ", en: "GYA"},
    {jp: "ぎゅ", en: "GYU"},
    {jp: "ぎょ", en: "GYO"},
    
    {jp: "じゃ", en: "JA"},
    {jp: "じゅ", en: "JU"},
    {jp: "じょ", en: "JO"},
    
    {jp: "びゃ", en: "BYA"},
    {jp: "びゅ", en: "BYU"},
    {jp: "びょ", en: "BYO"},
    
    {jp: "ぴゃ", en: "PYA"},
    {jp: "ぴゅ", en: "PYU"},
    {jp: "ぴょ", en: "PYO"}
]);

  let char = $state("")
  let anwser = $state("")

  function generate() {
    let randomIndex = Math.floor(Math.random() * hiragana.length)
    char = hiragana[randomIndex].jp
    anwser = hiragana[randomIndex].en
  }

</script>

<p>{char}</p>

<button onclick={generate}>Pl</button>


