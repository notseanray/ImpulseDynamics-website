<script>
	import { page } from '$app/stores';
	import logo from '$lib/images/svelte-logo.svg';
	import github from '$lib/images/github.svg';
</script>

<header>

	<nav>
		<ul>
            <div class="corner">
                <a href="https://kit.svelte.dev">
                    <img src={logo} alt="SvelteKit" />
                </a>
            </div>
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

<!-- hamburger -->
<div class="sep-line" />
</header>

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
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}

    .sep-line {
        border: 10px solid green;
        color: #ffffff;
    }
</style>
