<script>
	let output;

	function base64(e) {
		const file = e.target.files[0];

		const reader = new FileReader();
		reader.onloadend = () => {
			const base64String = reader.result.replace('data:', '').replace(/^.+,/, '');
			console.log(base64String);
			output = reader.result;
		};
		reader.readAsDataURL(file);
	}
</script>

<h1
	class="text-4xl tracking-tight font-extrabold text-gray-900 sm:text-5xl md:text-6xl lg:text-5xl xl:text-6xl text-center pt-16"
>
	Base 64 Encoding
</h1>
<div class="m-auto max-w-lg">
	<input type="file" on:change={(e) => base64(e)} class="w-full px-32 py-8" />
</div>
{#if output}
	Output
{/if}
