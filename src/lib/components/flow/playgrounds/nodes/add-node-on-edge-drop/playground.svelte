<script lang="ts">
  import { writable } from "svelte/store";
  import {
    SvelteFlow,
    useSvelteFlow,
    Background,
    type Edge,
    type Node,
    type OnConnectEnd,
    Controls,
    MiniMap,
  } from "@xyflow/svelte";

  import "@xyflow/svelte/dist/style.css";
  import { mode } from "mode-watcher";

  let initialNodes: Node[] = [
    {
      id: "0",
      type: "default",
      data: { label: "selcting handle.." },
      position: { x: 0, y: 0 },
    },
    {
      id: "1",
      type: "default",
      data: { label: "Add New Node " },
      position: { x: 100, y: 200 },
    },
  ];
  let initialEdges: Edge[] = [
    {
      id: "0-1",
      source: "0",
      target: "1",
      type: "default",
    },
  ];
  let nodes = writable<Node[]>(initialNodes);
  let edges = writable<Edge[]>(initialEdges);

  let id = 2;
  let getID = () => `${id++}`;

  let rect: DOMRectReadOnly;

  let { screenToFlowPosition } = useSvelteFlow();

  let handleConnectEnd: OnConnectEnd = (event, connectionState) => {
    if (connectionState.isValid) return;
    let sourceNodeId = connectionState.fromNode?.id ?? "1";
    let id = getID();
    let { clientX, clientY } =
      "changedTouches" in event ? event.changedTouches[0] : event;
    let newNode: Node = {
      id,
      data: { label: `Node ${id}` },
      position: screenToFlowPosition({
        x: clientX,
        y: clientY,
      }),
      origin: [0.5, 0.5],
    };
    // Push above new node to writable Nodes
    $nodes.push(newNode);
    $edges.push({
      source: String(sourceNodeId),
      target: String(id),
      id: `${sourceNodeId}--${id}`,
    });
    // Reassign nodes & edges
    $nodes = $nodes;
    $edges = $edges;
  };
</script>

<svelte:window />
<div class="h-[500px] wrapper" bind:contentRect={rect}>
  <SvelteFlow
    {nodes}
    {edges}
    colorMode={$mode}
    fitViewOptions={{ padding: 4 }}
    fitView
    onconnectend={handleConnectEnd}
  >
    <Background />
    <Controls />
    <MiniMap />
  </SvelteFlow>
</div>
