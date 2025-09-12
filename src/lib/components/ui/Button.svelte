<script lang="ts">
  import type { Snippet } from "svelte";

  interface Button {
    children: Snippet
    onclick?: (e: Event) => void
    href?: string
  }

  let { children, onclick, href }: Button = $props();
</script>

{#if href}
  <a {href} class="btn btn-lg btn-circle p-3 font-bold" target="_blank">{@render children()}</a>
{:else}
  <button {onclick} class="btn btn-success p-3 font-bold"
    >{@render children()}</button
  >
{/if}
