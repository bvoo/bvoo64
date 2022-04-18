<script lang="ts">
  import { Base64 } from 'js-base64';

  let inputString = '';
  let resultString = '';
  let copyIcon = 'fal fa-copy';

  async function encode(inputString: string) {
    resultString = Base64.encode(inputString);
    copyIcon = 'fal fa-copy';
  }

  async function decode(inputString: string) {
    resultString = Base64.decode(inputString);
    copyIcon = 'fal fa-copy';
  }

  async function copy(resultString: string) {
    navigator.clipboard.writeText(resultString);
    copyIcon = 'fal fa-check';
  }
</script>

<div class="h-[4em]" />
<div class="flex flex-row nowrap justify-center align-middle text-center">
  <div class="flex flex-col justify-between">
    <h1 class="font-serif font-bold tracking-wider pb-16 text-6xl sm:text-4xl md:text-5xl">
      base64
    </h1>
    <div class="h-2" />
    <input type="text" class="h-[200px] font-sans" bind:value={inputString} />
    <div class="pt-4 text-4xl flex flex-row gap-5 sm:gap-0">
      <div class="w-32" />
      <span class="font-mono text-secondary">
        <button on:click={() => encode(inputString)}> encode </button>
      </span>
      <div class="w-16" />
      <span class="font-mono text-secondary ">
        <button on:click={() => decode(inputString)}> decode </button>
      </span>
      <div class="w-32" />
    </div>
    <div class="h-6" />
    <div class="flex flex-row">
        <input bind:value={resultString} type="text" class="cursor-not-allowed w-full font-sans" disabled />
        <span class="font-mono text-secondary text-4xl ">
            <button on:click={() => copy(resultString)} >
                <i id="copy" class={copyIcon} />
            </button>
        </span>
    </div>
  </div>
</div>

<style>
  button {
    background-color: transparent;
  }
</style>
