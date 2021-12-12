<script>
	import Editor from '$lib/editor.svelte';

	import Parts from '$lib/panels/parts.svelte';
	import Properties from '$lib/panels/properties.svelte';
</script>

<div class="w-screen flex flex-row">
	<Properties />
	<Editor />
	<Parts />
</div>
