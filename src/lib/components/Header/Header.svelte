<script lang="ts">
  import { onMount } from "svelte";
  import Search from "$lib/components/Search/Search.svelte";
  import { setCookie, getCookie } from "$lib/helpers/cookieHelper";

  let header: HTMLDivElement;

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
      ?.setAttribute("data-theme", darkModeIcon === "" ? "light" : "rgb");
  }
</script>

<div class="header" bind:this={header}>
  <div class="logo">
    <img src={logo} alt="" on:click={changeMode} on:keydown={null} />
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
