<script>
	import LinkButton from '$lib/components/LinkButton.svelte';
</script>

<svelte:head>
	<title>Zombie Pixel Runner · The Fun Website</title>
	<meta name="theme-color" content="#73ACE0" />
</svelte:head>

<section class="panel">
	<h1>Zombie Pixel Runner</h1>
	<p>
		This game lives on another site, and some browsers block direct embedding. Use the button below to
		open it in a fresh tab and jump right in.
	</p>

	<div class="actions primary-actions">
		<a
			href="https://everettmartin.github.io/My-Website/programiz-html-css/index.html"
			target="_blank"
			rel="noopener noreferrer"
			class="launch-button"
		>
			▶ Play Zombie Pixel Runner
		</a>
	</div>

	<div class="actions">
		<LinkButton href="/games" showarrow>More games</LinkButton>
	</div>
</section>

<style>
	.panel {
		width: min(1100px, 100%);
		background-color: rgba(255, 255, 255, 0.92);
		border: 4px solid var(--orange);
		border-radius: 28px;
		padding: clamp(20px, 4vw, 40px);
		text-align: center;
		box-shadow: 0 18px 50px rgba(20, 50, 100, 0.25);
		backdrop-filter: blur(2px);
	}

	h1 {
		margin: 0 0 12px;
		font-size: clamp(2rem, 6vw, 3rem);
		font-weight: 800;
		color: #2c3e50;
		letter-spacing: -0.5px;
	}

	p {
		margin: 0 0 24px;
		color: #34495e;
		line-height: 1.5;
	}

	.actions {
		display: flex;
		justify-content: center;
	}

	.primary-actions {
		margin-bottom: 16px;
	}

	.launch-button {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		padding: 12px 18px;
		border: 4px solid var(--orange);
		border-radius: 999px;
		background: var(--yellow);
		color: #111;
		font-weight: 800;
		text-decoration: none;
		transition: background 0.2s ease;
	}

	.launch-button:hover {
		background: var(--orange);
	}
</style>
