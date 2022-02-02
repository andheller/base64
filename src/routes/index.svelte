<script>
	let base64String;
	let dataURL;

	function base64(e) {
		const file = e.target.files[0];

		const reader = new FileReader();
		reader.onloadend = () => {
			const result = reader.result;
			dataURL = result;
			base64String = result.replace('data:', '').replace(/^.+,/, '');
		};
		dataURL = reader.readAsDataURL(file);
	}
</script>

<div class="m-auto max-w-5xl">
	<h1
		class="text-4xl tracking-tight font-extrabold text-gray-900 sm:text-5xl md:text-6xl lg:text-5xl xl:text-6xl text-center pt-16"
	>
		Base 64 Encoding
	</h1>
	<div class="m-auto max-w-lg">
		<input type="file" on:change={(e) => base64(e)} class="w-full px-32 py-8" />
	</div>

	{#if base64String}
		<div class="flex max-w-lg m-auto">
			<button
				class="flex font-bold p-2 hover:bg-blue-50 m-4"
				on:click={() => navigator.clipboard.writeText(base64String)}
				><svg
					xmlns="http://www.w3.org/2000/svg"
					class="h-6 w-6 mr-1"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3"
					/>
				</svg> Copy Base 64 String</button
			>

			<button
				class="flex font-bold p-2 hover:bg-blue-50 m-4"
				on:click={() => navigator.clipboard.writeText(dataURL)}
				><svg
					xmlns="http://www.w3.org/2000/svg"
					class="h-6 w-6 mr-1"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 002 2h2a2 2 0 002-2M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10m0 0l3-3m-3 3l3 3"
					/>
				</svg> Copy Data URL</button
			>
		</div>

		<div
			class="break-all max-h-64 p-4 border overflow-scroll max-w-lg m-auto shadow"
			on:click={() => window.clipboardData.setData('Text', base64String)}
		>
			{dataURL}
		</div>
	{/if}
</div>
