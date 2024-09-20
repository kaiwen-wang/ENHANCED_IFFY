<script>
    import Header from "$lib/components/Header.svelte";

    const moderationLog = [
        {
            status: "Approved",
            reasoning:
                "The content does not contain any explicit or inappropriate material and appears to be focused on promoting a website. There are no suggestive or sexual elements present.",
            time: "9/17/2024, 9:22:12 PM",
        },
        {
            status: "Approved",
            reasoning:
                "The content does not contain any explicit, sexual, or inappropriate elements according to the guidelines.",
            time: "9/17/2024, 9:22:09 PM",
        },
        {
            status: "Approved",
            reasoning:
                "The content consists of non-explicit, general announcements about a website launch, and the image appears to be a playful portrait without any objectionable features.",
            time: "9/17/2024, 9:22:00 PM",
        },
    ];
</script>

<div class="pt-8">
    <Header />

    <section>
        <h1 class="text-3xl font-bold mb-4">Moderation Log</h1>
        <table class="w-full border-collapse">
            <thead>
                <tr class="bg-gray-100">
                    <td class="p-2 font-semibold">Status</td>
                    <td class="p-2 font-semibold">Reasoning</td>
                    <td class="p-2 font-semibold">Time</td>
                </tr>
            </thead>
            <tbody>
                {#each moderationLog as item, index}
                    <tr class="border-b">
                        <td class="p-2">
                            <span
                                class="inline-flex items-center px-2 py-1 rounded-full text-xs font-medium bg-green-100 text-green-800"
                            >
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    class="h-4 w-4 mr-1"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="2"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                >
                                    <path d="M20 6 9 17l-5-5"></path>
                                </svg>
                                {item.status}
                            </span>
                        </td>
                        <td class="p-2">{item.reasoning}</td>
                        <td class="p-2">{item.time}</td>
                    </tr>
                {/each}
            </tbody>
        </table>
        <div class="mt-4">
            <p>
                <strong>3</strong> moderations remaining.
                <a class="text-black underline" href="/subscribe">
                    Pay for more
                </a>
            </p>
        </div>
    </section>
</div>
