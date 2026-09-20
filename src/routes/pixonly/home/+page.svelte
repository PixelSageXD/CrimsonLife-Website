<script>
  import { onMount } from 'svelte';

  let currentImage = $state('/secrets/glitch1.png');

  onMount(() => {
    const interval = setInterval(() => {
      currentImage = currentImage === '/secrets/glitch1.png'
        ? '/secrets/glitch2.png'
        : '/secrets/glitch1.png';
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
    <strong>Crimson Life</strong> is a fanmade Life Series by pixlsage, as a continuation to Pixel's Life Series.<br>
    This website acts as a documentation of each of the seasons and players.<br>
</p>

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
        width: 250px;
    }
</style>