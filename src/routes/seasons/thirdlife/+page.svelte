<script lang="ts">
    import PlayerCard from '$lib/components/playerCard.svelte';
	import TeamCard from '$lib/components/teamCard.svelte';
    import playerData from '$lib/data/players.json';
    import teamData from '$lib/data/TLteams.json';

    function getPlayer(name: string) {
        return playerData.find(p => p.name === name);
    }
</script>

<div style="margin: 1rem;">
    <div class="logo mb-5" style="text-align:center">
        <img src="/CTL-logo.png" class="size-1/5 m-auto" width="256" alt="third life logo">
    </div>
    <br>
    <div class="info" style="text-align:center">
    <h1 class="montserrat" style="text-align:center">INFO</h1>
    <p class="text-xl" style="text-align:center">
    Start Date: N/A<br>End Date: N/A<br>Winner: N/A<br>
    </p>
    </div>

    <br><h1 class="montserrat" style="text-align:center">PLAYERS</h1><br>
    <div class="playerGrid m-10">
        {#each playerData as player}
            <PlayerCard
                name={player.name}
                nickname={player.nickname}
                lives={player.lives}
                placement={player.placement}
                seasons={player.seasons}
                season={true}
            />
        {/each}
    </div>

    <br><h1 class="montserrat" style="text-align:center">TEAMS</h1><br>
    <div class="teams">
    {#each teamData as team}
        <TeamCard teamName={team.teamName}>
        {#each team.players as playerName}
            {#if getPlayer(playerName)}
            <PlayerCard {...getPlayer(playerName)} season={true}/>
            {:else}
            <p>Player not found: {playerName}</p>
            {/if}
        {/each}
        </TeamCard>
    {/each}
    </div>

    <br><h1 class="montserrat" style="text-align:center">GIMMICK</h1><br>
    <p style="text-align:center">The gimmick for this season has not yet been revealed!</p>

    <br><h1 class="montserrat" style="text-align:center">EVENTS</h1>
    <h2 class="montserrat" style="text-align:center">Session 1</h2>
    <p style="text-align:center">This session has not yet taken place.</p>
</div>
