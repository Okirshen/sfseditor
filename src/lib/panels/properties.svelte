<div class="flex flex-col w-60 h-screen p-1 bg-red-500 gap-y-1">
	<div class="property">
		<div>position</div>
		<div class="input">
			<input type="number" name="x" placeholder="x" />
			<input type="number" name="y" placeholder="y" />
		</div>
	</div>
	<div class="property">
		<div>rotation</div>
		<div class="input"><input type="number" name="angle" placeholder="angle" /></div>
	</div>
	<div class="property">
		<div>size</div>
		<div class="input">
			<input type="number" name="x" placeholder="x" />
			<input type="number" name="y" placeholder="y" />
		</div>
	</div>
</div>

<style lang="postcss">
	.property {
		@apply flex flex-row place-content-between;
	}

	input {
		@apply w-10;
	}
</style>
