<script>
	export let posts = ["Hello!", "World!"];
	let text = '';

	function addText() {
		posts = [...posts, text];
	}
</script>

<style>
	ul {
		margin: 0 0 1em 0;
		line-height: 1.5;
	}
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>
<input type="text" bind:value={text} />
<button on:click={addText}>Add Post</button>

<ul>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<li><a rel='prefetch' href='blog/{post}'>{post}</a></li>
	{/each}
</ul>