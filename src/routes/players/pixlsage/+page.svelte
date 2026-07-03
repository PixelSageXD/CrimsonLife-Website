<script lang="ts">
    import playerData from '$lib/data/players.json';
    const player = playerData.find(p => p.name === "pixlsage")
</script>

<div class="player-profile">
  <img src="/players/pixlsage.png" alt="Pix" class="profile-img" />

  <div class="profile-info">
    <h2 class="montserrat text-2xl">{player.nickname}</h2>
    <p>Username: {player.name}</p>
    <p>Former Name(s): None</p>
    <p>Pronouns: any/all</p>
    <p>Season(s): {player.seasonCheck.join(", ")}</p>
    <p>Average Placement: N/A</p>
  </div>
</div>

<br>
<h2 class="montserrat text-3xl" style="text-align: center">Other Skins</h2>
<div class="skin-list">
  <figure class="skin">
    <img src="/players/thirdlife/pixlsage.png" alt="third life skin">
    <figcaption style="margin-top: 0.5rem">Third Life</figcaption>
  </figure>
  <figure class="skin">
    <img src="/players/lastlife/pixlsage.png" alt="last life skin">
    <figcaption style="margin-top: 0.5rem">Last Life</figcaption>
  </figure>
  <figure class="skin">
    <img src="/players/doublelife/pixlsage.png" alt="double life skin">
    <figcaption style="margin-top: 0.5rem">Double Life</figcaption>
  </figure>
</div>
<br>

<div class="season-info">
  <h1 class="montserrat text-3xl">Crimson Third Life</h1>
  <p>Placement: N/A<br>
  Team: None</p>
  <ul class="bullet-list">
    <li><strong>[S1]</strong> Event Placeholder</li>
    <li><strong>[S2]</strong> Session 2 Event</li>
  </ul>
</div>

<br>