<script lang="ts">
  import { fly, scale } from "svelte/transition";
  import { onMount } from "svelte";

  export let groups;

  export let area: keyof typeof groups;

  let group = groups[area];
  let areaName = area.charAt(0).toUpperCase() + area.slice(1);
  let open = false;

  onMount(() => {
    document.addEventListener("keydown", (e) => {
      if (e.key == "Escape") open = false;
    });
  });

  function closePopup(e: MouseEvent) {
    const target = e.target as HTMLElement;

    if (target.classList.contains("popup-container")) {
      open = false;
    }
  }
</script>

  <button class="area" on:click={() => (open = true)} in:scale>
    {areaName}
  </button>

{#if open}
  <div class="popup-container" in:scale out:scale on:mouseup={closePopup}>
    <div class="popup">
      <button class="close" on:click={() => (open = false)}></button>
      <div class="title">
        {areaName}
      </div>

      {#each Object.keys(group) as area}
        <div class="department">
          <div class="header">
            <div class="subtitle">
              {area}
            </div>
            <div class="other-container">
              {#if group[area].other.length > 0}
                {#each group[area].other as other}
                  <a
                    href={other.link}
                    class="other
                  {other.link.includes('instagram') ? 'instagram' : ''}
                  {other.link.includes('t.me') ? 'telegram' : ''}"
                  >
                    {#if other.link.includes("instagram")}
                      
                    {:else if other.link.includes("t.me")}
                      
                    {/if}
                  </a>
                {/each}
              {/if}
            </div>
          </div>
          <div class="courses">
            {#each group[area].list as course}
              <div class="course">
                <div class="course-name">
                  {course.name}
                </div>
                <div class="links">
                  {#each course.links as link}
                    <a
                      href={link}
                      target="_blank"
                      class="link
                  {link.includes('whatsapp') ? 'whatsapp' : ''}
                  {link.includes('t.me') ? 'telegram' : ''}
                  {link.includes('instagram') ? 'instagram' : ''}
                  "
                    >
                      {#if link.includes("whatsapp")}
                        
                      {:else if link.includes("t.me")}
                        
                      {:else if link.includes("instagram")}
                        
                      {/if}
                    </a>
                  {/each}
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
{/if}

<style lang="scss">
  @import "./area.scss";
</style>
