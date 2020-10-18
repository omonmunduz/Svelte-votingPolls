<script>
    import { onDestroy} from 'svelte';
    import PollStore from '../stores/pollStore.js';
    import PollDetails from './PollDetails.svelte';
     let polls = [];

    const unsub = PollStore.subscribe(data => {
         polls = data
     })

     onDestroy(() => {
         unsub()
     })
</script>

<div class = "list-of-polls">
    {#each polls as poll (poll.id)}
        <PollDetails {poll} />
    {/each}
</div>


<style>
    .list-of-polls {
        display: grid;
         grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
