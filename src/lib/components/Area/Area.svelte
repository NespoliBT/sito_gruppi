<script lang="ts">
  import { groups } from "$lib/data/groups";

  export let area: keyof typeof groups;

  console.log(typeof area);

  let group = groups[area];

  let areaName = area.charAt(0).toUpperCase() + area.slice(1);
</script>

<div class="area">
  {areaName}
</div>

<style lang="scss">
  @import "./area.scss";
</style>
