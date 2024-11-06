<script lang="ts">
	let counter = $state(0);
</script>

<h1>Welcome to SvelteKit</h1>
<p>{counter}</p>
<button onclick={() => counter++}>+</button>
<button onclick={() => counter--}>-</button>
