<script>
    import {onMount,onDestroy} from 'svelte'
    import { FeedbackStore } from '../stores'
    import {fade,scale} from 'svelte/transition'
    import FeedbackItem from './FeedbackItem.svelte'
    // let feedback = []
    // // console.log(feedback)
    // const unsubscribe= FeedbackStore.subscribe((data)=>feedback=data)
    // onMount(()=>{
    //     console.log("moMount")
    // })
    // onDestroy(()=>{
    //     unsubscribe();
    // })
</script>

{#each $FeedbackStore as fb(fb.id) }
<!-- {fb.text} <br> -->
<div in:scale out:fade="{{duration:500}}">
    <FeedbackItem item={fb} on:delete-feedback/>

</div>
{/each}