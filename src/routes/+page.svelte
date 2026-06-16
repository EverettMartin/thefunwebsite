<script>
	import ShortTextInput from '$lib/components/ShortTextInput.svelte';

	let email = $state('');
	let expandedFaqItem = $state(/** @type {number | null} */ (null));
	let showCatInfo = $state(false);
	let showStickynoteInfo = $state(false);

	// FAQ data — replace with your own questions and answers
	const faqData = [
		{
			question: 'What is The Fun Website?',
			answer: 'Placeholder answer. Tell visitors what The Fun Website is all about right here.'
		},
		{
			question: 'How do I get started?',
			answer: 'Placeholder answer. Explain how someone can jump in and start having fun.'
		},
		{
			question: 'Is it free?',
			answer: 'Placeholder answer. Let people know about pricing (or that it is free!).'
		},
		{
			question: 'Who is this for?',
			answer: 'Placeholder answer. Describe who will love The Fun Website.'
		},
		{
			question: 'Who made this?',
			answer: 'Placeholder answer. Add a little about the team behind The Fun Website.'
		}
	];

	/**
	 * @param {number} index
	 */
	function toggleFaqItem(index) {
		expandedFaqItem = expandedFaqItem === index ? null : index;
	}
</script>

<svelte:head>
	<title>The Fun Website</title>
	<meta property="og:title" content="The Fun Website" />
	<meta property="og:description" content="A placeholder description for The Fun Website." />
	<meta property="og:image" content="/ogimg.png" />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta property="og:type" content="website" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="The Fun Website" />
	<meta name="twitter:description" content="A placeholder description for The Fun Website." />

	<meta name="theme-color" content="#73ACE0" />
</svelte:head>

