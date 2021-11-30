<script>
	import Month from './Month.svelte';
	//import { onMount } from 'svelte';
	//import { google } from 'googleapis';

	const selectedDate = new Date(2021, 10, 1);
	const defaultEvents = [
		{
			name: "Test 1",
			start: new Date(2021,10,1,10,30,0),
			end: new Date(2021,10,1,11,0,0),
		},
		{
			name: "Test 2",
			start: new Date(2021,10,24,10,30,0),
			end: new Date(2021,10,24,11,0,0),
		},
		{
			name: "Test 3",
			start: new Date(2021,10,24,11,30,0),
			end: new Date(2021,10,24,12,0,0),
		},
		{
			name: "Test 1",
			start: new Date(2021,10,1,10,30,0),
			end: new Date(2021,10,1,11,0,0),
		},
		{
			name: "Test 2",
			start: new Date(2021,10,24,10,30,0),
			end: new Date(2021,10,24,11,0,0),
		},
		{
			name: "Test 3",
			start: new Date(2021,10,24,11,30,0),
			end: new Date(2021,10,24,12,0,0),
		},
	];


	let events = [];
	// const cachedEvents = 'localStorage' in window ? localStorage.getItem('events') : null;
	// if (cachedEvents) {
	// 	events = JSON.parse(cachedEvents).map(e => { return { name: e.name, start: new Date(e.start), end: new Date(e.end)}});
	// } 
	
	const client_id = "1007028032280-v14ggigd5grqjfdg3vrs2k26ocavh6sm.apps.googleusercontent.com";
	const client_secret = "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";
	const redirect_uris = ["urn:ietf:wg:oauth:2.0:oob","http://localhost"];

	function getToken() {
		return {"access_token":"ya29.a0ARrdaM_hj59PbTmklD5D9-AQnKDeghrLHXc_OKXoHKTxOqTPaurhGbmg4Z6Ds8_MxWi_gnTZEAxTlDpSM1F44AKa_NcxzKJHW2J7dIbI2tEcMtXDfMZqE_sbFDR127JstwnVxAKRMepQWEVRO-005qq-Xf0d","refresh_token":"1//060Q_-n-AGi7gCgYIARAAGAYSNgF-L9IrhdMK3BOcfuZ7WvKhYpLDF91Ng7-ihnlBbW29hx2Ms_9bwLPUjqe3K1hAIFb9iF9q4w","scope":"https://www.googleapis.com/auth/calendar.readonly","token_type":"Bearer","expiry_date":1638289200682};
	};

	// fetchEvents( (date) => {
	// 	const oAuth2Client = new google.auth.OAuth2(client_id, client_secret, redirect_uris[0]);
	// 	oAuth2Client.setCredentials(getToken());
	// 	const calendar = google.calendar({version: 'v3', oAuth2Client});
	// 	calendar.events.list({
	// 		calendarId: 'primary',
	// 		timeMin: (new Date()).toISOString(),
	// 		maxResults: 10,
	// 		singleEvents: true,
	// 		orderBy: 'startTime',
	// 	}, (err, res) => {
	// 		if (err) return console.log('The API returned an error: ' + err);
	// 		const googleEvents = res.data.items;
	// 		if (googleEvents.length) {
	// 			console.log('Upcoming 10 events:');
	// 			events = googleEvents.map((event, i) => {
	// 				const start = event.start.dateTime || event.start.date;
	// 				console.log(`${start} - ${event.summary}`);
	// 				return { name: event.summary, start: new Date(event.start), end: new Date(event.end)};
	// 			});
	// 		} else {
	// 			console.log('No upcoming events found.');
	// 		}
	// 	});
	// });

	// onMount(async () => {
	// 	const res = await fetch(`https://jsonplaceholder.typicode.com/photos?_limit=20`);
	// 	const photos = await res.json();
	// 	events = await photos.map( (p,i) => { return {
	// 		name: p.title.split(' ')[0],
	// 		start: new Date(2021,10,i+1,11,30,0),
	// 		end: new Date(2021,10,i+1,12,0,0),
	// 	}});
	// });
</script>

<Month selectedDate={selectedDate} events={events}/>