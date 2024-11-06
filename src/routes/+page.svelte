<script lang="ts">
	import { Select, Label, Input, Button } from 'flowbite-svelte';
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

	function copyToClipboard() {
		navigator.clipboard.writeText(`${selected}(${context}): ${message} ${postfix}`.trimEnd());
	}
</script>

<form>
	<div class="m-auto flex w-[80%] items-center space-x-2">
		<div class="flex flex-col items-start" style="width: 20%;">
			<Label for="countries">Select an option</Label>
			<Select id="countries" class="mt-2" bind:value={selected} placeholder="">
				{#each commitTypes as { value, name }}
					<option {value}>{name}</option>
				{/each}
			</Select>
		</div>
		<div class="flex flex-col items-start" style="width: 20%;">
			<Label for="context">Enter the context</Label>
			<Input type="text" id="context" bind:value={context} placeholder="Context..." />
		</div>
		<div class="flex flex-col items-start" style="width: 40%;">
			<Label for="message">Enter the commit message</Label>
			<Input type="text" bind:value={message} id="message" placeholder="Commit message..." />
		</div>
		<div class="flex flex-col items-start" style="width: 20%;">
			<Label for="postfix">Postfix</Label>
			<Input type="text" id="postfix" bind:value={postfix} placeholder="(Optional) Postfix" />
		</div>
		<Button class="mt-4" on:click={copyToClipboard}>Copy</Button>
	</div>
	<div class="m-auto mt-4 w-[80%]">
		<p class="text-center">Your commit message will be:</p>
		<p class="text-center">{selected}({context}): {message} {postfix}</p>
	</div>
</form>
