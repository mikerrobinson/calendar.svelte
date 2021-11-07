<script>
	import Event from './Event.svelte';
	export let date = new Date();
	export let isActive = false;
	export let isSelected = false;
	//export let events = [];
</script>

<style>
	.spacer {
		background: #ddd;
	}

	td {
		text-align: left;
		vertical-align: top;
		position: relative;
		overflow: hidden;
	}
</style>

{#if !isActive }
<td class="spacer">{date.getDate()} foo</td>
{:else}
<td class="day {isSelected ? "selected" : ""}">{date.getDate()}</td>
{/if}
