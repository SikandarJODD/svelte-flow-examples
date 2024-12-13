<script lang="ts">
  import { writable } from "svelte/store";
  import {
    SvelteFlow,
    Background,
    Controls,
    MiniMap,
    Position,
    type Node,
    type Edge,
  } from "@xyflow/svelte";

  import "@xyflow/svelte/dist/style.css";
  import ColorSelectorNode from "./custom/ColorSelectorNode.svelte";
  import { bgColor } from "./custom/bgcolor.svelte";
  import { mode } from "mode-watcher";

  const nodeTypes = {
    selectorNode: ColorSelectorNode,
  };

  const initialNodes: Node[] = [
    {
      id: "1",
      type: "input",
      data: { label: "An input node" },
      position: { x: 0, y: 50 },
      sourcePosition: Position.Right,
    },
    {
      id: "2",
      type: "selectorNode",
      data: { label: "Color" },
      position: { x: 300, y: 50 },
    },
    {
      id: "3",
      type: "output",
      data: { label: "Output A" },
      position: { x: 650, y: 25 },
      targetPosition: Position.Left,
    },
    {
      id: "4",
      type: "output",
      data: { label: "Output B" },
      position: { x: 650, y: 100 },
      targetPosition: Position.Left,
    },
  ];

  const initialEdges: Edge[] = [
    {
      id: "e1-2",
      source: "1",
      target: "2",
      animated: true,
      style: "stroke: #fff;",
    },
    {
      id: "e2a-3",
      source: "2",
      target: "3",
      sourceHandle: "a",
      animated: true,
      style: "stroke: #fff;",
    },
    {
      id: "e2b-4",
      source: "2",
      target: "4",
      sourceHandle: "b",
      animated: true,
      style: "stroke: #fff;",
    },
  ];

  const nodes = writable<Node[]>(initialNodes);
  const edges = writable(initialEdges);
</script>

<div style="height:100vh;">
  <SvelteFlow
    {nodes}
    {edges}
    {nodeTypes}
    style="background: {bgColor.value};"
    colorMode={$mode}
    fitView
  >
    <Background />
    <Controls />
    <MiniMap />
  </SvelteFlow>
</div>
