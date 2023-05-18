<script lang="ts">
  import { onMount } from "svelte";
  import Search from "$lib/components/Search/Search.svelte";
  import { setCookie, getCookie } from "$lib/helpers/cookieHelper";

  let header: HTMLDivElement;

  let logo = "/img/logo.png";
  let darkModeIcon = "";

  onMount(() => {
    const darkMode = getCookie("darkMode");
    if (darkMode === "dark") {
      changeMode();
    }
  });

  function changeMode() {
    darkModeIcon = darkModeIcon === "" ? "" : "";
    logo = darkModeIcon === "" ? "/img/logo.png" : "/img/logo-scuro.png";

    setCookie("darkMode", darkModeIcon === "" ? "light" : "dark", 365);

    document
      .querySelector("html")
      ?.setAttribute("data-theme", darkModeIcon === "" ? "light" : "dark");
  }
</script>

<div class="header" bind:this={header}>
  <div class="logo">
    <img src={logo} alt="" />
    <div class="title">
      Studenti <br />
      Indipendenti
    </div>
  </div>
  <Search />
  <div class="dark-mode">
    <button on:click={() => changeMode()}>{darkModeIcon}</button>
  </div>
</div>

<style lang="scss">
  @import "./header.scss";
</style>
