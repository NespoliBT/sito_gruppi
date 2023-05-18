<script lang="ts">
  import { groups } from "$lib/data/groups";
  import Area from "$lib/components/Area/Area.svelte";

  const aree = Object.keys(groups);
</script>

<div class="groups">
  <div class="title">Gruppi matricole</div>
  <div class="areas">
    {#each aree as area}
      <Area {area} />
    {/each}
  </div>
</div>

<style lang="scss">
  @import "./groups.scss";
</style>
