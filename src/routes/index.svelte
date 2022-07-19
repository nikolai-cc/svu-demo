<script lang="ts">
	import {
		clickoutside,
		copy,
		paste,
		download,
		draggable,
		keydown,
		keyup,
		onclose
	} from 'svu/action';

	import { mouse, dark } from 'svu/client';

	let clickedOutside = 0;
	let value = "🐠 It's lovely to see you here!";
	let result: HTMLElement;

	let dragMessage = "💩 Don't move me!";
	let respectMessage = 'click to select';
</script>

<h2 use:onclose>Actions</h2>

<p>
	This header has the onclose action applied. It will ask you to confirm to close the browser tab.
</p>

<h3>clickoutside</h3>
<div class="box" use:clickoutside={() => (clickedOutside += 1)}>
	You have clicked somewhere other than this box {clickedOutside} times.
</div>

<h3>copy & paste</h3>

<div class="container">
	<div class="box">
		<input bind:value id="input" />
		<button use:copy={'#input'}>copy text</button>
		<button use:paste={'#result'}>paste text</button>
	</div>

	<div class="box">
		<p id="result" bind:this={result}>Something will happen when you press copy, then paste.</p>
		<button use:download={{ target: result }}>download result</button>
	</div>
</div>

<h3>draggable</h3>

<div
	class="box"
	use:draggable
	on:drag:start={() => {
		dragMessage = "🤬 I said don't!";
	}}
	on:drag:end={() => {
		dragMessage = '😵‍💫';
		setTimeout(() => {
			dragMessage = "💩 Don't move me!";
		}, 1000);
	}}
>
	{dragMessage}
</div>

<h3>keydown / keyup</h3>

<div
	class="box"
	on:click={() => (respectMessage = '❤️‍🩹 Hold F to pay more respects.')}
	use:keydown={{ F: () => (respectMessage = '🖤') }}
	use:keyup={{ F: () => (respectMessage = '❤️‍🩹 Hold F to pay more respects.') }}
	tabindex="-1"
>
	{respectMessage}
</div>

<h2>Stores</h2>

<h3>Dark Mode</h3>

<div class="box">
	<p>
		{$dark ? '🌙' : '☀️'}
		{$dark
			? 'Your browser wants dark mode, but I havent made it yet'
			: "I'm glad your browser prefers light mode, it's all I've got."}
	</p>
</div>

<h3>Mouse</h3>

<div class="box">
	<p>
		🐁 I see you're at ({$mouse.x}, {$mouse.y}).
	</p>
</div>

<br />
<br />

<h2>& more...</h2>

<p>
	There is way more to discover at the <code><a href="https://svu.vercel.app">svu</a></code> documentation
</p>

<style>
	.box {
		background-color: var(--bg, aliceblue);
		padding: 2rem;
		border-radius: 2rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.container {
		display: flex;
		gap: 1rem;
	}
</style>
