<script>
  import Button from "../ui/button/button.svelte";
</script>

<div class="h-[90vh] flex justify-center items-center">
  <div class="mx-auto max-w-3xl pb-32">
    <div class="hidden sm:mb-8 sm:flex sm:justify-center">
      <!-- <div
        class="relative rounded-full px-3 py-1 text-sm/6 text-gray-600 ring-1 ring-gray-900/10 hover:ring-gray-900/20"
      >
        Announcing our next round of funding. <a
          href="#"
          class="font-semibold text-indigo-600"
          ><span class="absolute inset-0" aria-hidden="true"></span>Read more
          <span aria-hidden="true">&rarr;</span></a
        >
      </div> -->
    </div>
    <div class="text-center">
      <h1
        class="text-balance text-5xl font-semibold tracking-tight text-transparent bg-clip-text from-zinc-900 to-zinc-600/80 bg-gradient-to-b dark:from-primary dark:to-primary/20 sm:text-7xl"
      >
        Svelte Flow Examples
      </h1>
      <p
        class="mt-5 text-pretty text-lg font-mono text-primary/80 sm:text-xl/8"
      >
        Examples to make life easier
      </p>
      <div class="mt-10 flex items-center justify-center gap-x-2">
        <Button size="lg">Get Started</Button>
        <Button size="lg" variant="outline">Flows</Button>
      </div>
    </div>
  </div>
</div>