<main>
	<img class="corner-logo" src="logo.png" alt="The Fun Website logo" />

	<img class="logo-bg" src="hero.png" alt="The Fun Website" />

	<div class="login-inputs">
		<p style="color: white;">Welcome to The Fun Website — placeholder tagline goes here.</p>
		<ShortTextInput bind:value={email} placeholder="enter your email">get started</ShortTextInput>
	</div>

	<div class="sample-room">
		<img src="landing/sample room.png" class="room-bg" alt="" />

		<img
			src="landing/stickynote.png"
			class="room-stickynote"
			alt=""
			onmouseenter={() => (showStickynoteInfo = true)}
			onmouseleave={() => (showStickynoteInfo = false)}
		/>

		<div class="room-stickynote-info" class:visible={showStickynoteInfo}>
			<p style="color: white;">placeholder note text</p>
			<p style="color: white;">~ anonymous</p>
		</div>

		<img
			src="landing/cat.png"
			class="room-cat"
			alt=""
			onmouseenter={() => (showCatInfo = true)}
			onmouseleave={() => (showCatInfo = false)}
		/>

		<div class="room-cat-info" class:visible={showCatInfo}>
			<p style="color: white;">placeholder title</p>
			<p style="color: white;">placeholder description</p>
			<p style="color: white;">placeholder detail</p>
		</div>

		<img src="landing/makegames.png" class="room-makegames" alt="games" />
		<img src="landing/buildhouses.png" class="room-buildhouses" alt="puzzles" />
		<img src="landing/getprizes.png" class="room-getprizes" alt="quizzes" />
	</div>

	<div class="prizes-row">
		<img src="prizes/prize-1.png" alt="Prize one" class="prize-image" />
		<img src="prizes/prize-2.png" alt="Prize two" class="prize-image" />
		<img src="prizes/prize-3.png" alt="Prize three" class="prize-image highlight" />
		<img src="prizes/prize-4.png" alt="Prize four" class="prize-image" />
		<img src="prizes/prize-5.png" alt="Prize five" class="prize-image" />
	</div>

	<div class="faq-section">
		<h3>Have questions? We answer them!!!</h3>
		<div class="faq-list">
			{#each faqData as item, index}
				<div class="faq-item">
					<button class="faq-question" onclick={() => toggleFaqItem(index)}>
						<span>{item.question}</span>
						<span class="faq-arrow" class:expanded={expandedFaqItem === index}>▼</span>
					</button>

					{#if expandedFaqItem === index}
						<div class="faq-answer">
							<p>{item.answer}</p>
						</div>
					{/if}
				</div>
			{/each}
		</div>
	</div>

	<footer>
		<p>made with ❤️ by your team</p>
		<p>placeholder footer text — add credits or links here</p>
	</footer>
</main>

<style>
	footer {
		width: 100%;
		text-align: center;
		padding: 20px;
	}

	footer p {
		margin: 4px 0;
	}

	main {
		position: relative;
		width: 100%;
		background-color: #74ade1;
		min-height: 100%;

		padding-bottom: 24px;
	}

	.logo-bg {
		width: 100%;
		margin-bottom: -45%;
	}

	.corner-logo {
		position: absolute;
		top: 16px;
		left: 16px;
		width: min(90px, 18vw);
		height: auto;
		z-index: 10;
	}

	.login-inputs {
		width: 100%;
		display: flex;
		flex-flow: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.sample-room {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 80px;
		min-height: 50vw;
	}

	.sample-room img {
		position: absolute;
	}

	.sample-room .room-bg {
		width: 50vw;
		top: 0;
	}

	.sample-room .room-cat {
		width: 5vw;
		top: 70%;
		left: 52%;
	}

	.sample-room .room-stickynote {
		width: 5vw;
		top: 35%;
		left: 40%;
	}

	.room-cat,
	.room-stickynote {
		transition: filter 0.2s;
	}

	.room-cat-info {
		position: absolute;
		display: none;

		background-color: white;

		top: 60%;
		left: 50%;
	}

	.room-cat-info p {
		margin: 0;
		font-size: 0.8em;
	}

	.room-cat-info.visible {
		display: block;
	}

	.room-stickynote-info {
		position: absolute;
		display: none;

		background-color: white;
		top: 29%;
		left: 38%;
	}

	.room-stickynote-info p {
		margin: 0;
		font-size: 0.8em;
	}

	.room-stickynote-info.visible {
		display: block;
	}

	.room-circle-info.makegames {
		position: absolute;
		top: 2%;
		left: 21%;
	}

	.room-makegames {
		height: 15vw;
		top: 5%;
		left: 16%;
	}

	.room-text {
		text-align: center;
		position: absolute;
		alignment-baseline: middle;
	}

	.room-text.room-makegames {
		transform: translateX(-50%) translateY(-50%);
		top: 19%;
		left: 30%;
	}

	.room-buildhouses {
		height: 15vw;
		top: 40%;
		left: 5%;
	}

	.room-text.room-buildhouses {
		transform: translateX(-50%) translateY(-50%);
		top: 55%;
		left: 12.5%;
	}

	.room-getprizes {
		height: 15vw;
		top: 72.5%;
		left: 20%;
	}

	.room-text.room-getprizes {
		transform: translateX(-50%) translateY(-50%);
		top: 86.5%;
		left: 26.5%;
	}

	.prizes-row {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-top: 40px;
		max-width: 100vw;
		box-sizing: border-box;
		margin-left: calc(-50vw + 50%);
		overflow-x: hidden;
		padding-top: 15px;
		padding-bottom: 15px;
	}

	.prize-image {
		height: 15vw;
		width: auto;
		object-fit: contain;
		margin-left: -5vw;
		flex: 1;
		animation: bounce 2s ease-in-out infinite;
	}

	.prize-image.highlight {
		height: 23vw;
	}

	.prize-image:first-child {
		margin-left: 0;
		animation-delay: 0s;
	}

	.prize-image:nth-child(2) {
		animation-delay: 0.2s;
	}

	.prize-image:nth-child(3) {
		animation-delay: 0.4s;
	}

	.prize-image:nth-child(4) {
		animation-delay: 0.6s;
	}

	.prize-image:nth-child(5) {
		animation-delay: 0.8s;
	}

	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-10px);
		}
	}

	.faq-section {
		margin: 40px 20px;
		padding: 32px;
		text-align: center;
	}

	.faq-section h3 {
		margin: 0 0 24px 0;
		color: #2c3e50;
		font-size: 24px;
		font-weight: 700;
		letter-spacing: -0.5px;
	}

	.faq-list {
		text-align: left;
		max-width: 600px;
		margin: 0 auto;
	}

	.faq-item {
		margin-bottom: 0;
	}

	.faq-item:last-child {
		border-bottom: none;
	}

	.faq-question {
		width: 100%;
		background: none;
		border: none;
		padding: 20px 16px;
		text-align: left;
		cursor: pointer;
		display: flex;
		justify-content: space-between;
		align-items: center;
		color: #2c3e50;
		font-size: 1em;
		font-family: inherit;
		font-weight: 600;
		line-height: 1.4;
	}

	.faq-question:hover {
		color: #1a252f;
	}

	.faq-arrow {
		transition: transform 0.2s;
		font-size: 14px;
		color: #435b89;
		margin-left: 12px;
		flex-shrink: 0;
	}

	.faq-arrow.expanded {
		transform: rotate(180deg);
	}

	.faq-answer {
		padding: 0 16px 20px 16px;
		color: #34495e;
		line-height: 1.6;
		font-size: 1em;
		font-family: inherit;
	}

	.faq-answer p {
		margin: 0;
		font-weight: 400;
	}

	.login-inputs :global(button) {
		cursor: pointer;
	}
</style>
