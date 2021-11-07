<script>
	import Week from './Week.svelte';
	const today = new Date();
	export let year = today.getFullYear();
	export let month = today.getMonth();
	export let day = today.getDate();
	export let selectedDate = new Date(year, month, day);
	let firstOfMonth = new Date(year, month, 1);
	let firstOfNextMonth = new Date(year, month, 1);
	firstOfNextMonth.setMonth(firstOfNextMonth.getMonth() + 1);
	let firstCellDate = new Date(year, month, 1);
	firstCellDate.setDate(1 - firstOfMonth.getDay());
	let weeks = [];
	for (let d = new Date(firstCellDate); d < firstOfNextMonth; d.setDate(d.getDate() + 7)) {
    weeks.push(new Date(d));
	}
</script>

<style>
	.calendar {
		table-layout: fixed;
		height: 100%;
		width: 100%;
		box-sizing: border-box;
		border: 4px solid #000;
		background-color: #000;
		color: #fff;
	}

	thead td {
		text-align: center;
	}
	
	tbody {
		background: #fff;
		color: #000;
	}
</style>

<table class="monthly calendar">
  <thead>
    <tr>
      <th colspan="7">{firstOfMonth.toLocaleString('default', { month: 'long', year: 'numeric' })}</th>
    </tr>
    <tr>
      <td>{new Date(2000,0,2).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,3).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,4).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,5).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,6).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,7).toLocaleString('default', { weekday: 'short' })}</td>
			<td>{new Date(2000,0,8).toLocaleString('default', { weekday: 'short' })}</td>
    </tr>
  </thead>
  <tbody>
		{#each weeks as week, count}
			<Week startDate={week} selectedDate={selectedDate} />
		{/each}
	</tbody>
</table>