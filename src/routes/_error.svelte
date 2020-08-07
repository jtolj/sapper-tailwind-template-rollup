<script>
  export let status;
  export let error;

  const dev = process.env.NODE_ENV === "development";
</script>

<svelte:head>
  <title>{status}</title>
</svelte:head>

<h1 class="my-1 mx-auto text-xl md:text-2xl font-bold">{status}</h1>

<p class="my-1 mx-auto">{error.message}</p>

{#if dev && error.stack}
  <pre>{error.stack}</pre>
{/if}
