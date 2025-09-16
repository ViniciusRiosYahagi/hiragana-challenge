<script lang="ts">
  import type { Snippet } from "svelte";

  interface Button {
    children: Snippet;
    onclick?: (e: Event) => void;
    href?: string;
    disabled?: boolean;
  }

  let { children, onclick, href, disabled = false }: Button = $props();
</script>

{#if href}
  <a {href} class="btn btn-lg btn-circle p-3 font-bold">{@render children()}</a>
{:else}
  <button {onclick} {disabled} class="btn btn-success p-3 font-bold"
    >{@render children()}</button
  >
{/if}
