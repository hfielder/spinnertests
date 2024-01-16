<script lang="ts">
  import Spinner from "./Spinner.svelte";

  export let encoded;

  let paapiResponseData: any;

  let sliderValue = 0;

  $: threeSixties = paapiResponseData?.results.threesixty;

  fetch(`https://isitetv.com/isitetv_cms/paapi.php?s=false&encoded=${encoded}`)
    .then((res) => res.json())
    .then((data) => {
      paapiResponseData = data;
    });

  $: {
    console.log(paapiResponseData);
  }

  console.log;
</script>

{#if threeSixties}
  <!-- content here -->
  <div class="flex flex-col gap-8 p-8">
    {#each threeSixties as threesixty}
      <Spinner spinnerData={threesixty} />
    {/each}
  </div>
{/if}
