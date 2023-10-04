<script lang="ts">
	import {links, contacts} from "$lib/data/links";
</script>

<div class="info">
	<div class="title">Link utili</div>
	<div class="contacts">
		{#each contacts as contact}
			<a href={contact.link} class="contact">
				{contact.icon}
			</a>
		{/each}
	</div>
	<div class="links">
		{#each links as link}
			<div class="link">
				<div class="icon">{link.icon}</div>
				<a target="_blank" href={link.link}>{link.text}</a>
			</div>
		{/each}
	</div>
</div>

<style lang="scss">
	@import "./info.scss";
</style>
