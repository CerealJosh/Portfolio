<script>
  import Header from "./Header.svelte";
  import Footer from "./Footer.svelte";
  import "./styles.css";
  import "./app.css";
  import "@fortawesome/fontawesome-free/css/all.min.css";
</script>

<div class="flex flex-col min-h-screen overflow-x-hidden bg-[url('$lib/images/back.jpg')] bg-no-repeat bg-cover bg-fixed">
  <Header />

  <main
    class="flex-1 flex flex-col w-full mx-auto box-border"
  >
    <slot />
  </main>
  <Footer />
</div>
