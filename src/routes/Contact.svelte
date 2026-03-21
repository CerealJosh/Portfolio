<script>
  let email = "";
  let idea = "";

  function sendEmail() {
    const subject = encodeURIComponent("Portfolio Inquiry / New Idea");
    const body = encodeURIComponent(`Sender Email: ${email}\n\nProject/Idea Description:\n${idea}`);
    window.location.href = `mailto:onujoshua@outlook.com?subject=${subject}&body=${body}`;
  }
</script>

<section id="contact" class="flex flex-col w-full bg-[#040a0f]/80 backdrop-blur-lg py-20 lg:py-32 px-8 lg:px-32">
  <div class="flex flex-col lg:flex-row w-full mb-16 lg:mb-24">
    <div class="w-full lg:w-20 lg:mr-28 justify-self-start font-semibold flex flex-col mb-8 lg:mb-0">
      <span class="text-sm uppercase tracking-wide text-gray-400">Tell us about yourself and the project</span>
    </div>
    <div class="lg:mr-36 justify-self-start font-semibold flex flex-col space-y-4">
      <span class="text-4xl md:text-5xl lg:text-6xl font-semibold">Get in Touch</span>
      <div class="flex flex-col mt-4 font-normal text-gray-400">
        <a href="mailto:onujoshua@outlook.com" class="text-lg md:text-xl lg:text-2xl hover:text-blue-400 transition-colors">onujoshua@outlook.com</a>
        <a href="tel:+2348086670477" class="text-lg md:text-xl lg:text-2xl hover:text-blue-400 transition-colors">+234 808 667 0477</a>
        <span class="text-lg md:text-xl lg:text-2xl mt-4">Lugbe, FCT. Nigeria</span>
      </div>
    </div>
  </div>

  <div class="flex flex-col lg:flex-row w-full">
    <div class="hidden lg:flex w-11 mr-36 justify-self-start font-semibold flex-col"></div>

    <div class="w-full lg:mr-36 flex flex-col lg:textContainer mb-12 lg:mb-0">
      <div class="flex flex-row justify-between py-4 lg:p-6 text-center">
        <input bind:value={email} type="email" placeholder="Your email" class="w-full bg-[#040a0f] border-b-slate-700 border-b-2 pb-3 lg:pb-5 text-lg lg:text-xl transition-colors duration-500 focus:outline-none focus:border-b-blue-500 hover:border-b-blue-500" />
      </div>
      <div class="flex flex-row justify-between py-4 lg:p-6 text-center">
        <input bind:value={idea} type="text" placeholder="Describe your idea" class="w-full bg-[#040a0f] border-b-slate-700 border-b-2 pb-3 lg:pb-5 text-lg lg:text-xl transition-colors duration-1000 ease-in focus:outline-none focus:border-b-blue-500 hover:border-b-blue-500" />
      </div>
    </div>
    <div class="lg:mr-36 justify-self-end font-semibold flex flex-col-reverse pb-4 items-end lg:items-center">
      <button on:click={sendEmail} class="text-3xl lg:text-4xl flex items-center space-x-4 hover:text-blue-500 transition-colors"><span>Send </span> <i class="fa-solid fa-arrow-right"></i></button>
    </div>
  </div>
</section>
