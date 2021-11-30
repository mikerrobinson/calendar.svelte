<script>
	import calendarHelper from './calendarHelper';

	export let selectedDate = new Date();
    export let firstDayOfWeek = 0;
	export let events = [];
    const monthName = new Date(selectedDate.getFullYear(), selectedDate.getMonth(), 1).toLocaleString('default', { month: 'long', year: 'numeric' });
    const weeksInMonth = calendarHelper(selectedDate);
    const dayNames = Array.from(Array(7), (_, i) => new Date(2000,0,2 + firstDayOfWeek + i).toLocaleString('default', { weekday: 'short' }));

	function isSameDay(d1, d2) {
		return d1.getFullYear() === d2.getFullYear() &&
		d1.getDate() === d2.getDate() &&
		d1.getMonth() === d2.getMonth();
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

	.spacer {
		background: #ddd;
	}

	td {
		text-align: left;
		vertical-align: top;
		position: relative;
		overflow: hidden;
	}

    .event-list {
	  display: inline;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      list-style: none;
      margin-block-start: 0;
      margin-block-end: 0;
      margin-inline-start: 1em;
      margin-inline-end: 0;
      padding-inline-start: 0;
    }

    .event {
      margin: 8px;
      padding: 4px;
      background: lightblue;
    }
</style>

<table class="monthly calendar">
  <thead>
    <tr>
      <th colspan="7">{monthName}</th>
    </tr>
    <tr>
		{#each dayNames as dayName}
			<td>{dayName}</td>
		{/each}
    </tr>
  </thead>
  <tbody>
		{#each weeksInMonth as week}
			<tr class="week">
				{#each week as day}
					<td class="day {day.getMonth() === selectedDate.getMonth() ? "" : "spacer"}">
						<span>{day.getDate()}</span>
						<ul class="event-list">
							{#each (events.filter(event => isSameDay(event.start, day)) || []) as event}
								<li class="event">{event.name}</li>	
							{/each}
						</ul>
					</td>
				{/each}
			</tr>
		{/each}
	</tbody>
</table>