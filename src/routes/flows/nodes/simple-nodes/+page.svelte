<script>
  import SimpleNodePlayground from "$lib/components/flow/playgrounds/nodes/simple-nodes/SimpleNodePlayground.svelte";
  import SmPlay2 from "$lib/components/flow/playgrounds/nodes/simple-nodes/SMPlay2.svelte";
  import SmPlay3 from "$lib/components/flow/playgrounds/nodes/simple-nodes/SMPlay3.svelte";
</script>

<div class="mt-4 space-y-2">
  <h1 class="text-3xl font-semibold">Simple Nodes</h1>
  <p class="text-muted-foreground">
    simple nodes consist of easy examples related to nodes and edges.
  </p>
  <div class="space-y-4">
    <SimpleNodePlayground />
    <SmPlay2 />
    <SmPlay3 />
  </div>
</div>
