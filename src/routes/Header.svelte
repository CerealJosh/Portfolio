<script>
  import { onMount } from "svelte";
  import { base } from "$app/paths";

  let activeSection = "home";

  onMount(() => {
    const sections = ["home", "projects", "expertise", "experience", "contact"];

    const handleScroll = () => {
      let current = "";
      // Calculate which section is highest up on the viewport but not invisible
      sections.forEach((id) => {
        const el = document.getElementById(id);
        if (el) {
          const rect = el.getBoundingClientRect();
          // Using 200px threshold to snap sections actively
          if (rect.top <= 200) {
            current = id;
          }
        }
      });

      if (current) {
        activeSection = current;
      }
    };

    window.addEventListener("scroll", handleScroll);
    // Initial evaluation
    handleScroll();

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  });
</script>

<header
  class="fixed top-0 left-0 right-0 z-50 bg-[#040a0f]/80 backdrop-blur-lg w-full pt-4 pb-4 border-b border-gray-800/50 shadow-sm transition-colors duration-500"
>
  <nav
    class="max-w-screen-xl mx-auto flex flex-col md:flex-row items-center justify-center gap-6 md:gap-16 px-4"
  >
    <!-- Centered Logo -->
    <a
      href="{base}/"
      class="flex items-center group transition-transform duration-300 hover:-translate-y-1"
    >
      <span
        class="text-3xl font-extrabold whitespace-nowrap text-white tracking-widest group-hover:text-blue-500 transition-colors"
        >JO</span
      >
    </a>

    <!-- Centered Inline Navigation -->
    <ul
      class="font-medium flex flex-wrap justify-center items-center gap-6 md:gap-8 border-t border-gray-800/80 md:border-t-0 pt-4 md:pt-0"
    >
      <li>
        <a
          href="#home"
          class="block transition-colors duration-300 text-lg {activeSection ===
          'home'
            ? 'text-blue-500 font-bold scale-105'
            : 'text-slate-300 hover:text-blue-500'}">Home</a
        >
      </li>
      <li>
        <a
          href="#projects"
          class="block transition-colors duration-300 text-lg {activeSection ===
          'projects'
            ? 'text-blue-500 font-bold scale-105'
            : 'text-slate-300 hover:text-blue-500'}">Projects</a
        >
      </li>
      <li>
        <a
          href="#expertise"
          class="block transition-colors duration-300 text-lg {activeSection ===
          'expertise'
            ? 'text-blue-500 font-bold scale-105'
            : 'text-slate-300 hover:text-blue-500'}">Expertise</a
        >
      </li>
      <li>
        <a
          href="#experience"
          class="block transition-colors duration-300 text-lg {activeSection ===
          'experience'
            ? 'text-blue-500 font-bold scale-105'
            : 'text-slate-300 hover:text-blue-500'}">Experience</a
        >
      </li>
      <li>
        <a
          href="#contact"
          class="block transition-colors duration-300 text-lg {activeSection ===
          'contact'
            ? 'text-blue-500 font-bold scale-105'
            : 'text-slate-300 hover:text-blue-500'}">Contact</a
        >
      </li>
    </ul>
  </nav>
</header>
