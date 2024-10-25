<script>
    // import Header from "$lib/components/Header.svelte";
</script>

<header>
    <div class="header--bar">
        <img src="/logo.svg" alt="logo">
        <button onclick = "showSidebar()" class="svg-icon">
            <img src="/menu-icon.svg" alt="menu icon">
        </button>
    </div>

    <nav class="side--menu">
        <button onclick="hideSidebar()" id="close" class="svg-icon">
            <img src="/close-icon.svg" alt="menu icon">
        </button>
        <ul>                   
            <li><a href="../explore"> What's New </a></li>
            <li><a href="../lessonNotes"> Study Help </a></li>
            <li><a href="../revision"> Revision </a></li>
            <li><a href="https://whatsapp.com/channel/0029VaeRav7JuyAImX0dzq0N"> Career </a></li>  
            <li><a href="../jobAlert">People Nearby </a></li>            
            <li><div class="cta--telegram"><a class="telegram-btn" href="https://t.me/prepxconsult"> Community <img src="/telegram.svg" alt="telegram"> </a></div></li>
        </ul>
    </nav>
</header>