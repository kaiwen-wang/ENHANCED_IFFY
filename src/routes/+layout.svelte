<script>
    import "../app.css";
</script>

<div class="max-w-4xl px-2 pb-2 mx-auto whitespace-normal">
    <slot />
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
</div>
