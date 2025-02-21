<script lang="ts">
  import { onMount } from "svelte";
  import events from "$lib/data/events";
  import { fly } from "svelte/transition";

  let loading = true;

  // preload images
  onMount(() => {
    events.forEach((e) => {
      const img = new Image();
      img.src = e.img;
    });

    loading = false;
  });
</script>

<div class="events-background"></div>

{#if loading}
  <div class="loading">
    <div class="title">Caricando gli eventi...</div>
  </div>
{:else}
  <div class="events" in:fly>
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
        <div
          class="event-container"
          in:fly|global={{
            y: 100,
            duration: 500,
            delay: 300 * i,
          }}
        >
          <a
            class="event"
            style={`background-image: url(${e.img});`}
            href={e.link}
            target="_blank"
          >
          </a>
          <div class="event-info">
            {#if e.date}
              <div class="date">{e.date}</div>
            {/if}
            {#if e.dateStart && e.dateEnd}
              <div class="dateSE">
                <div class="dateStart">Da: {e.dateStart}</div>
                <div class="dateEnd">A: {e.dateEnd}</div>
              </div>
            {/if}
          </div>
        </div>
      {/each}
    </div>
  </div>
{/if}

<style lang="scss">
  @import "$lib/scss/events.scss";
  @import "$lib/scss/standard.scss";
</style>
