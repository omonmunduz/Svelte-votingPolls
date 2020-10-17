<script>
    import PollDetails from './PollDetails.svelte';
    export let polls = [];
</script>

<div class = "list-of-polls">
    {#each polls as poll (poll.id)}
        <PollDetails {poll} on:vote/>
    {/each}
</div>


<style>
    .list-of-polls {
        display: grid;
         grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
