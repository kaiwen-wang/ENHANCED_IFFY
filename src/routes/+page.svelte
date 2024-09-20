<script>
	import Header from "$lib/components/Header.svelte";
	import { onMount } from "svelte";

	let activeTab = 1;
	let copyButtonText = "Copy";
	let isCopyDisabled = false;

	function setActiveTab(tab) {
		activeTab = tab;
		isCopyDisabled = tab === codeExamples.length;
		copyButtonText = "Copy";
	}

	function copyAndMoveNext() {
		if (isCopyDisabled) return;

		const currentCode = codeExamples[activeTab - 1];
		navigator.clipboard
			.writeText(currentCode)
			.then(() => {
				copyButtonText = "Copied!";
				setTimeout(() => {
					copyButtonText = "Copy";
				}, 500);

				// Move to next tab if not the last one
				if (activeTab < codeExamples.length) {
					activeTab += 1;
					isCopyDisabled = activeTab === codeExamples.length;
				}
			})
			.catch((err) => {
				console.error("Failed to copy text: ", err);
			});
	}

	const codeExamples = [
		`curl https://www.iffy.com/api/moderate \\
	-X POST \\
	-H "Content-Type: application/json" \\
	-H "Authorization: Bearer iffy_5e4570fccddd14976d33bb4e90aa7be1ca745a11a4b8a7a7ced1d2b945ad6a80" \\
	-d '{
	"content": [
	{
		"type": "text",
		"text": "{\"type\":\"product\",\"url\":\"goodsnooze.gumroad.com/l/vivid\",\"name\":\"Vivid - Double your MacBook Pro Brightness\",\"description\":\"Vivid doubles the brightness of your MacBook Pro across all apps, not just videos! ⚠️ Vivid only works on MacBook Pro with M1/2/3 Pro or Max chips.\"}"
	},
	{
		"type": "image_url",
		"image_url": {
		"url": "https://public-files.gumroad.com/bbaop6t7ewslyb1q4rdwssyf0yw1"
		}
	}
	]
}'`,
		`curl https://www.iffy.com/api/moderate \\
    -X POST \\
    -H "Content-Type: application/json" \\
    -H "Authorization: Bearer iffy_f69546c2e83cce4b66cd33f57bbcb0b3f3a10c23920cfe64762fe390e6bc4af1" \\
    -d '{
  "content": [
    {
      "type": "text",
      "text": "{\"url\":\"pornhub.com\",\"content\":\"This is an adult website. This website contains age-restricted materials including nudity and explicit depictions of sexual activity. By entering, you affirm that you are at least 18 years of age or the age of majority in the jurisdiction you are accessing the website from and you consent to viewing sexually explicit content.\"}"
    },
    {
      "type": "image_url",
      "image_url": {
        "url": "https://api.url2png.com/v6/P4DF2F8BC83648/189f62d5d9da7d7308982fc5650fa4b3/png/?thumbnail_max_width=851&url=pornhub.com&viewport=1280x2000"
      }
    }
  ]
}'`,
		`curl https://www.iffy.com/api/moderate \\
    -X POST \\
    -H "Content-Type: application/json" \\
    -H "Authorization: Bearer iffy_f69546c2e83cce4b66cd33f57bbcb0b3f3a10c23920cfe64762fe390e6bc4af1" \\
    -d '{
  "content": [
    {
      "type": "text",
      "text": "{\"type\":\"user\",\"url\":\"x.com/shl\",\"name\":\"@shl on Twitter\",\"posts\":[\"Follow me for updates on my new website :)\",\"Check out my new website at x.com! 🚀\",\"I'\''m excited to announce the launch of my new website at x.com! 🎉\"]}"
    },
    {
      "type": "image_url",
      "image_url": {
        "url": "https://pbs.twimg.com/profile_images/1764285408135753728/pYT7qoCb_400x400.jpg"
      }
    }
  ]
}'`,
	];
</script>

