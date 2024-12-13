<script>
  import Playground from "$lib/components/flow/playgrounds/nodes/add-node-on-edge-drop/playground.svelte";
  import { SvelteFlowProvider } from "@xyflow/svelte";
</script>

<div class="space-y-2 mt-4">
  <h1 class="font-semibold text-3xl">Add Node on Edge Drop</h1>
  <div>
    <SvelteFlowProvider>
      <Playground />
    </SvelteFlowProvider>
  </div>
</div>
