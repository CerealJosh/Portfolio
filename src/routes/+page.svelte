<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";
  import Hero from "./Hero.svelte";
  import Projects from "./Projects.svelte";
  import Expertise from "./Expertise.svelte";
  import Experience from "./Experience.svelte";
  import Contact from "./Contact.svelte";

  let isLoading = true;

  onMount(() => {
    // Ensure the beautifully styled loading animation forces the viewer to focus before revealing the layout
    setTimeout(() => {
      isLoading = false;
    }, 1800);
  });
</script>

<svelte:head>
  <title>Joshua Onu - Software Engineer</title>
  <meta name="description" content="Portfolio of Joshua Onu" />
</svelte:head>

{#if isLoading}
  <div out:fade={{ duration: 800 }} class="fixed inset-0 z-[100] bg-[#0b0d0f] flex flex-col items-center justify-center">
    <div class="flex flex-col items-center">
      <span class="text-6xl md:text-8xl font-extrabold text-white tracking-[0.2em] drop-shadow-lg animate-pulse">JO</span>
      <div class="w-32 md:w-48 h-1 bg-slate-800 rounded-full mt-6 md:mt-8 overflow-hidden shadow-sm">
        <div class="h-full bg-blue-500 rounded-full loading-bar"></div>
      </div>
    </div>
  </div>
{/if}

<section class="relative flex flex-col gap-20 lg:gap-32 flex-1 text-white pt-28 md:pt-36 pb-20">
  <Hero />
  <Projects />
  <Expertise />
  <Experience />
  <Contact />
</section>

<style>
  @keyframes load {
    0% { width: 0%; }
    100% { width: 100%; }
  }
  .loading-bar {
    animation: load 1.6s cubic-bezier(0.7, 0, 0.3, 1) forwards;
  }
</style>
