<script>
  import { onMount } from 'svelte';

  let currentImage = $state('/glitch1.png');

  onMount(() => {
    const interval = setInterval(() => {
      currentImage = currentImage === '/glitch1.png'
        ? '/glitch2.png'
        : '/glitch1.png';
    }, 750);

    return () => clearInterval(interval);
  });
</script>

<div style="text-align:center">
<img src="CL-heart.png" width="256" alt="Logo Heart">
</div>

<h1 class="montserrat" style="text-align:center">CRIMSON LIFE</h1>
<br>

<p style="text-align:center">
    <a href="/secrets/contact" class="glitch-link">
        <img src={currentImage} alt="Glitch">
    </a>
</p>

<style>
    .glitch-link {
        display: inline-block;
        cursor: pointer;
    }

    .glitch-link img {
        width: 300px;
    }
</style>