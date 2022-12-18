<script>
    import Hamburger from "./Hamburger.svelte";
    import { clickOutside } from "../scripts/clickOutside";
    let checked = false;
    function toggle() {
        checked = !checked;
    }
    function clickAway() {
        if (checked) {
            checked = false;
        }
    }
    const links = [
        { url: "/", title: "Home" },
        { url: "/poetry", title: "Poetry" },
        { url: "/essays", title: "Essays" },
        { url: "/philosophy", title: "Philosophy" },
    ];
</script>

<header class="header">
    <div class="logo-center">
        <a class="logo" href="/">ST</a>
    </div>
    <Hamburger class="ham" on:click={toggle} />
    <nav class={`${checked ? 'nav-open' : ''} nav`} use:clickOutside on:click_outside={clickAway}>
        <div class="close-container">
            <button class="close-button" on:click={clickAway}>
                <div class="cross-one">
                    <div class="cross-two" />
                </div>
            </button>
        </div>
        <ul class="menu">
            {#each links as link}
                <li>
                    <a href={link.url}>
                        {link.title}
                    </a>
                </li>
            {/each}
        </ul>
    </nav>
</header>

<style>
    .header {
        display: flex;
        justify-content: space-between;
        background-color: var(--black);
        box-shadow: 1px 1px 5px 0px var(--gray);
        position: sticky;
        top: 0;
        width: 100%;
        padding: 0 15px 0 15px;
    }
    .logo {
        display: inline-block;
        color: var(--white);
        font-size: 30px;
    }
    .logo-center {
        display: inline-flex;
        align-items: center;
    }

    .menu li {
        font-size: 20px;
        display: block;
        padding: 15px;
    }
    .menu a {
        color: var(--black);
    }

    .menu li:first-child {
        padding-top: 0;
    }
    
    .menu a:hover {
        background-color: var(--gray);
    }

    .nav {
        width: 80%;
        height: 100%;
        position: fixed;
        right: 0;
        overflow: hidden;
        background-color: white;
        max-width: 0;
        transition: max-width 0.3s ease-out;
    }

    .show-nav {
        visibility: hidden;
        display: none;
    }

    .nav.nav-open {
        max-width: 100%;
    }

    .close-container {
        width: 80vw;
        display: flex;
        justify-content: right;
        padding: 30px 30px 0 0;
    }

    .close-button {
        background: none;
        color: inherit;
        border: none;
        padding: 0;
        font: inherit;
        cursor: pointer;
        outline: inherit;
        width: 25px;
        height: 25px;
    }

    .cross-one {
        height: 25px;
        width: 2px;
        margin-left: 12px;
        background-color: black;
        transform: rotate(45deg);
        z-index: 1;
    }

    .cross-two {
        height: 25px;
        width: 2px;
        background-color: black;
        transform: rotate(90deg);
        z-index: 2;
    }

    @media screen and (min-width: 801px) {
        :global(.ham) {
            
            display: none !important;
        }

        .header {
            min-height: 100%;
            align-items: stretch;
            justify-content: left;
        }

        .nav {
            height: auto;
            background-color: transparent;
            max-width: 100%;
            position: static;
        }

        .logo-center {
            margin-right: 20px;
        }

        .close-container {
            display: none;
        }

        .menu {
            display: flex;
            align-items: stretch;
            justify-content: left;
            height: auto;
            height: 100%;
        }

        .menu li {
            display: flex;
            align-items: stretch;
            color: white;
            padding: 0;
            height: 100%;
        }

        .menu a {
            font-size: 15px;
            color: white;
            display: flex;
            padding: 0 10px 0 10px;
            align-items: center;
        }
    }
</style>
