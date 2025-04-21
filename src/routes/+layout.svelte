<nav id="navbar">
    <a href="/">Index</a>
    <a href="/counter">Counter</a>
    <a href="/tempconv">Temperature Converter</a>
    <a href="/flightbooker">Flight Booker</a>
    <a href="/timer">Timer</a>
    <a href="/crud">CRUD</a>
    <a href="/circledrawer">Circle Drawer</a>
    <a href="/cells">Cells</a>
</nav>

<hr>
  
<main>
    <slot />
</main>

<style>
    :global(html) {
        padding: 2rem 2rem 2rem 2rem;
    }
    #navbar {
        gap: 2rem;
    }

    main {
        padding-top: 2rem;
    }
</style>