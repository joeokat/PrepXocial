<script>
	import { page } from '$app/stores';
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
</script>

{#if $page.url.pathname !== '/'}
	<Header />
{/if}

<slot />

{#if $page.url.pathname !== '/'}
	<Footer />
{/if}
