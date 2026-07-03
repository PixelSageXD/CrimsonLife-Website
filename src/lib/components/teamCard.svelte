<script>
    export var teamName = "";
</script>

<div class="teamCard">
    <h1 class="text-3xl md:text-5xl lg:text-5xl pb-5 montserrat text-gray-200 text-center">{teamName}</h1>
    <div class="teamGrid">
        <slot></slot>
    </div>
</div>

<style>
    .teamCard {
        max-width: 1600px;
        width: calc(100% - 2rem);
        margin: 0 auto 2rem;
        padding: 1rem;
        border-radius: 1rem;
        background-color: var(--secondary);
        box-shadow: 0 0 30px rgba(70, 0, 34, 0.3)
    }
</style>
