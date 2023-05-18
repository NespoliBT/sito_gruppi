<script lang="ts">
  import Footer from "$lib/components/Footer/Footer.svelte";
  import Header from "$lib/components/Header/Header.svelte";
  import Groups from "$lib/components/Groups/Groups.svelte";

  console.log("page");
</script>

<Header />
<div class="homepage">
  <Groups />
</div>

<style lang="scss">
  @import "$lib/scss/homepage.scss";
  @import "$lib/scss/standard.scss";
</style>
