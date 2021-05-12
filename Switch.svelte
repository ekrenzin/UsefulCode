<script>
  import { onMount } from 'svelte'
  export let checked = true
  export const color = '#2196F3'
  let sliderText
  let text = ''
  const leftText = () => {}
  const rightText = () => {
    sliderText.style.marginLeft = '25px'
  }
  function toggleText(checked) {
    if (sliderText && sliderText.style) checked ? (text = 'ON') : (text = 'OFF')
  }
  onMount(() => toggleText(checked))
  $: toggleText(checked)
</script>

<style>
  .switch {
    position: relative;
    display: inline-block;
    width: 55px;
    height: 34px;
    font-weight: 600;
  }
  .switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  .slider {
    position: absolute;
    cursor: pointer;
    height: 25px;
    left: 0;
    right: 0;
    bottom: 5px;
    background-color: #ccc;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
    box-shadow: 2px 2px 4px 2px rgba(0, 0, 0, 0.4);
  }
  .slider:before {
    position: absolute;
    content: '';
    top: -2px;
    left: 0px;
    height: 30px;
    width: 30px;
    background-color: #616161;
    box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.4);
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
  }
  .sliderText {
    position: absolute;
    font-size: 10px;
    margin-top: 5px;
    z-index: 5;
  }
  .leftText {
    margin-left: 10px;
  }
  .rightText {
    margin-left: 32px;
  }
  input {
    transition-duration: 0.5s;
  }
  input:checked + .slider {
    background-color: #57fff2;
  }
  input:checked + .slider {
    box-shadow: 0 0 1px #57fff2;
    box-shadow: 2px 2px 4px 2px rgba(0, 0, 0, 0.4);
  }
  input:checked + .slider:before {
    -webkit-transform: translateX(30px);
    -ms-transform: translateX(30px);
    transform: translateX(30px);
  }
</style>

<label class="switch">
  <input type="checkbox" bind:checked />
  <span class="slider">
    <span
      class="sliderText"
      class:leftText={checked}
      class:rightText={!checked}
      bind:this={sliderText}>
      {text}
    </span>
  </span>
</label>
