<script>
    import {FeedbackStore} from "../stores"
    export let count;
    export let average;
    
    $: count = $FeedbackStore.length;
  $: average =
  $FeedbackStore.reduce((a, { rating }) => a + rating, 0) / $FeedbackStore.length;

</script>

<div class="feedback-stat">
    <h4>{count} Reviews</h4>
    <h4>Rating Average: {average}</h4>
</div>

<style>
    .feedback-stat{
        display: flex;
        justify-content: space-between;
        justify-items: center;
    }
</style>