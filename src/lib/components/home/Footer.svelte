<script>
  import ArrowUpRightIcon from "lucide-svelte/icons/arrow-up-right";
</script>

<footer
  class="relative z-10 overflow-hidden border-t border-border/50 bg-background"
>
  {@render blur()}
  <div class="relative mx-auto w-full max-w-7xl px-8 py-16 md:px-3">
    <div class="flex gap-10 max-md:flex-col md:justify-between">
      <div class="flex flex-col gap-4">
        <h1 class="text-xl font-bold">Svelte Flow Examples</h1>
        <p class="text-sm font-normal text-foreground">
          Examples to make life easier
        </p>
        <span class="text-sm font-normal text-foreground">
          Made by{" "}
          <a
            href="https://github.com/SikandarJODD"
            target="_blank"
            rel="noopener noreferrer"
            class="text-primary font-medium"
          >
            Sikandar Bhide
          </a>
        </span>
      </div>
      <div class="flex flex-col gap-4 text-sm">
        <a href="/flow" class="text-foreground duration-200 hover:text-primary">
          Explore Flows
        </a>
        <a
          href="https://github.com/SikandarJODD/svelte-flow-examples"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex items-center gap-1 text-foreground duration-200 hover:text-primary"
        >
          Source code
          <ArrowUpRightIcon
            size={10}
            class="transition-transform duration-300 group-hover:-translate-y-0.5 group-hover:translate-x-0.5"
          />
        </a>
        <a
          href="https://github.com/SikandarJODD"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex items-center gap-1 text-foreground duration-200 hover:text-primary"
        >
          GitHub
          <ArrowUpRightIcon
            size={10}
            class="transition-transform duration-300 group-hover:-translate-y-0.5 group-hover:translate-x-0.5"
          />
        </a>
        <a
          href="https://x.com/Sikandar_Bhide"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex items-center gap-1 text-foreground duration-200 hover:text-primary"
        >
          Twitter
          <ArrowUpRightIcon
            size={10}
            class="transition-transform duration-300 group-hover:-translate-y-0.5 group-hover:translate-x-0.5"
          />
        </a>
      </div>
    </div>
  </div>
</footer>

{#snippet blur()}
  <!-- svelte-ignore element_invalid_self_closing_tag -->
  <div
    aria-hidden="true"
    class="user-select-none center pointer-events-none absolute -top-1 left-1/2 h-[200px] w-full max-w-[400px] -translate-x-1/2 -translate-y-1/2"
    style="
      background: conic-gradient(from 90deg at 50% 50%, #00000000 50%, #0a0a0a 50%),radial-gradient(rgba(134, 134, 134, 0.1) 0%, transparent 80%)"
  />
{/snippet}
