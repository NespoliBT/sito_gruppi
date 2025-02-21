<script lang="ts">
  import points from "$lib/data/points";

  let open: boolean[] = [];
</script>

<div class="programma">
  <div class="title">Programma</div>
  <div class="info">Spero ti piacciano i muri di testo</div>
  <div class="program-list">
    {#each points as point, i}
      <div class="point">
        <button
          class="subtitle {open[i] ? 'active' : ''}"
          on:click={() => (open[i] = !open[i])}
        >
          {point.title}
        </button>
        {#if open[i]}
          <div class="text">
            {@html point.text}
          </div>
        {/if}
      </div>
    {/each}
  </div>
</div>

<style lang="scss">
  @import "$lib/scss/programma.scss";
  @import "$lib/scss/standard.scss";
</style>
