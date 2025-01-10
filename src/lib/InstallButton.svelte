<!-- <script>
	import { onMount } from 'svelte';
	let deferredPrompt;
	let isInstalled = false;

	onMount(() => {
		// Check if the app is already installed
		const isInStandaloneMode = window.matchMedia('(display-mode: standalone)').matches;

		if (isInStandaloneMode) {
			isInstalled = true; // The app is installed
			return; // Exit early if installed
		}

		// Listen for the beforeInstallPrompt event
		window.addEventListener('beforeInstallPrompt', (e) => {
			e.preventDefault();
			deferredPrompt = e;
			document.getElementById('installLink').style.display = 'flex';
		});

		// Add click event listener for the install link
		const installLink = document.getElementById('installLink');
		installLink.addEventListener('click', async (event) => {
			installLink.style.display = 'none';
			event.preventDefault();
			if (deferredPrompt) {
				deferredPrompt.prompt();
				const { outcome } = await deferredPrompt.userChoice;
				console.log(`User  response to the install prompt: ${outcome}`);
				deferredPrompt = null;
			}
		});

		// Cleanup event listeners when the component is destroyed
		return () => {
			window.removeEventListener('beforeInstallPrompt', () => {});
			installLink.removeEventListener('click', () => {});
		};
	});
</script>

<a class="telegram-btn" id="installLink" href="/" style="display: {isInstalled ? 'none' : 'flex'};">
	<img src="download.svg" alt="install" /> Install Web App
</a> -->

<!-- I am still looking at how to fix this issue so once i find something that works i will update you. -->

<script lang="ts">
	import { onMount } from 'svelte';
	
	let deferredPrompt = null;
	let isInstalled = false;
	let showInstallButton = false;
	
	onMount(() => {
	  // Check if the app is already installed
	  isInstalled = window.matchMedia('(display-mode: standalone)').matches;
	
	  // Listen for the beforeInstallPrompt event
	  window.addEventListener('beforeInstallPrompt', (e) => {
		e.preventDefault();
		deferredPrompt = e;
		showInstallButton = true;
	  });
	
	  return () => {
		window.removeEventListener('beforeInstallPrompt', () => {});
	  };
	});
	
	async function handleInstallClick() {
	  if (!deferredPrompt) return;
	  
	  showInstallButton = false;
	  deferredPrompt.prompt();
	  
	  const { outcome } = await deferredPrompt.userChoice;
	  console.log(`User response to the install prompt: ${outcome}`);
	  deferredPrompt = null;
	}
	</script>
	
	{#if showInstallButton && !isInstalled}
	  <a 
		class="telegram-btn" 
		href="/" 
		on:click|preventDefault={handleInstallClick}
	  >
		<img src="download.svg" alt="install" /> 
		Install Web App
	  </a>
	{/if}