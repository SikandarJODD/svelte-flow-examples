<script lang="ts">
  import { writable } from "svelte/store";
  import {
    SvelteFlow,
    Background,
    type Edge,
    type Node,
    Panel,
    MiniMap,
  } from "@xyflow/svelte";
  import "@xyflow/svelte/dist/style.css";
  import Label from "$lib/components/ui/label/label.svelte";
  import Input from "$lib/components/ui/input/input.svelte";
  import Checkbox from "$lib/components/ui/checkbox/checkbox.svelte";
  import { mode } from "mode-watcher";
  import { onMount } from "svelte";
  const initialNodes: Node[] = [
    { id: "1", data: { label: "Select Based" }, position: { x: 100, y: 100 } },
    { id: "2", data: { label: "Svelte is fun" }, position: { x: 100, y: 200 } },
  ];

  const initialEdges: Edge[] = [{ id: "e1-2", source: "1", target: "2" }];

  let nodes = writable<Node[]>(initialNodes);
  let edges = writable(initialEdges);

  let nodeId = $state("");
  let nodeName = $state("");
  let nodeBg = $state("");
  let nodeHidden = $state(false);

  function updateNode() {
    $nodes.forEach((node) => {
      if (nodeId === "") {
        alert("Please Select Node");
      } else if (node.id === nodeId) {
        node.data = {
          ...node.data,
          label: nodeName,
        };

        if (nodeBg) {
          node.style = `background: ${nodeBg};`;
        }
        if (nodeHidden !== undefined) {
          node.hidden = nodeHidden;
          $edges.forEach((edge) => {
            if (edge.id === "e1-2") {
              edge.hidden = nodeHidden;
            }
          });
        }
      }
      //   Reassign the node
      $nodes = $nodes;
      $edges = $edges;
    });
  }
  let nodeSelected = (event) => {
    console.log("Selected Node", event.detail.node);
    let nodeDetail = event.detail.node;
    nodeName = nodeDetail.data.label;
    nodeId = nodeDetail.id;
  };
</script>

<div class="h-[500px]">
  <SvelteFlow
    {nodes}
    {edges}
    fitView
    colorMode={$mode}
    on:nodeclick={nodeSelected}
  >
    <!-- Node Update Controls -->
    <Panel
      position="top-right"
      class="flex flex-col gap-2 bg-background border-dashed border border-muted-foreground/60  p-3 rounded-xl"
    >
      <div>
        <Label for="name">Name</Label>
        <Input
          bind:value={nodeName}
          type="text"
          name="name"
          id="name"
          placeholder="Select Node to Update"
          oninput={updateNode}
        />
      </div>
      <div>
        <label for="bg">Background</label>
        <Input
          oninput={updateNode}
          bind:value={nodeBg}
          type="color"
          name="bg"
          id="bg"
        />
      </div>
      <div class="flex items-center gap-2">
        <Label for="hidden">Hidden</Label>
        <Checkbox onCheckedChange={updateNode} name="hidden" id="hidden" bind:checked={nodeHidden} />
      </div>
    </Panel>
    <!-- MiniMap -->
    <MiniMap />
    <Background />
  </SvelteFlow>
</div>
