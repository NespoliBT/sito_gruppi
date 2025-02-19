<script lang="ts">
  import { onMount } from "svelte";
  import events from "$lib/data/events";
  import { fly } from "svelte/transition";
</script>

<div class="events-background"></div>

<div class="events">
  <div class="lasers">
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
    <div class="laser"></div>
  </div>
  <div class="title">Eventi</div>

  <div class="events-list">
    {#each events as e, i}
      <a
        class="event-container"
        style={`background-image: url(${e.img});`}
        in:fly|global={{
          y: 100,
          duration: 500,
          delay: 300 * i,
        }}
        href={e.link}
        target="_blank"
      >
      </a>
    {/each}
  </div>
</div>

<style lang="scss">
  @import "$lib/scss/events.scss";
  @import "$lib/scss/standard.scss";
</style>
