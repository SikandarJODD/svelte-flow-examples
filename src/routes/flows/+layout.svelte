<script>
  import Sidebar from "$lib/components/flow/sidebar/Sidebar.svelte";

  let { children } = $props();
</script>

<Sidebar>
  {@render children()}
</Sidebar>
