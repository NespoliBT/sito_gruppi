<script lang="ts">
  import { groups_1 } from "$lib/data/groups_1";
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";

  let open = false;

  export let searchResults: {
    list: Array<any>;
    other: Array<any>;
  } = {
    list: [],
    other: [],
  };

  onMount(() => {
    document.addEventListener("click", (e) => {
      const target = e.target as HTMLElement;
      const parent = target.parentElement as HTMLElement;
      console.log(target);

      if (!parent.classList.contains("search")) {
        open = false;
      }
    });
  });

  function search(e: Event) {
    const target = e.currentTarget as HTMLInputElement;
    const searchQuery: string = target.value.toLowerCase();

    searchResults = {
      list: [],
      other: [],
    };

    if (!searchQuery) return;

    open = true;

    for (const area in groups) {
      const group = groups[area];

      for (const department in group) {
        for (const item of group[department]?.list) {
          if (item.name.toLowerCase().includes(searchQuery)) {
            searchResults.list.push([item.name, item.links]);
          }
        }

        for (const item of group[department].other) {
          if (item.name.toLowerCase().includes(searchQuery)) {
            searchResults.other.push([item.name, item.links]);
          }
        }
      }
    }

    // console.log(searchResults.list);
  }
</script>

<div class="search">
  <input
    type="text"
    on:input={search}
    placeholder="Cerca un gruppo"
    on:click={() => (open = true)}
  />
  {#if searchResults.list.length && open}
    <div class="search-results" in:fly={{ y: -50 }} out:fly={{ y: -50 }}>
      {#each searchResults.list as group}
        <div class="group">
          <div class="group-name">
            {group[0]}
          </div>
          <div class="links">
            {#each group[1] as link}
              <a
                href={link}
                target="_blank"
                class="link
                  {link.includes('whatsapp') ? 'whatsapp' : ''}
                  {link.includes('t.me') ? 'telegram' : ''}
                "
              >
                {#if link.includes("whatsapp")}
                  
                {:else if link.includes("t.me")}
                  
                {/if}
              </a>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  {/if}
</div>

<style lang="scss">
  @import "./search.scss";
</style>
