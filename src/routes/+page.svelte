<script lang="ts">
  import { onMount } from "svelte";
  import { setCookie, getCookie } from "$lib/helpers/cookieHelper";

  import Info from "$lib/components/Info/Info.svelte";
  import Groups from "$lib/components/Groups/Groups.svelte";

  let logo = "/img/logo.png";
  let darkModeIcon = "";
  let i = 0;

  onMount(() => {
    const darkMode = getCookie("darkMode");
    if (darkMode === "dark") {
      changeMode();
    }
  });

  function changeMode() {
    // L'esercizio di spiegare queste 3 righe e' lasciato a te
    i += 1;
    if (i < 3) return;
    i %= 3;

    darkModeIcon = darkModeIcon === "" ? "" : "";
    logo = darkModeIcon === "" ? "/img/logo.png" : "/img/logo-scuro.png";

    setCookie("darkMode", darkModeIcon === "" ? "light" : "dark", 365);

    document
      .querySelector("html")
      ?.setAttribute("data-theme", darkModeIcon === "" ? "light" : "dark");
  }
</script>

<div class="homepage">
  <button on:click={() => changeMode()} class="sss">Super Secret Setting</button
  >
  <Info />
  <div class="center" data-sveltekit-preload-data>
    <a class="notify" href="/Salvamatricole.pdf" target="_blank">
      Guida Salvamatricole
    </a>
    <a class="events" href="/events">Eventi</a>
  </div>
  <Groups />
</div>

<style lang="scss">
  @import "$lib/scss/homepage.scss";
  @import "$lib/scss/standard.scss";
</style>
