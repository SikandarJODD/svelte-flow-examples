<script lang="ts">
  let { children } = $props();
  import Shell from "lucide-svelte/icons/shell";
  import { slide } from "svelte/transition";
  import ChevronRight from "lucide-svelte/icons/chevron-right";
  import ChevronDown from "lucide-svelte/icons/chevron-down";
  type SideNav = {
    name: string;
    url: string;
    isExpand?: boolean;
    subnavs?: SubNavs[];
  };
  type SubNavs = {
    name: string;
    url: string;
  };
  let sidenavs: SideNav[] = $state([
    {
      name: "Nodes",
      url: "/flows/nodes",
      isExpand: true,
      subnavs: [
        {
          name: "Simple Nodes",
          url: "/flows/nodes/simple-nodes",
        },
        {
          name: "Custom Nodes",
          url: "/flows/nodes/custom-nodes",
        },
        {
          name: "Updating Nodes",
          url: "/flows/nodes/updating-nodes",
        },
        {
          name: "Add Node on edge drop",
          url: "/flows/nodes/add-node-on-edge-drop",
        },
        {
          name: "proximity connect",
          url: "/flows/nodes/proximity-connect",
        },
        {
          name: "node resizer",
          url: "/flows/nodes/node-resizer",
        },
        {
          name: "easy connect",
          url: "/flows/nodes/easy-connect",
        },
        {
          name: "connection limit",
          url: "/flows/nodes/connection-limit",
        },
        {
          name: "intersections",
          url: "/flows/nodes/intersections",
        },
      ],
    },
    {
      name: "Edges",
      url: "/flows/edges",
      isExpand: false,
      subnavs: [
        {
          name: "connection line",
          url: "/flows/edges/connection-line",
        },
        {
          name: "custom edges",
          url: "/flows/edges/custom-edges",
        },
        {
          name: "edge label renderer",
          url: "/flows/edges/edges-label-renderer",
        },
        {
          name: "edge markers",
          url: "/flows/edges/edge-markers",
        },
        {
          name: "edge types",
          url: "/flows/edges/edges-types",
        },
      ],
    },
  ]);
</script>

