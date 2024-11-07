<script>
	import { LinkHandler } from '$lib/LinkHandler';
	import {
		Navbar,
		NavBrand,
		NavLi,
		NavUl,
		NavHamburger,
		Button,
		Input,
		DarkMode
	} from 'flowbite-svelte';
	import { Search } from 'lucide-svelte';
</script>

<Navbar>
	<NavBrand href={LinkHandler('/')}>
		<svg
			xmlns="http://www.w3.org/2000/svg"
			width="32"
			height="32"
			viewBox="0 0 24 24"
			fill="none"
			stroke="currentColor"
			stroke-width="2"
			stroke-linecap="round"
			stroke-linejoin="round"
			class="lucide lucide-git-commit-vertical stroke-gray-500 dark:stroke-white"
			><path d="M12 3v6" /><circle cx="12" cy="12" r="3" /><path d="M12 15v6" /></svg
		>
		<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white"
			>ConventionalFighter</span
		>
	</NavBrand>
	<div class="flex md:order-2">
		<Button
			color="none"
			data-collapse-toggle="mobile-menu-3"
			aria-controls="mobile-menu-3"
			aria-expanded="false"
			class="md:hidden text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 rounded-lg text-sm p-2.5 me-1"
		>
			<Search class="w-5 h-5" />
		</Button>

		<div class="hidden relative md:block">
			<div class="flex absolute inset-y-0 start-0 items-center ps-3 pointer-events-none">
				<Search class="w-4 h-4" />
			</div>
			<Input id="search-navbar" class="ps-10" placeholder="Search..." />
		</div>

		<NavHamburger />
		<DarkMode class="ml-2" />
	</div>
	<NavUl>
		<NavLi href={LinkHandler('/')}>Home</NavLi>
		<!--
		<NavLi href="/about">About</NavLi>
		<NavLi href="/docs/components/navbar">Navbar</NavLi>
    -->
	</NavUl>
</Navbar>
