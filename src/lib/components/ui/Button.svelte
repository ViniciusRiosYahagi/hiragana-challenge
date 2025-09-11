<script lang="ts">
  let { children, onclick} = $props()
</script>

<button {onclick} class="btn btn-success p-3 font-bold">{@render children()}</button>