<script lang="ts">
	import { Select, Label, Input, Button, Toggle, P, DarkMode, Tooltip } from 'flowbite-svelte';

	let selected = $state('feat');
	let commitTypes = [
		{ value: 'build', name: 'build' },
		{ value: 'ci', name: 'ci' },
		{ value: 'chore', name: 'chore' },
		{ value: 'docs', name: 'docs' },
		{ value: 'feat', name: 'feat' },
		{ value: 'fix', name: 'fix' },
		{ value: 'perf', name: 'perf' },
		{ value: 'refactor', name: 'refactor' },
		{ value: 'revert', name: 'revert' },
		{ value: 'style', name: 'style' },
		{ value: 'test', name: 'test' }
	];
	let message = $state('');
	let context = $state('');
	let postfix = $state('');
	let breaking = $state(false);
	const commitMessage = () => {
		let type = selected;
		if (context === '') {
			type = breaking ? `${type}!` : type;
			return `${type}: ${message} ${postfix}`;
		}
		type = breaking ? `${type}(${context})!` : `${type}(${context})`;
		return `${type}: ${message} ${postfix}`;
	};

	function copyToClipboard() {
		navigator.clipboard.writeText(commitMessage().trimEnd());
	}
</script>

<form>
	<div class="flex justify-end m-5">
		<DarkMode
			class="text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2"
		/>
		<Tooltip>Toggle dark mode</Tooltip>
	</div>
	<div class="m-auto flex w-[80%] items-center space-x-2 mt-10">
		<div class="flex flex-col" style="width: 20%;">
			<P class="mb-2">Select commit type*:</P>
			<Select id="countries" bind:value={selected} placeholder="">
				{#each commitTypes as { value, name }}
					<option {value}>{name}</option>
				{/each}
			</Select>
		</div>
		<div class="flex flex-col" style="width: 20%;">
			<P class="mb-2">Enter the context:</P>
			<Input type="text" id="context" bind:value={context} placeholder="Context..." />
		</div>
		<div class="flex flex-col" style="width: 40%;">
			<P class="mb-2">Enter the commit message*:</P>
			<Input type="text" bind:value={message} id="message" placeholder="Commit message..." />
		</div>
		<div class="flex flex-col" style="width: 20%;">
			<P class="mb-2">Postfix:</P>
			<Input type="text" id="postfix" bind:value={postfix} placeholder="Postfix" />
		</div>
		<Toggle class="mt-4" color="red" bind:checked={breaking}>Breaking change</Toggle>
		<Button class="mt-4" on:click={copyToClipboard}>Copy</Button>
	</div>
	<div class="m-auto mt-4 w-[80%]">
		<P class="text-left text-sm">* required</P>
		<P class="text-center">Your commit message will be:</P>
		<P class="text-center text-xl">{commitMessage()}</P>
	</div>
</form>

<style scoped>
	.clabel {
		font-size: 1.2rem;
		margin-bottom: 2px;
		color: red;
	}
</style>
