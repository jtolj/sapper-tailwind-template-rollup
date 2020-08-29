
<svelte:head>
    <title>{post.title}</title>
</svelte:head>

<div class="container mx-auto">
    <div class="lg:flex lg:justify-center">
        <article class="lg:w-3/5">
            <header class="mt-8">
				<span><a href="/blog">&laquo; Back</a></span>
                <h1 class="text-5xl font-bold leading-snug lg:text-6xl">{post.title}</h1>
                <div class="flex items-center mt-6 lg:mt-6">
					<img class="w-6 h-6 rounded-full" src="//placehold.it/150x150.png" alt="A small me.">
						<span class="ml-2 text-gray-500 high-contrast-grey">{ post.author ? post.author : 'Jesse' } &mdash;
						<time pubdate="pubdate" datetime="{post.printDate}">{post.printDate}</time> | {post.printReadingTime}
						</span>
					</div>
            </header>
            <main role="main" class="mt-8 prose lg:mt-12">
                {@html post.html}
            </main>
        </article>
    </div>
</div>

<script context="module">
    export async function preload({ params, query }) {
        const res = await this.fetch(`blog/${params.slug}.json`);
        const data = await res.json();
        if (res.status === 200) {
            return { post: data };
            } else {
                this.error(res.status, data.message);
            }
        }
</script>

<script>
    export let post;
    import "prismjs/themes/prism.css";
    import "prismjs/themes/prism-okaidia.css";
</script>
