<script lang="ts">
  import { groups_1 } from "$lib/data/groups_2";
  import { groups_2 } from "$lib/data/groups_3";
  import { groups_3 } from "$lib/data/groups_1";
  import Area from "$lib/components/Area/Area.svelte";

  const aree_1 = Object.keys(groups_1);
  const aree_2 = Object.keys(groups_2);
  const aree_3 = Object.keys(groups_3);
  let opened = 1;
</script>

<div class="groups">
  <div class="title">Gruppi</div>
  <div class="year-selector">
    <div class="year {opened == 1 ? 'open' : ''}" on:click={() => (opened = 1)}>
      Primo anno
    </div>
    <div class="year {opened == 2 ? 'open' : ''}" on:click={() => (opened = 2)}>
      Secondo anno
    </div>
    <div class="year {opened == 3 ? 'open' : ''}" on:click={() => (opened = 3)}>
      Terzo anno
    </div>
  </div>
  {#if opened == 1}
    <div class="areas">
      {#each aree_1 as area}
        <Area {area} groups={groups_1} />
      {/each}
    </div>
  {/if}
  {#if opened == 2}
    <div class="areas">
      {#each aree_2 as area}
        <Area {area} groups={groups_2} />
      {/each}
    </div>
  {/if}
  {#if opened == 3}
    <div class="areas">
      {#each aree_3 as area}
        <Area {area} groups={groups_3} />
      {/each}
    </div>
  {/if}
</div>

<style lang="scss">
  @import "./groups.scss";
</style>
