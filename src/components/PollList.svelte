<script>
    import {fade, slide, scale} from 'svelte/transition';
    import PollStore from '../stores/PollStore.js';
    import PollDetails from './PollDetails.svelte';
    import { onMount, onDestroy}  from 'svelte';
    //export let polls = [];
/*
    const unsub = PollStore.subsribe(data => {
        polls = data;
    });

    onDestroy(()=>{
        //unsubscribe from store
        unsub();
    });

*/

</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div transition:fade>
            <PollDetails {poll} />
        </div>
    {/each}
</div>

<style>
    .poll-list{
        display:grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>