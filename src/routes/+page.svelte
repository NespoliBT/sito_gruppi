<script lang="ts">
  import Info from "$lib/components/Info/Info.svelte";
  import Header from "$lib/components/Header/Header.svelte";
  import Groups from "$lib/components/Groups/Groups.svelte";
</script>

<Header />
<div class="homepage">
  <a class="notify" href="/Salvamatricole.pdf" target="_blank">
    Guida Salvamatricole
  </a>
  <Groups />
  <Info />
</div>

<style lang="scss">
  @import "$lib/scss/homepage.scss";
  @import "$lib/scss/standard.scss";
</style>
