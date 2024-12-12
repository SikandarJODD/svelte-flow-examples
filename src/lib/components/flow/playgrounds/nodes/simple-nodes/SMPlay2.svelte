<script lang="ts">
  import { writable } from "svelte/store";
  import { 
    SvelteFlow,
    Controls,
    Background, 
    BackgroundVariant,  
    Position,
  } from "@xyflow/svelte";
  // for light and dark mode using mode-watcher
  import { mode } from "mode-watcher";

  // 👇 this is important! You need to import the styles for Svelte Flow to work
  import "@xyflow/svelte/dist/style.css";
  import type { Node, Edge } from "@xyflow/svelte";

  // We are using writables for the nodes and edges to sync them easily. When a user drags a node for example, Svelte Flow updates its position.
  let nodes = writable<Node[]>([
    {
      id: "1",
      type: "default",
      data: { label: "Frameworks" },
      position: { x: 0, y: 0 },
      sourcePosition: Position.Right,
      targetPosition: Position.Left,
    },
    {
      id: "2",
      data: { label: "Svelte" },
      position: { x: 300, y: -100 },
      sourcePosition: Position.Right,
      targetPosition: Position.Left,
    },
    {
      id: "3",
      data: { label: "React" },
      position: { x: 300, y: 0 },
      sourcePosition: Position.Right,
      targetPosition: Position.Left,
    },
    {
      id: "4",
      data: { label: "Vue" },
      position: { x: 300, y: 100 },
      sourcePosition: Position.Right,
      targetPosition: Position.Left,
      
    },
  ]);

  // same for edges
  let edges = writable<Edge[]>([
    {
      id: "1-2",
      source: "1",
      type: "default",
      target: "2",
    },
    {
      id: "1-3",
      source: "1",
      type: "default",
      target: "3",
    },
    {
      id: "1-4",
      source: "1",
      type: "default",
      target: "4",
    },
  ]);
</script>

<!--
    👇 By default, the Svelte Flow container has a height of 100%.
    This means that the parent container needs a height to render the flow.
    -->
<div class="h-[500px] border">
  <SvelteFlow zoomOnDoubleClick={true} {nodes} {edges} fitView colorMode={$mode}>
    <Controls />
    <Background variant={BackgroundVariant.Dots} />
    <!-- <MiniMap /> -->
  </SvelteFlow>
</div>
