<script lang="ts">
	import './global.css';
	import { active } from 'svu/action';
</script>

<header>
	<h1><code>/svu-demo</code></h1>
	<p>
		🎪 Showcasing a few features of <code><a href="https://svu.vercel.app/">/svu</a></code>.
	</p>

	<nav>
		<ul>
			<li><a href="/" use:active>Home</a></li>
			<li><a href="/about" use:active>About</a></li>
			<li><a href="/contact" use:active>Contact</a></li>
		</ul>
	</nav>

	<p>
		👆 These nav links use the <code>
			<a href="https://svu.vercel.app/docs/action/active">use:active</a>
		</code> action to highlight the link to the current page.
	</p>
</header>

<main>
	<slot />
</main>

<style>
	h1,
	p {
		text-align: center;
	}

	ul {
		all: unset;
		display: flex;
		flex-direction: row;
		justify-content: space-between;

		margin: 2rem;
	}

	li {
		all: unset;
		background-color: aliceblue;
		padding: 0 1rem;
	}

	header,
	main {
		width: 80%;
		max-width: 800px;
		margin: 0 auto;
		padding: 2rem;
	}
</style>
