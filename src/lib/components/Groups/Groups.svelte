<script lang="ts">
  import { groups } from "$lib/data/groups";
  import Area from "$lib/components/Area/Area.svelte";

  const aree = Object.keys(groups);
</script>

<div class="groups">
  {#each aree as area}
    <Area {area} />
  {/each}
</div>

<style lang="scss">
  @import "./groups.scss";
</style>
