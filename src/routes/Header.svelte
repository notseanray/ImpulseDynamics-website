<script>
	import { page } from '$app/stores';
	import logo from '$lib/images/svelte-logo.svg';
    import { onMount, onDestroy } from "svelte";
	import github from '$lib/images/github.svg';
    import { browser } from '$app/environment';
    let menuOpen = false;
    const MOBILE_WIDTH = 800;
    let mobile = false;
    if (browser) {
        mobile = innerWidth < MOBILE_WIDTH;
        onMount(() => {
            window.addEventListener("resize", handleResize)
        })
        onDestroy(() => {
            window.removeEventListener("scroll", handleResize);
        })
        const handleResize = (e) => {
            mobile = innerWidth < MOBILE_WIDTH;
        }
        const debounce = (fn, interval) => {
            let timer;
            return function debounced(...args) {
                clearTimeout(timer);
                timer = setTimeout(function call() {
                    fn(...args);
                }, interval);
            };
        };
    }
</script>

<header>

	<nav>
		<ul>
            {#if !mobile}
                <div class="corner">
                    <a href="https://kit.svelte.dev">
                        <img src={logo} alt="SvelteKit" />
                    </a>
                </div>
            {/if}
			<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">About</a>
			</li>
			<li aria-current={$page.url.pathname === '/Partners' ? 'page' : undefined}>
				<a href="/partners">Partners</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('/products') ? 'page' : undefined}>
				<a href="/products">Products</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('/resources') ? 'page' : undefined}>
				<a href="/resources">Resources</a>
			</li>
		</ul>
	</nav>

    {#if !mobile}
<!-- hamburger -->
        <div class="navbar">
            <div class="container nav-container mb-10">
                <input
                    bind:checked={menuOpen}
                    class="checkbox"
                    type="checkbox"
                    name=""
                    id=""
                />
                <div class="hamburger-lines">
                    <span class="line line1" />
                    <span class="line line2" />
                    <span class="line line3" />
                </div>
                <div class="menu-items font-bold rounded-md">
                    <a class="p-2 hover:underline" on:click={() => menuOpen = false} href="/">Home</a>
                    <br />
                    <a class="p-2 hover:underline" on:click={() => menuOpen = false} href="/legal">Legal</a>
                </div>
            </div>
        </div>
    {/if}
</header>
<div class="sep-line" />

<style>
	header {
		display: flex;
		justify-content: space-between;
        width: 100vw;
	}

	.corner {
        left: 1.5em;
        position: absolute;
		width: 3em;
		height: 3em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	nav {
        width: 100vw;
		display: flex;
		justify-content: center;
		--background: #eb5060;
	}

	svg {
		width: 2em;
		height: 3em;
		display: block;
	}

	path {
		fill: var(--background);
	}

	ul {
        width: 100vw;
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	li[aria-current='page']::before {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid #ffffff;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: #ffffff;
		font-weight: 700;
		font-size: 0.7vw;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}

    .sep-line {
        border: 2px solid #c9c9c9;
    }
    .nav-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .navbar .menu-items {
        z-index: 10;
        display: flex;
    }
    .navbar .nav-container li {
        list-style: none;
    }
    .navbar .nav-container a {
        text-decoration: none;
        color: #fff;
        font-weight: 500;
        font-size: 1.2rem;
        padding: 0.7rem;
    }
    .navbar .nav-container a:hover {
        font-weight: bolder;
    }
    .nav-container {
        display: block;
    }
    .nav-container .checkbox {
        position: absolute;
        right: 20px;
        display: block;
        height: 32px;
        width: 32px;
        top: 20px;
        z-index: 500;
        opacity: 0;
        cursor: pointer;
    }
    .nav-container .hamburger-lines {
        display: block;
        height: 26px;
        width: 32px;
        position: absolute;
        top: 17px;
        right: 20px;
        z-index: 2;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .nav-container .hamburger-lines .line {
        display: block;
        height: 4px;
        width: 100%;
        border-radius: 10px;
        background: #fff;
    }
    .nav-container .hamburger-lines .line1 {
        transform-origin: 0% 0%;
        transition: transform 0.4s ease-in-out;
    }
    .nav-container .hamburger-lines .line2 {
        transition: transform 0.2s ease-in-out;
    }
    .nav-container .hamburger-lines .line3 {
        transform-origin: 0% 100%;
        transition: transform 0.4s ease-in-out;
    }
    .navbar .menu-items {
        box-shadow: inset 00 2000px rgba(0, 0, 0, 0.8);
        margin-top: 120px;
        height: fit-content;
        min-width: 200px;
        width: 20vw;
        transform: 50vw;
        display: flex;
        flex-direction: column;
        transition: transform 0.3s ease-in-out;
        text-align: center;
        position: fixed;
        margin-right: 0px;
    }
    .navbar .menu-items li {
        margin-bottom: 1.2rem;
        font-size: 1.5rem;
        font-weight: 500;
    }
    .nav-container input[type="checkbox"]:checked ~ .menu-items {
        transform: translateX(-150%);
    }
    .nav-container input[type="checkbox"]:checked ~ .hamburger-lines .line1 {
        transform: rotate(45deg);
    }
    .nav-container input[type="checkbox"]:checked ~ .hamburger-lines .line2 {
        transform: scaleY(0);
    }
    .nav-container input[type="checkbox"]:checked ~ .hamburger-lines .line3 {
        transform: rotate(-45deg);
    }
</style>