<div>
  <!-- Off-canvas menu for mobile, show/hide based on off-canvas menu state. -->
  <div class="relative z-50 lg:hidden" role="dialog" aria-modal="true">
    <!--
        Off-canvas menu backdrop, show/hide based on off-canvas menu state.
  
        Entering: "transition-opacity ease-linear duration-300"
          From: "opacity-0"
          To: "opacity-100"
        Leaving: "transition-opacity ease-linear duration-300"
          From: "opacity-100"
          To: "opacity-0"
      -->
    <div class="fixed inset-0 bg-gray-900/80" aria-hidden="true"></div>

    <div class="fixed inset-0 flex">
      <!--
          Off-canvas menu, show/hide based on off-canvas menu state.
  
          Entering: "transition ease-in-out duration-300 transform"
            From: "-translate-x-full"
            To: "translate-x-0"
          Leaving: "transition ease-in-out duration-300 transform"
            From: "translate-x-0"
            To: "-translate-x-full"
        -->
      <div class="relative mr-16 flex w-full max-w-xs flex-1">
        <!--
            Close button, show/hide based on off-canvas menu state.
  
            Entering: "ease-in-out duration-300"
              From: "opacity-0"
              To: "opacity-100"
            Leaving: "ease-in-out duration-300"
              From: "opacity-100"
              To: "opacity-0"
          -->
        <div class="absolute left-full top-0 flex w-16 justify-center pt-5">
          <button type="button" class="-m-2.5 p-2.5">
            <span class="sr-only">Close sidebar</span>
            <svg
              class="size-6 text-white"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              aria-hidden="true"
              data-slot="icon"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>

        <!-- Sidebar component, swap this element with another sidebar if you like -->
        <div
          class="flex grow flex-col gap-y-5 overflow-y-auto bg-gray-900 px-6 pb-2 ring-1 ring-white/10"
        >
          <div class="flex h-16 shrink-0 items-center">
            <img
              class="h-8 w-auto"
              src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=500"
              alt="Your Company"
            />
          </div>
          <nav class="flex flex-1 flex-col">
            <ul role="list" class="flex flex-1 flex-col gap-y-7">
              <li>
                <ul role="list" class="-mx-2 space-y-1">
                  <li>
                    <!-- Current: "bg-gray-800 text-white", Default: "text-gray-400 hover:text-white hover:bg-gray-800" -->
                    <a
                      href="#"
                      class="group flex gap-x-3 rounded-md bg-gray-800 p-2 text-sm/6 font-semibold text-white"
                    >
                      <svg
                        class="size-6 shrink-0"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="currentColor"
                        aria-hidden="true"
                        data-slot="icon"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="m2.25 12 8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75M8.25 21h8.25"
                        />
                      </svg>
                      Dashboard
                    </a>
                  </li>
                  <li>
                    <a
                      href="#"
                      class="group flex gap-x-3 rounded-md p-2 text-sm/6 font-semibold text-gray-400 hover:bg-gray-800 hover:text-white"
                    >
                      <svg
                        class="size-6 shrink-0"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="currentColor"
                        aria-hidden="true"
                        data-slot="icon"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M15 19.128a9.38 9.38 0 0 0 2.625.372 9.337 9.337 0 0 0 4.121-.952 4.125 4.125 0 0 0-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 0 1 8.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0 1 11.964-3.07M12 6.375a3.375 3.375 0 1 1-6.75 0 3.375 3.375 0 0 1 6.75 0Zm8.25 2.25a2.625 2.625 0 1 1-5.25 0 2.625 2.625 0 0 1 5.25 0Z"
                        />
                      </svg>
                      Team
                    </a>
                  </li>
                </ul>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </div>

  <!-- Static sidebar for desktop -->
  <div
    class="hidden lg:fixed lg:inset-y-0 lg:z-50 lg:flex lg:w-72 lg:flex-col mt-[65px] border-r"
  >
    <!-- Sidebar component, swap this element with another sidebar if you like -->
    <div
      class="flex grow flex-col gap-y-5 overflow-y-auto bg-background px-6 pt-4"
    >
      <nav class="flex flex-1 flex-col">
        <ul role="list" class="flex flex-1 flex-col">
          {#each sidenavs as nav}
            <li>
              <button
                onclick={() => {
                  nav.isExpand = !nav.isExpand;
                }}
                class="-mx-2 w-full flex rounded-md px-2 py-1 text-sm/6 items-center font-semibold text-primary justify-between"
              >
                <span>
                  {nav.name}
                </span>
                <span>
                  <ChevronRight
                    strokeWidth={1.4}
                    size={16}
                    class="{!nav.isExpand
                      ? ''
                      : 'rotate-90'} transition-all duration-300 text-muted-foreground"
                  />
                </span>
              </button>
              {#if nav.subnavs && nav.isExpand}
                <ul role="list" class="border-l pl-1.5" transition:slide>
                  {#each nav.subnavs as subnav}
                    <li>
                      <a
                        href={subnav.url}
                        class="group flex rounded-md pl-2 py-1.5 hover:bg-muted text-sm/6 font-normal text-primary/50 capitalize"
                      >
                        {subnav.name}
                      </a>
                    </li>
                  {/each}
                </ul>
              {/if}
            </li>
          {/each}
        </ul>
      </nav>
    </div>
  </div>

  <div
    class="sticky top-0 z-40 flex items-center gap-x-6 bg-gray-900 px-4 py-4 shadow-sm sm:px-6 lg:hidden"
  >
    <button type="button" class="-m-2.5 p-2.5 text-gray-400 lg:hidden">
      <span class="sr-only">Open sidebar</span>
      <svg
        class="size-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        aria-hidden="true"
        data-slot="icon"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
        />
      </svg>
    </button>
    <div class="flex-1 text-sm/6 font-semibold text-white">Dashboard</div>
    <a href="#">
      <span class="sr-only">Your profile</span>
      <img
        class="size-8 rounded-full bg-gray-800"
        src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
        alt=""
      />
    </a>
  </div>

  <main class="py-10 lg:pl-72">
    <div class="px-4 sm:px-6 lg:px-8">
      {@render children()}
    </div>
  </main>
</div>
