<script context="module">
	export async function load({ fetch }) {
		const res = await fetch('/posts.json');
		if (res.ok) {
			const posts = await res.json();
			return { props: posts };
		}
	}
</script>

<script>
	export let posts;
</script>

<svelte:head>
	<title>Teddy's Jamstack Conf Blog</title>
</svelte:head>

<ul>
	{#each posts as post}
		<li class="card text-center shadow-2xl mb-20">
			<figure class="px-10 pt-10">
				{#if post.coverImage.url}
					<img src={post.coverImage.url} alt={post.title} />
				{:else}
					<img src={`/default-cover-image.jpg`} alt="default cover image" />
				{/if}
				<h2 class="title font-bold text-2l mb-2">
					{post.title}
				</h2>
				<p class="mb-2">{post.excerpt}</p>
				<div>
					{#if post.tags}
						{#each post.tags as tag}
							<span class="badge badge-primary">{tag}</span>
						{/each}
					{/if}
				</div>
				<div class="my-2">
					<a href={`/posts/${post.slug}`} class="btn">Read &rArr</a>
				</div>
			</figure>
		</li>
	{/each}
</ul>
