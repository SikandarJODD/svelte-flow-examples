<script>
  import BreadButter from "$lib/components/flow/comps/Bread_Butter.svelte";

  let { children } = $props();
</script>

<BreadButter />
{@render children()}
