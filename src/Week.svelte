<script>
	import Day from './Day.svelte';
	
	export let startDate = new Date();
	export let selectedDate = new Date(startDate);
	let days = [];
	days.push(new Date(startDate));
	for (let i = 0; i < 6; i++) {
		days.push(new Date(startDate.setDate(startDate.getDate() + 1)));
	}
</script>

<style>
</style>

<tr class="week">
{#each days as day, count}
	<Day date={day} isActive={day.getMonth() == selectedDate.getMonth()} />
{/each}
</tr>