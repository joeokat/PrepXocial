<script>
  import '../styles/app.css';
  import '../styles/card.css';

  import { page } from '$app/stores';
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  const showHeaderFooter = $page.url.pathname !== '/';
</script>

{#if showHeaderFooter}
  <Header />
{/if}

<slot>
  <p>Sorry, the issue is from us not you.</p>
</slot>

{#if showHeaderFooter}
  <Footer />
{/if}

<!-- <main>
  <p>testing page load</p>
</main> -->
