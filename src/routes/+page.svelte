<script>
	import Install from '$lib/Install.svelte';

	let currentYear = new Date().getFullYear();
</script>

<section class="login--screen">
	<section class="login--container">
		<div class="login--caption">
			<img src="logo.svg" alt="logo" />
			<h1 class="login--title">Prep Xocial</h1>
			<h3 style="font-weight: 500;">
				Social Ed-Tech Platform for Basic, Secondary & College School Learners
			</h3>
		</div>

		<a class="subscribe-btn" href="/explore"> Explore Platform </a>

		<!-- Render the Install component -->
		<Install />

		<a class="whatsapp-btn" href="https://whatsapp.com/channel/0029VaeRav7JuyAImX0dzq0N">
			<img src="whatsapp.svg" alt="whatsapp" /> Announcements
		</a>
	</section>

	<div class="copyright">
		<h5 style="font-weight: 500;">
			Join the waitlist today and connect with learners in your province
		</h5>
		<h5 style="font-weight: 500;">Copyright &copy; {currentYear} PrepX. All rights reserved</h5>
	</div>
</section>
