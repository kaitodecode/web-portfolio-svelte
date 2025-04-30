<script lang="ts">
	import { onMount } from 'svelte';

	let isMenuOpen = false;
	let isPinned = false;
	let isVisible = true;
	let lastScrollY = 0;
	let scrollTimeout: ReturnType<typeof setTimeout>;
	let navElement: HTMLUListElement;
	let menuButton: HTMLButtonElement;

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	function togglePin() {
		isPinned = !isPinned;
		if (isPinned) isVisible = true;
	}

	function handleScroll() {
		if (isPinned) return;

		const currentScrollY = window.scrollY;
		// Menghilangkan navbar untuk semua arah scroll
		isVisible = false;
		lastScrollY = currentScrollY;

		// Reset timer
		clearTimeout(scrollTimeout);
		scrollTimeout = setTimeout(() => {
			if (!isPinned) isVisible = true;
		}, 1500);
	}

	onMount(() => {
		window.addEventListener('scroll', handleScroll);
		return () => {
			window.removeEventListener('scroll', handleScroll);
			clearTimeout(scrollTimeout);
		};
	});
</script>

<nav
	class="fixed left-1/2 z-50 w-full -translate-x-1/2 transition-transform duration-300 ease-in-out md:w-auto"
	class:translate-y-full={!isVisible}
	style="bottom: 2.5rem;"
>
	<!-- Mobile menu button -->
	<button
		class="fixed right-4 bottom-20 z-50 rounded-full bg-slate-300/70 p-2 shadow-lg backdrop-blur-sm transition-colors duration-300 hover:bg-slate-300/90 md:hidden"
		on:click={toggleMenu}
		aria-label="Toggle menu"
	>
		{#if isMenuOpen}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="h-6 w-6"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M6 18L18 6M6 6l12 12"
				/>
			</svg>
		{:else}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="h-6 w-6"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M4 6h16M4 12h16M4 18h16"
				/>
			</svg>
		{/if}
	</button>

	<!-- Navigation menu -->
	<div class="relative w-full md:w-auto" role="navigation" aria-label="Main menu">
		<ul
			role="menu"
			bind:this={navElement}
			class="fixed right-4 bottom-20 left-4 z-40 flex flex-col
            items-center justify-center space-y-2 rounded-3xl bg-slate-300/70 p-4 shadow-lg backdrop-blur-sm
            transition-colors duration-300 hover:bg-slate-300/90 md:relative md:right-auto md:bottom-2 md:left-auto md:flex-row md:space-y-0
            md:space-x-8 md:rounded-full md:px-10"
			class:hidden={!isMenuOpen}
			class:md:flex={true}
		>
			{#each [{ text: 'Beranda', path: '/' }, { text: 'Tentang Saya', path: '/about' }, { text: 'Proyek & Pencapaian', path: '/project' }, { text: 'Artikel', path: '/blog' }, { text: 'Kontak', path: '/contact' }] as item}
				<li>
					<a
						href={item.path}
						class="block font-medium text-gray-700 transition-colors duration-200 hover:text-sky-600"
						on:click={() => (isMenuOpen = false)}
					>
						{item.text}
					</a>
				</li>
			{/each}
			<li>
				<!-- Pin button (visible only on md+) -->
				<button
					bind:this={menuButton}
					class="z-50 hidden  items-center justify-center rounded-full bg-slate-300/70 shadow-lg backdrop-blur-sm transition-colors duration-300 hover:bg-slate-300/90 md:flex"
					on:click={togglePin}
					aria-label="Pin navigation"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5 transition-transform duration-300"
						class:rotate-45={!isPinned}
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M5 5a2 2 0 012-2h10a2 2 0 012 2v16l-7-3.5L5 21V5z"
						/>
					</svg>
				</button>
			</li>
		</ul>
	</div>
</nav>

<style>
	.translate-y-full {
		transform: translate(0%, 100%);
	}
</style>
