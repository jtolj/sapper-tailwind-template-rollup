<script>
  import Tailwind from "../components/Tailwind.svelte";
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<Tailwind />
<div class="max-w-screen-md mx-auto bg-white">

  <Nav {segment} />

  <main class="p-2 my-0 mx-auto box-border">
    <slot />
  </main>
</div>
