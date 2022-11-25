<script>
	let firstname = 'Bree';
	let lastname = 'Armstrong'
	let showText = false;

	let posts = [
		{
			title: 'How I made an app',
			link: "https://www.google.com"
		},
		{
			title: 'This is blog post 2',
			link: 'https://www.youtube.com'
		},
		{
			title: 'This is blog post 3',
			link: 'https://www.medium.com'
		},
	]

	let color = 'purple'

	//Reactive value
	$: name = firstname + ' ' + lastname

	const toggle = () => {
		color = color === 'purple' ? 'blue' : 'purple'
		showText = !showText;
		posts = [...posts, {title: 'Blog post 4', link: 'https://linkedin.com'}]
	}
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
	<p>It's nice to see you!</p>
	{/if}
	<button on:click={toggle}>Click</button>
	{#each posts as post (post.link)}
	<a href="{post.link}"><h2>{post.title}</h2></a>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>