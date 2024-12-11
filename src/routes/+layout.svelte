<script lang="ts">
  import Navbar from "$lib/components/home/Navbar.svelte";
  import "../app.css";
  let { children } = $props();
  import { ModeWatcher } from "mode-watcher";
</script>

<ModeWatcher defaultMode="light" />
<Navbar />
{@render children()}
