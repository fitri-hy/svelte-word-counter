<script>
	let text = "";
	let wordCount = 0;
	let charCount = 0;
	let spaceCount = 0;
	let totalCount = 0;
	let letterCounts = {};
	
	function countWords() {
		wordCount = text.split(" ").filter(Boolean).length;
		charCount = text.replace(/\s/g, "").length;
		spaceCount = text.split(" ").length - 1;
		totalCount = text.length;
		
		letterCounts = {};
		for (let letter of text.toLowerCase()) {
		if (letter.match(/[0-9a-zA-Z.`~!@#$%^&*()_\-+=;:'",.<>/?|\\{}\[\]]/)) {
			// @ts-ignore
			letterCounts[letter] = (letterCounts[letter] || 0) + 1;
		}
		}
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="flex flex-col items-center p-4 w-full lg:w-3/4 mx-auto my-8">
	<h2 class="w-full font-bold text-center text-3xl mb-4 text-blue-600">
		Example Word Counter Function Application
	</h2>
	<textarea class="w-full h-[50vh] p-4 border border-blue-600 rounded-md resize-none" bind:value={text} on:input={countWords}></textarea>
	<div class="w-full grid grid-cols-4 gap-auto py-5 px-4 mt-4 text-lg font-semibold text-gray-100 bg-blue-600 rounded-md">
		<p class="flex flex-col items-center pe-4">CHAR
			<span class="bg-slate-200 p-2 text-center w-20 rounded-md text-rose-500 font-bold">
				{charCount}
			</span>
		</p>
		<p class="flex flex-col items-center pe-4">WORD
			<span class="bg-slate-200 p-2 text-center w-20 rounded-md text-rose-500 font-bold">
				{wordCount}
			</span>
		</p>
		<p class="flex flex-col items-center pe-4">SPACE
			<span class="bg-slate-200 p-2 text-center w-20 rounded-md text-rose-500 font-bold">
				{spaceCount}
			</span>
		</p>
		<p class="flex flex-col items-center pe-4">TOTAL
			<span class="bg-slate-200 p-2 text-center w-20 rounded-md text-rose-500 font-bold">
				{totalCount}
			</span>
		</p>
	</div>
	<div class="w-full py-2 px-2 mt-4 text-lg font-semibold text-gray-100 bg-blue-600 rounded-md">
		<div class="w-full text-lg text-center font-semibold mb-2 text-gray-100">
			LETTER COUNTS
		</div>
		<span class="">
			{#each Object.entries(letterCounts).sort() as [letter, count]}
			<span class="bg-slate-200 text-gray-800 px-2 m-2 uppercase rounded-md">
				{letter}: 
				<span class="text-rose-500 font-bold">{count}</span>
			</span>
			{/each}
		</span>
	</div>
</section>