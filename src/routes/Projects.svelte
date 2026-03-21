<script>
  import img2 from "$lib/images/project.png";
  import img1 from "$lib/images/wahya.png";
  import img3 from "$lib/images/mySavings.png";

  /** @type {HTMLDivElement} */
  let carousel;
  const scrollAmount = 600;

  function scrollRight() {
    if (carousel) {
      carousel.scrollBy({ left: scrollAmount, behavior: "smooth" });
    }
  }

  function scrollLeft() {
    if (carousel) {
      carousel.scrollBy({ left: -scrollAmount, behavior: "smooth" });
    }
  }

  const projects = [
    {
      id: 2,
      title: "WahyaPay",
      category: "Fintech Platform",
      image: img1,
      description:
        "A comprehensive fintech platform designed to streamline peer-to-peer transactions, providing bank-grade security and sub-second payment finality across integrated banking endpoints.",
      techStack: ["Node.js", "React Native", "PostgreSQL", "Redis"],
    },
    {
      id: 3,
      title: "MySavings",
      category: "Financial Savings",
      image: img3,
      description:
        "A collaborative financial savings application empowering local cooperatives to pool funds safely, track individual contribution metrics, and automate rotational payouts.",
      techStack: ["Spring Boot", "Java", "MySQL", "TailwindCSS"],
    },
    {
      id: 1,
      title: "Fire Outbreak Classification",
      category: "IoT & Machine Learning",
      image: img2,
      description:
        "An advanced machine learning system deployed on IoT edge devices tailored to detect, classify, and instantly alert stakeholders about potential fire hazards in structured environments.",
      techStack: ["Python", "TensorFlow", "C#", "IoT"],
    },
  ];

  /** @type {any} */
  let selectedProject = null;
  let isModalOpen = false;

  /** @param {any} project */
  function openModal(project) {
    selectedProject = project;
    isModalOpen = true;
    if (typeof document !== "undefined") {
      document.body.style.overflow = "hidden";
    }
  }

  function closeModal() {
    isModalOpen = false;
    setTimeout(() => {
      selectedProject = null;
    }, 300);
    if (typeof document !== "undefined") {
      document.body.style.overflow = "";
    }
  }
</script>

<section
  id="projects"
  class="flex flex-col w-full bg-[#040a0f]/80 backdrop-blur-lg py-20 lg:py-32"
