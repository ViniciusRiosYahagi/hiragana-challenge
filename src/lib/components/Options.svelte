<script lang="ts">
  import { page } from "$app/state";
  import { Button, Theme } from "$lib";
  import { Settings, Close, Home, Abc, Game, Github } from "$lib/icons";
</script>

<!-- Icons/Settings div -->
<div class="fab fab-flower m-6">
  <span
    tabindex="0"
    role="button"
    class="btn btn-lg btn-circle fab-main-action bg-success"
  >
    <!-- Settings Icon -->
    <Settings />
  </span>
  <!-- Redirect to home -->
  <Button href="/">
    <!-- Home/Close Icon -->
    <!-- If home page show close icon else Home -->
    {#if page.url.pathname === "/"}
      <Close />
    {:else}
      <Home />
    {/if}
  </Button>
  <!-- Toggle theme Component/Icon-->
  <Theme />
  <!-- Redirect to hiragana show case route -->
  <Button href="/hiragana">
    <!-- Abc Icon -->
    <Abc />
  </Button>
  <!-- Redirect to game route -->
  <Button href="/game">
    <!-- Game Icon -->
    <Game />
  </Button>
  <!-- Redirect to github repository -->
  <Button href="https://github.com/ViniciusRiosYahagi/hiragana-challenge">
    <!-- Github Icon -->
    <Github />
  </Button>
</div>
