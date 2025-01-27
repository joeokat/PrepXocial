<script lang="ts">
  import InstallButton from '$lib/InstallButton.svelte';

  let currentYear = new Date().getFullYear();
</script>

<section class="login--screen">
  <section class="login--container">
    <div class="login--caption">
      <img src="logo.svg" alt="logo" />
      <h1 class="login--title">Prep Xocial</h1>
      <h3 style="font-weight: 400; font-size: 16px;">
        Community based learning platform for Basic and Secondary Education
        Learners in West Africa.
      </h3>
    </div>

    <a class="subscribe-btn" href="/explore"> Explore Platform </a>

    <!-- Render the Install component -->
    <InstallButton />

    <a
      class="whatsapp-btn"
      href="https://whatsapp.com/channel/0029VaeRav7JuyAImX0dzq0N"
    >
      <img src="whatsapp.svg" alt="whatsapp" /> Announcements
    </a>
  </section>

  <div class="copyright">
    <h5 style="font-weight: 500;">
      Join the waitlist today and connect with learners in your province
    </h5>
    <h5 style="font-weight: 500;">
      Copyright &copy; {currentYear} Prep Xocial. All rights reserved
    </h5>
  </div>
</section>
