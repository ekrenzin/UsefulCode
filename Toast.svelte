<script>
  import { Toasts } from './../Store.js'
  import { fade, fly } from 'svelte/transition'
  import { backOut } from 'svelte/easing'
  Toasts.subscribe(data => {
    if (data.length > 0)
      setTimeout(() => Toasts.set($Toasts.filter((a, i) => i > 0)), 2000)
  })
</script>

<style>
  .toast-wrapper {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    text-align: center;
    z-index: 9999;
  }
  .toast-item {
    border-radius: 4px;
    padding: 12px 10px;
    margin: 10px auto;
    max-width: 400px;
    background: #383d3f;
    color: #fff;
  }
</style>

<div class="toast-wrapper">
  {#each $Toasts as toast}
    <div
      class="toast-item"
      in:fly={{ delay: 0, duration: 300, x: 0, y: 50, opacity: 0.1, easing: backOut }}
      out:fade={{ duration: 200, opacity: 0 }}>
      {toast}
    </div>
  {/each}
</div>
