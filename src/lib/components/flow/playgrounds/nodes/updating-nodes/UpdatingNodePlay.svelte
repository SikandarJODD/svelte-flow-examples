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
    { id: "1", data: { label: "-" }, position: { x: 100, y: 100 } },
    { id: "2", data: { label: "Svelte is fun" }, position: { x: 100, y: 200 } },
  ];

  const initialEdges: Edge[] = [{ id: "e1-2", source: "1", target: "2" }];

  let nodes = writable<Node[]>(initialNodes);
  let edges = writable(initialEdges);

  let nodeName = $state("Edit Node....");
  let nodeBg = $state("#eff");
  let nodeHidden = $state(false);

  function updateNode() {
    $nodes.forEach((node) => {
      if (node.id === "1") {
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
  onMount(() => {
    updateNode();
  });
</script>

<div class="h-[500px] border border-muted-foreground/40">
  <SvelteFlow {nodes} {edges} fitView colorMode={$mode}>
    <!-- Node Update Controls -->
    <Panel
      position="top-right"
      class="flex flex-col gap-2 bg-background border-dashed border border-muted-foreground/60  p-3 rounded-xl"
    >
      <div>
        <Label for="name">Name</Label>
        <Input
          bind:value={nodeName}
          oninput={updateNode}
          type="text"
          name="name"
          id="name"
        />
      </div>
      <div>
        <label for="bg">Background</label>
        <Input
          bind:value={nodeBg}
          oninput={updateNode}
          type="color"
          name="bg"
          id="bg"
        />
      </div>
      <div class="flex items-center gap-2">
        <Label for="hidden">Hidden</Label>
        <Checkbox
          name="hidden"
          id="hidden"
          onCheckedChange={updateNode}
          bind:checked={nodeHidden}
        />
      </div>
    </Panel>
    <!-- MiniMap -->
    <MiniMap />
    <Background />
  </SvelteFlow>
</div>