>
  <div class="flex flex-col md:flex-row w-full px-8 lg:px-32 mb-8 lg:mb-16">
    <div
      class="w-full md:w-48 lg:w-11 lg:pr-36 justify-self-start font-semibold flex flex-col mb-4 md:mb-0"
    >
      <span class="text-xl lg:text-2xl">2026</span>
    </div>
    <div class="flex flex-col">
      <span class="text-4xl lg:text-5xl font-semibold">Selected Work</span>
    </div>
  </div>

  <div class="flex flex-row w-full relative group">
    <div
      class="flex flex-row absolute left-0 opacity-0 group-hover:opacity-100 transition-opacity moveBtn top-0 z-10 bg-gradient-to-r from-black/80 lg:from-black/50 to-transparent p-4 h-full items-center pointer-events-none"
    >
      <button
        on:click={scrollLeft}
        class="pl-4 lg:pl-8 pointer-events-auto hover:text-blue-500 transition-colors"
        aria-label="Scroll left"
        ><i class="fa-solid fa-arrow-left text-2xl lg:text-4xl"></i></button
      >
    </div>

    <div
      bind:this={carousel}
      class="flex flex-row overflow-x-auto snap-x snap-mandatory scroll-smooth w-full [&::-webkit-scrollbar]:hidden [-ms-overflow-style:none] [scrollbar-width:none] pb-8 pt-4 px-8 lg:px-32 gap-6 lg:gap-12"
    >
      {#each projects as project}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div
          class="flex flex-col snap-center shrink-0 group/item cursor-pointer"
          on:click={() => openModal(project)}
        >
          <div
            class="w-[82vw] md:w-[60vw] lg:w-[40vw] aspect-3/2 imgbox relative overflow-hidden rounded-xl"
          >
            <img
              src={project.image}
              alt={project.title}
              class="img w-full h-full object-contain transition-transform duration-700 group-hover/item:scale-105"
            />
            <div
              class="absolute inset-0 bg-black/20 group-hover/item:bg-black/0 transition-colors duration-500"
            ></div>
            <button
              aria-label="View Project"
              class="absolute bottom-5 right-5 shadow-xl opacity-0 group-hover/item:opacity-100 transition-all duration-300 translate-y-4 group-hover/item:translate-y-0 flex items-center justify-center w-12 h-12 border-2 border-blue-500 rounded-full bg-[#040a0f] text-blue-500 hover:bg-blue-500 hover:text-white"
            >
              <i class="fa-solid fa-arrow-right text-lg"></i>
            </button>
          </div>
          <div class="pt-6">
            <span
              class="text-xs lg:text-sm text-slate-400 font-semibold uppercase tracking-widest"
              >{project.category}</span
            >
            <p
              class="text-2xl lg:text-3xl font-bold mt-2 tracking-tight group-hover/item:text-blue-500 transition-colors"
            >
              {project.title}
            </p>
          </div>
        </div>
      {/each}
    </div>

    <div
      class="flex flex-row absolute right-0 opacity-0 group-hover:opacity-100 transition-opacity moveBtn top-0 z-10 bg-gradient-to-l from-black/80 lg:from-black/50 to-transparent p-4 h-full items-center pointer-events-none"
    >
      <button
        on:click={scrollRight}
        class="pr-4 lg:pr-8 pointer-events-auto hover:text-blue-500 transition-colors"
        aria-label="Scroll right"
        ><i class="fa-solid fa-arrow-right text-2xl lg:text-4xl"></i></button
      >
    </div>
  </div>
</section>

<!-- Project Modal Overlay -->
{#if isModalOpen && selectedProject}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div
    class="fixed inset-0 z-50 flex items-center justify-center p-4 sm:p-6 bg-black/80 backdrop-blur-sm transition-opacity duration-300"
    on:click={closeModal}
  >
    <div
      class="relative w-full max-w-4xl max-h-[90vh] overflow-y-auto bg-[#0b0d0f] border border-blue-900/30 rounded-2xl shadow-2xl flex flex-col"
      on:click|stopPropagation
    >
      <button
        aria-label="Close Modal"
        on:click={closeModal}
        class="absolute top-4 right-4 sm:top-6 sm:right-6 w-10 h-10 bg-black/50 hover:bg-blue-600 outline-none rounded-full flex items-center justify-center text-white transition-colors z-20"
      >
        <i class="fa-solid fa-xmark text-xl"></i>
      </button>

      <div class="w-full aspect-3/2 relative">
        <img
          src={selectedProject.image}
          alt={selectedProject.title}
          class="w-full h-full object-contain rounded-t-2xl"
        />
        <div
          class="absolute inset-0 bg-gradient-to-t from-[#0b0d0f] to-transparent"
        ></div>
      </div>

      <div
        class="px-6 py-8 sm:px-12 sm:py-10 flex flex-col -mt-20 relative z-10"
      >
        <span
          class="text-blue-500 font-bold tracking-widest uppercase text-sm mb-2"
          >{selectedProject.category}</span
        >
        <h3 class="text-4xl sm:text-5xl font-bold text-white mb-6">
          {selectedProject.title}
        </h3>

        <p class="text-gray-300 text-lg sm:text-xl leading-relaxed mb-8">
          {selectedProject.description}
        </p>

        <div class="flex flex-col">
          <span class="text-white font-semibold mb-4 text-xl">Technologies</span
          >
          <div class="flex flex-wrap gap-3">
            {#each selectedProject.techStack as tech}
              <span
                class="px-4 py-2 bg-[#040a0f] border border-slate-700 hover:border-blue-500 hover:text-white transition-colors rounded-full text-slate-300 text-sm font-medium"
              >
                {tech}
              </span>
            {/each}
          </div>
        </div>
      </div>
    </div>
  </div>
{/if}
