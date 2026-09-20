<script>
	import "../../app.css";
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';
	import { page } from '$app/stores';
	
	$: currentPath = $page.url.pathname;

	const isMobile = writable(false);
	let mounted = false;

	onMount(() => {
		const checkMobile = () => {
			isMobile.set(window.innerWidth <= 768);
		};

		checkMobile();
		mounted = true;

		window.addEventListener('resize', checkMobile);

		return () => {
			window.removeEventListener('resize', checkMobile);
		};
	});
</script>

{#if !mounted}
	<div class="loading-screen">
		<p>Loading...</p>
	</div>
{:else if $isMobile}
	<div class="nav">
		<a href="/">
			<img class="logo-small" src="/CL-heart.png" alt="home">
		</a>
	</div>
{:else}
	<div class="nav">
		<a href="/">
			<img class="logo" src="/CL-heart.png" alt="home">
		</a>
	</div>
{/if}

<div class="container">
	<slot></slot>
</div>

<style>
	:root {
		--primary: #290217;
		--secondary: #420422;
		font-family: 'Lexend', sans-serif;
		line-height: 1.5;
		font-weight: 400;

		color-scheme: light dark;
		color: rgba(255, 255, 255, 0.87);
		background-color: var(--primary);

		font-synthesis: none;
		text-rendering: optimizeLegibility;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	.logo {
		display: block;
		width: 96px; /* or 80px if you prefer */
		height: auto;
		margin: 0;
	}

	.logo-small {
		display: block;
		width: 64px;
		height: auto;
		margin: 0;
	}

	.nav {
		align-items: center;
		justify-content: center;
	}

    .loading-screen {
        display: flex;
        justify-content: center;
        align-items: center; 
        height: 100vh;
        width: 100vw;
        font-size: 1.5rem;
        font-weight: bold;
    }
</style>