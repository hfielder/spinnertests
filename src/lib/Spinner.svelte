<script lang="ts">
  export let spinnerData: any;
  let sliderValue = 0;
  $: frameNum = Math.floor((sliderValue / 100) * spinnerData.assets.length);
</script>

{#if spinnerData}
  <article class="w-full">
    <h2>{spinnerData.title}</h2>
    <h3>{sliderValue} - {frameNum}</h3>
    <img
      src={spinnerData.assets[
        frameNum == spinnerData.assets.length ? frameNum - 1 : frameNum
      ]?.image_url}
      alt=""
      draggable="false"
      class="user-select-none w-full"
    />
    <input
      class="w-full"
      bind:value={sliderValue}
      type="range"
      min="0"
      max="100"
    />
  </article>
{/if}
