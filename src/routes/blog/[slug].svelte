<script context="module">
  export async function preload({ params, query }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
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
</script>

<style>
  /*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
  .content :global(h2) {
    @apply text-lg;
    @apply font-medium;
  }

  .content :global(pre) {
    @apply bg-gray-200;
    @apply shadow-md;
    @apply p-1;
    @apply rounded;
    @apply overflow-x-auto;
  }

  .content :global(ul) {
    @apply leading-normal;
  }

  .content :global(p) {
    @apply pb-5;
  }

  .content :global(li) {
    @apply m-0;
    @apply mb-1;
  }
</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<h1 class="py-2 text-xl">{post.title}</h1>

<div class="content">
  {@html post.html}
</div>
