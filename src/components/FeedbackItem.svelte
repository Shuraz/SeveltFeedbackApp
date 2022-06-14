<script>
    import Card from '../components/ui/Card.svelte'
import { FeedbackStore } from '../stores';
    export let item;
    const handleDelete=(itemId)=>{
        // console.log(item.id)
        FeedbackStore.update((currentFeedback)=>{
            return currentFeedback.filter(item=>item.id!=itemId)

        })

    }
</script>

<Card>
<div class="num-display">
    {item.rating}
</div>
<button class="close" on:click={()=>{handleDelete(item.id)}}>X</button>
<div class="text-display">{item.text}</div>
</Card>
<style>
    .num-display{
        position: absolute;
        left: -10px;
        top: -10px;
        width: 50px;
        height: 50px;
        background: #ff6a95;
        color: #fff;
        border: 1px solid #fff;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }
    .close{
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        background: none;
        border: none;
        font-size: 15px;
    }
</style>