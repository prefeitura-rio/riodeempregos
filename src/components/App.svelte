<script>
  import copy from "$data/doc.json";

  import Text from "$components/Text.svelte";
  import Subhead from "$components/Subhead.svelte";
  import Image from "$components/Image.svelte";
  import Hero from "$components/Hero.svelte";
  import Map from "$components/Map.svelte";
  import Scrolly from "$components/helpers/Scrolly.svelte";
  import Triptych from "$components/Triptych.svelte";
  import Slide from "$components/Slide.svelte";
  import Methodology from "$components/Methodology.svelte";
  import LeadImageContainer from "$components/LeadImageContainer.svelte";
  import LeadText from "$components/LeadText.svelte";
  import Stains from "$components/Stains.svelte";
  import ScrollyContainer from "$components/upward-mobility/ScrollyContainer.svelte";
    import Problema from "./Problema.svelte";
    import Deterioracao from "./Deterioracao.svelte";
    import Solucao from "./Solucao.svelte";
    import SolucaoPhoto from "./SolucaoPhoto.svelte";

  const blocks = {
    text: Text,
    image: Image,
    subhead: Subhead,
    map: Map,
    hero: Hero,
    triptych: Triptych,
    problema: Problema,
    solucao: Solucao,
    solucaoPhoto: SolucaoPhoto,
    deterioracao: Deterioracao,
    slide: Slide,
    methodology: Methodology,
    leadtext: LeadText
  };

  let introH;
  let preMapH;
  let outroH;
  let radialH;

  export let introScrollValue;
  export let id;
</script>

<article>
  <!-- Display header -->
  <Hero />
  
  <!-- Intro -->
  <section style="margin-top:-15rem" class="intro-section" bind:clientHeight={introH}>
    <div class="text-wrapper">
      {#each copy.intro as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if introH != undefined}
      <Stains height={introH} />
    {/if}
  </section>
   <!--  ############################ !jumped to here -->
  <section id="text" class="px-4" bind:clientHeight={preMapH}>
    <div class="text-wrapper">
      {#each copy.blocks as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if preMapH != undefined}
      <Stains height={preMapH} />
    {/if}
  </section>
  <!-- scrolly -->
  <section class="relative-custom">
    <LeadImageContainer stepIndex={introScrollValue} />
    <!-- <div class="spacer" /> -->
    <Scrolly bind:value={introScrollValue} bind:id className="flex flex-col">
      <!-- <div class="grid grid-cols-12"> -->
      {#each copy.outcomes as slide, i}
        <LeadText
          stepIndex={introScrollValue}
          className={`h-screen ${introScrollValue === i ? "active" : ""}`}
          {...slide}
        />
     
      {/each}
    </Scrolly>
  </section>
 <!--  ############################ here i jumped to here -->
  <!-- Radial bar chart -->
  <section class="relative-custom">
    <ScrollyContainer />
  </section>
  <!-- conclusion text -->

  <section class="intro-section" bind:clientHeight={introH}>
    <div class="text-wrapper">
      {#each copy.problema as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if introH != undefined}
      <Stains height={introH} />
    {/if}
  </section>
   
  <section id="text" class="px-4" bind:clientHeight={preMapH}>
    <div class="text-wrapper">
      {#each copy.blocks_problema as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if preMapH != undefined}
      <Stains height={preMapH} />
    {/if}

  </section>

  <section style="margin-top:-20px" class="intro-section" bind:clientHeight={introH}>
    <div class="text-wrapper">
      {#each copy.deterioracao as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if introH != undefined}
      <Stains height={introH} />
    {/if}
  </section>
  <!-- <section id="text" class="px-4" bind:clientHeight={preMapH}>
    <div class="text-wrapper">
      {#each copy.blocks_deterioracao as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if preMapH != undefined}
      <Stains height={preMapH} />
    {/if}
  </section>
  <div class="iframe-container">
    <iframe class="border-2 border-black" width="900" height="500" src="https://www.youtube.com/embed/vmqZFQy_lhg?si=4rjb380bBc_HiGv5" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div> -->

  <section style="margin-top:-20px" class="intro-section" bind:clientHeight={introH}>
    <div class="text-wrapper">
      {#each copy.solucao as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if introH != undefined}
      <Stains height={introH} />
    {/if}
  </section>
  <!-- <section id="text" class="px-4" bind:clientHeight={preMapH}>
    <div class="text-wrapper">
      {#each copy.blocks_solucao as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if preMapH != undefined}
      <Stains height={preMapH} />
    {/if}
  </section> -->

  <!-- <section style="margin-top:28rem" class="intro-section" bind:clientHeight={introH}>
    <div class="text-wrapper">
      {#each copy.solucao_continuacao as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if introH != undefined}
      <Stains height={introH} />
    {/if}
  </section> -->
  
  <section id="text-2" class="px-4" bind:clientHeight={outroH}>
    <div class="text-wrapper2">
      {#each copy.blocks2 as props, i}
        <svelte:component
          this={blocks[props.block] ?? Text}
          id={props.id ?? `graf-${i}`}
          {...props}
        />
      {/each}
    </div>
    {#if outroH != undefined}
      <Stains height={outroH} />
    {/if}
  </section>
</article>

<style>
  .iframe-container iframe {
  position: relative;
  z-index: 9999; /* Ajuste o valor conforme necessário */
}
  .iframe-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Full height of the viewport */
  width: 100%; /* Full width of the viewport */
}

iframe {
  /* Optional: To ensure the iframe is responsive and maintains aspect ratio */
  max-width: 100%;
  max-height: 100%;
}

.text-wrapper {
  padding-top:5rem;
  position: relative;
  z-index: 999;
}
.text-wrapper2 {
  padding-top:5rem;
  position: relative;
  z-index: 999;
}
  .relative-custom {
    width: 100%;
    margin: 3rem 0;
  }

  .intro-section {
    margin-top: 4rem;
    padding: 0 1rem;
  }

  @media only screen and (min-width: 550px) {
    .intro-section {
      margin-top: 6rem;
      padding: 0 2rem;
    }
  }

  @media only screen and (min-width: 700px) {
    .intro-section {
      margin-top: 6rem;
      padding: 0;
    }
  }
  @media only screen and  (max-width: 650px) {
    .text-wrapper2 {
      margin: 0 1rem;
}
  }
</style>