<div class="pt-3">
	<Header />

	<div class="grid grid-cols-12 gap-8">
		<section class="col-span-12 relative">
			<p class="absolute top-0 right-0  flex items-center gap-1 mt-3.5  ">
				Copy/paste this into your Terminal to give it a shot!

				<svg width="15" height="15" viewBox="0 0 15 15" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M3.85355 2.14645C3.65829 1.95118 3.34171 1.95118 3.14645 2.14645C2.95118 2.34171 2.95118 2.65829 3.14645 2.85355L7.14645 6.85355C7.34171 7.04882 7.65829 7.04882 7.85355 6.85355L11.8536 2.85355C12.0488 2.65829 12.0488 2.34171 11.8536 2.14645C11.6583 1.95118 11.3417 1.95118 11.1464 2.14645L7.5 5.79289L3.85355 2.14645ZM3.85355 8.14645C3.65829 7.95118 3.34171 7.95118 3.14645 8.14645C2.95118 8.34171 2.95118 8.65829 3.14645 8.85355L7.14645 12.8536C7.34171 13.0488 7.65829 13.0488 7.85355 12.8536L11.8536 8.85355C12.0488 8.65829 12.0488 8.34171 11.8536 8.14645C11.6583 7.95118 11.3417 7.95118 11.1464 8.14645L7.5 11.7929L3.85355 8.14645Z" fill="currentColor" fill-rule="evenodd" clip-rule="evenodd"></path></svg>
			</p>

			<div
				class="flex *:px-8 divide-x divide-black border-l border-r border-t w-fit border-black"
			>
				{#each [1, 2, 3] as tab}
					<button
						class="py-2 transition-colors duration-200 ease-in-out"
						class:bg-black={activeTab === tab}
						class:text-white={activeTab === tab}
						on:click={() => setActiveTab(tab)}
					>
						{tab}
					</button>
				{/each}
			</div>

			{#each codeExamples as example, index}
				{#if activeTab === index + 1}
					<div class="relative">
						<button
							on:click={copyAndMoveNext}
							class="absolute top-0 right-0 flex items-center gap-1 border border-black px-1 rounded-sm mr-3 mt-3 z-10 bg-white hover:bg-gray-100 transition-colors duration-200"
							class:opacity-50={isCopyDisabled}
							class:cursor-not-allowed={isCopyDisabled}
							disabled={isCopyDisabled}
						>
							<svg
								width="15"
								height="15"
								viewBox="0 0 15 15"
								fill="none"
								xmlns="http://www.w3.org/2000/svg"
								><path
									d="M1 9.50006C1 10.3285 1.67157 11.0001 2.5 11.0001H4L4 10.0001H2.5C2.22386 10.0001 2 9.7762 2 9.50006L2 2.50006C2 2.22392 2.22386 2.00006 2.5 2.00006L9.5 2.00006C9.77614 2.00006 10 2.22392 10 2.50006V4.00002H5.5C4.67158 4.00002 4 4.67159 4 5.50002V12.5C4 13.3284 4.67158 14 5.5 14H12.5C13.3284 14 14 13.3284 14 12.5V5.50002C14 4.67159 13.3284 4.00002 12.5 4.00002H11V2.50006C11 1.67163 10.3284 1.00006 9.5 1.00006H2.5C1.67157 1.00006 1 1.67163 1 2.50006V9.50006ZM5 5.50002C5 5.22388 5.22386 5.00002 5.5 5.00002H12.5C12.7761 5.00002 13 5.22388 13 5.50002V12.5C13 12.7762 12.7761 13 12.5 13H5.5C5.22386 13 5 12.7762 5 12.5V5.50002Z"
									fill="currentColor"
									fill-rule="evenodd"
									clip-rule="evenodd"
								></path></svg
							>
							{copyButtonText}
						</button>

						<pre
							class="whitespace-pre-wrap break-words overflow-x-auto max-w-full bg-[#F8F9FA] py-4 px-4 border border-black relative">
{example}</pre>
					</div>
				{/if}
			{/each}
		</section>
	</div>
</div>

<a
	target="_blank"
	rel="noreferrer"
	href="https://gumroad.com/"
	class="fixed bottom-0 right-0 bg-[rgb(240,150,227)] flex gap-1.5 py-2 px-2.5 rounded-full border-2 border-black mr-2 mb-2 shadow-md
	
	hover:-translate-y-1
	 transition-all
	ease-in
	group
	 "
>
	<svg
		xmlns="http://www.w3.org/2000/svg"
		class=""
		fill="none"
		height="24"
		width="24"
		viewBox="90.295 93.404 330.706 320.703"
		><path
			d="m278.037 414.107c78.957 0 142.964-61.788 142.964-138.008s-64.007-138.009-142.964-138.009-142.965 61.789-142.965 138.009 64.008 138.008 142.965 138.008z"
			fill="#000"
		/><path
			d="m241.141 385.186c83.044 0 150.846-65.055 150.846-145.891 0-80.835-67.802-145.891-150.846-145.891-83.043 0-150.846 65.056-150.846 145.891 0 80.836 67.803 145.891 150.846 145.891z"
			fill="#ff90e8"
			stroke="#000"
			stroke-width="1.563"
		/><path
			d="m229.795 312.898c-42.217 0-67.05-34.11-67.05-76.54 0-44.095 27.316-79.869 79.465-79.869 53.806 0 72.016 36.607 72.844 57.405h-38.905c-.827-11.647-10.761-29.118-34.766-29.118-25.66 0-42.216 22.463-42.216 49.918s16.556 49.917 42.216 49.917c23.178 0 33.111-18.303 37.25-36.605h-37.25v-14.976h78.162v76.54h-34.29v-48.254c-2.484 17.472-13.245 51.582-55.46 51.582z"
			fill="#000"
		/></svg
	>
	<div class="leading-none flex items-center group-hover:underline">
		By Gumroad
	</div>
</a>
