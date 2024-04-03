<svelte:head>
  <title>Bnnuy Clicker</title>
</svelte:head>

<style>
  :global(a, p) {
    display: block;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 1rem;
    margin: 0.5rem 0;
  }
</style>

<p id="loading">Loading...</p>

<script lang="ts">
	import { onMount } from 'svelte';
  
  onMount(async () => {
    new MutationObserver((list, observer) => {
      for (const mutation of list) {
        if (mutation.type === "childList" && [...mutation.addedNodes.values()].find(n => n instanceof HTMLCanvasElement)) {
          observer.disconnect();
          let loading = document.getElementById("loading")!;
          let parent = loading.parentElement!;
          loading.remove();
          let src = document.createElement("a");
          src.textContent = "Source";
          src.href = "https://github.com/Arc-blroth/alpha-crab-moment/tree/main/bnnuy-clicker/";
          parent.appendChild(src);
        }
      }
    }).observe(document.body, { childList: true });

    const wasm = await import("./bnnuy-clicker.js");
    try {
      await wasm.default("bnnuy/bnnuy-clicker_bg.wasm");
      wasm.start();
    } catch (error) {
      if (!(error instanceof Error) || !error.message.startsWith("Using exceptions for control flow, don't mind me. This isn't actually an error!")) {
        throw error;
      }
    }
  });
</script>
