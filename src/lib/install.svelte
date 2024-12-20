<script>
	let deferredPrompt;
	let isInstalled = false;

	import { onMount } from 'svelte';

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

<a class="telegram-btn" id="installLink" href=" " style="display: {isInstalled ? 'none' : 'flex'};">
	<img src="download.svg" alt="install" /> Install web app
</a>
