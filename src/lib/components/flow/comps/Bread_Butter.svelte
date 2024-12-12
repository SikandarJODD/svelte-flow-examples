<script lang="ts">
  import { page } from "$app/stores";
  import * as Breadcrumb from "$lib/components/ui/breadcrumb/index";
  let link_obj = $derived.by(() => {
    let url = $page.url.pathname.split("/").filter((n) => n != "");
    type AllObj = {
      name: string;
      url: string;
    };
    let all_objs: AllObj[] = [];
    url.map((n) => {
      let index = $page.url.pathname.search(`/${n}`);
      let generated_url = $page.url.pathname.slice(0, n.length + index + 1);
      let obj = {
        name: n === "flows" ? "Examples" : n,
        url: generated_url,
      };
      all_objs.push(obj);
    });
    return all_objs;
  });
</script>

<Breadcrumb.Root>
  <Breadcrumb.List>
    {#each link_obj as item, index}
      <Breadcrumb.Item>
        <Breadcrumb.Link class="capitalize" href={item.url}
          >{item.name}</Breadcrumb.Link
        >
      </Breadcrumb.Item>
      {#if index !== link_obj.length - 1}
        <Breadcrumb.Separator />
      {/if}
    {/each}
  </Breadcrumb.List>
</Breadcrumb.Root>
