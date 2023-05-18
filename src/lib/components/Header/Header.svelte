<script lang="ts">
  import Search from "$lib/components/Search/Search.svelte";

  let header: HTMLDivElement;
</script>

<div class="header" bind:this={header}>
  <div class="logo">
    <img src="/img/logo.png" alt="" />
    <div class="title">
      Studenti <br />
      Indipendenti
    </div>
  </div>

  <Search />
</div>

<style lang="scss">
  @import "./header.scss";
</style>
