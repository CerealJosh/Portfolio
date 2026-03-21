<script>
  import { onMount } from "svelte";
  import { base } from "$app/paths";

  const titles = [
    "Software Engineer",
    "Mobile Developer",
    "Fullstack Developer",
  ];
  let currentTitle = "";
  let titleIndex = 0;
  let charIndex = 0;
  let isDeleting = false;

  onMount(() => {
    /** @type {any} */
    let timeout;
    function type() {
      const fullTitle = titles[titleIndex];

      if (isDeleting) {
        currentTitle = fullTitle.substring(0, charIndex - 1);
        charIndex--;
      } else {
        currentTitle = fullTitle.substring(0, charIndex + 1);
        charIndex++;
      }

      let typeSpeed = isDeleting ? 40 : 100;

      if (!isDeleting && currentTitle === fullTitle) {
        typeSpeed = 2500; // Pause at end of word
        isDeleting = true;
      } else if (isDeleting && currentTitle === "") {
        isDeleting = false;
        titleIndex = (titleIndex + 1) % titles.length;
        typeSpeed = 400; // Pause before typing new word
      }

      timeout = setTimeout(type, typeSpeed);
    }
    type();

    return () => clearTimeout(timeout);
  });
</script>

<section
  id="home"
  class="flex flex-col md:flex-row w-fit py-20 lg:py-32 px-8 lg:px-32 lg:pr-[15vw] bg-[#040a0f]/80 backdrop-blur-lg rounded-br-[4rem]"
>
  <div
    class="w-[50%] md:w-32 lg:w-24 lg:mr-36 justify-self-start font-semibold flex flex-row md:flex-col space-x-6 md:space-x-0 md:space-y-12 lg:space-y-24 mb-12 md:mb-0 items-center md:items-start"
  >
    <span
      class="text-base flex-1 md:flex-none leading-relaxed text-gray-300 wrap-break-word"
      >Software Engineer specializing in fullstack development and secure
      financial systems.</span
    >
    <i
      class="fa-solid fa-arrow-down text-4xl lg:text-7xl -rotate-45 text-blue-500"
    ></i>
  </div>

  <div class="flex flex-col mt-4 md:mt-0">
    <span
      class="text-5xl md:text-8xl lg:text-9xl font-semibold mb-4 lg:mb-8 tracking-tighter"
      style="line-height: 1.1;"
      >Joshua<br />Onu<span class="text-blue-500">.</span></span
    >
    <span
      class="text-3xl md:text-3xl lg:text-4xl text-blue-500 font-semibold mb-8 lg:mb-12 h-[32px] md:h-[40px] lg:h-[48px] flex items-center"
    >
      {currentTitle}<span
        class="animate-pulse border-r-[3px] md:border-r-4 border-blue-500 h-[80%] ml-[2px]"
      ></span>
    </span>
    <a
      href="{base}/Onu Joshua Menayo - Resume.pdf"
      download
      class="mt-6 md:mt-12 px-8 py-3 lg:px-12 lg:py-4 w-fit border-2 border-blue-500 text-blue-500 hover:bg-blue-500 hover:text-white rounded-full transition-colors text-lg lg:text-xl font-semibold flex items-center gap-4 group/btn"
    >
      <span>Download Resume</span>
      <i
        class="fa-solid fa-download group-hover/btn:-translate-y-1 transition-transform duration-300"
      ></i>
    </a>
  </div>
</section>
