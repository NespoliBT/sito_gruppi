<script lang="ts">
  import { onMount } from "svelte";
  import Search from "$lib/components/Search/Search.svelte";

  let height = 0;
  let header: HTMLDivElement;

  onMount(() => {
    height = header.offsetHeight;
  });
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

<div class="header-fix" style="height: {height}px" />

<style lang="scss">
  @import "./header.scss";
</style>
