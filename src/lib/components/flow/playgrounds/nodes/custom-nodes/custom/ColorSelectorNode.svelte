<script lang="ts">
  import { Handle, Position, type NodeProps } from "@xyflow/svelte";
  import { bgColor } from "./bgcolor.svelte";

  type $$Props = NodeProps;
  type Props = {
    data: $$Props["data"];
    isConnectable: $$Props["isConnectable"];
  };
  let { data, isConnectable }: Props = $props();
</script>

<Handle
  type="target"
  position={Position.Left}
  style="background: #555;"
  {isConnectable}
/>
<div class="text-primary bg-background flex flex-col p-2 border-pink-500 border">
  <span>
    Custom Color Picker Node <br />
    {data.label} <strong>{bgColor.value}</strong>
  </span>
  <input class="nodrag" type="color" bind:value={bgColor.value} />
</div>
<Handle
  type="source"
  position={Position.Right}
  id="a"
  style="top: 10px; background: #555;"
  {isConnectable}
/>
<Handle
  type="source"
  position={Position.Right}
  id="b"
  style="bottom: 10px; top: auto; background: #555;"
  {isConnectable}
/>
