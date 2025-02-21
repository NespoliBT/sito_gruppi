<script lang="ts">
  import { dev } from "$app/environment";
  import { inject } from "@vercel/analytics";
  import { onMount } from "svelte";
  import { setCookie, getCookie } from "$lib/helpers/cookieHelper";
  import Header from "$lib/components/Header/Header.svelte";
  import { contacts } from "$lib/data/links";

  inject({ mode: dev ? "development" : "production" });

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

<Header />
<slot />
<div class="contacts">
  {#each contacts as contact}
    <a href={contact.link} class="contact">
      {contact.icon}
    </a>
  {/each}
</div>

<style lang="scss">
  @import "$lib/scss/standard.scss";
</style>
