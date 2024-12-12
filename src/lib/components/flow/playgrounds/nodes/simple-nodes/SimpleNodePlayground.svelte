<script>
  import { writable } from "svelte/store";
  import {
    SvelteFlow,
    Controls,
    Background,
    BackgroundVariant,
    MiniMap,
  } from "@xyflow/svelte";
  // for light and dark mode using mode-watcher
  import { mode } from "mode-watcher";

  // 👇 this is important! You need to import the styles for Svelte Flow to work
  import "@xyflow/svelte/dist/style.css";

  // We are using writables for the nodes and edges to sync them easily. When a user drags a node for example, Svelte Flow updates its position.
  let nodes = writable([
    {
      id: "1",
      type: "default",
      data: { label: "Simple Node" },
      position: { x: -100, y: 0 },
    },
    {
      id: "2",
      type: "default",
      data: { label: "Second Node" },
      position: { x: 0, y: 150 },
    },
  ]);

  // same for edges
  let edges = writable([
    {
      id: "1-2",
      type: "default",
      source: "1",
      target: "2",
    },
  ]);
</script>

<!--
  👇 By default, the Svelte Flow container has a height of 100%.
  This means that the parent container needs a height to render the flow.
  -->
<div class="h-[500px] border">
  <SvelteFlow {nodes} {edges} fitView colorMode={$mode}>
    <Controls />
    <Background variant={BackgroundVariant.Dots} />
    <MiniMap />
  </SvelteFlow>
</div>
